[TOC]

# 讲解ssh key的原理和使用

## ssh key加密的几种方式

### 对称加密

使用对称加密时，客户端和服务器拥有同一个公钥（整个服务器和客户端用的都是同一个）。客户端在本地将登录信息进行加密之后发送到服务器，服务器再通过这个公钥解密判断登录信息是否正确。
>对称加密的客户端和服务器具有相同的权利和地位，但是每个客户端和服务器握有的权利又太强（因为用的都是同一个公钥，一个客户端相当于拥有了所有的权利，而不是仅仅自己登录的权利）

@import "./pic/sshKey/对称加密.png"


### 非对称加密

如果对称加密的公钥泄露（因为全网只有一个，很容易从某个客户端泄露），则安全就没有保证，所以就有非对称加密。

非对称加密的服务器上存有私钥和公钥，当客户端发出请求，服务器将公钥发送给客户端，客户端用这个公钥加密自己的登录信息，再发回服务器，服务器用对应的私钥解密后查看登录信息。

>这种加密方式将权利都给了服务器，一旦黑客冒充服务器，密码就有泄露的风险。（中间人攻击）

@import "./pic/sshKey/非对称加密.png"


### 口令登录

为了避免中间人攻击就采取口令登录，服务器将自己的公钥加密成公钥指纹发布，客户端通过算法将服务器的公钥生成公钥指纹，用户自己核对是否与官网的公钥指纹相同决定是否连接。（这样就能保证公钥不会被公钥指纹倒推出来？）


### 公钥登录

公钥登录应该是最安全的了。客户端自己生成一对公钥和私钥，将公钥上传到服务器，私钥留在本地（每一对公钥和私钥都是唯一匹配的）。服务器收到登录请求，向客户端发送一个公钥加密的随机字符串a,并对a用MD5算法生成D2，客户端用私钥解密出a后也用MD5算法生成D1,并发回服务器，服务器比对D1、D2是否相等之后返回是否登录成功。
这种验证方式没有用到密码，而是client和server“密约”一种数据处理的手段，最后看处理结果是否相同。


@import "./pic/sshKey/公钥登录.png"



## 生成ssh key

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
-t生成ssh用的加密类型，-b生成ssh的大小，-C用于识别这个密钥的注释 ,不一定要用邮箱，但用邮箱好辨认。

```bash
> Enter a file in which to save the key (/home/you/.ssh/id_rsa): [Press enter] 
```
输入密钥和公钥保存的路径

```bash
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```
启动ssh服务

```bash
$ ssh-add ~/.ssh/id_rsa
```
添加密钥


## 一台电脑设置多个ssh key（公钥登录）
ssh的信息应该都存在～/.ssh文件夹下
1. 生成多个ssh
2. 新建config文件，添加内容如下
    ```
    # Home account
    Host home.github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_home

    # Company account
    Host company.github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_company
    ```
    - Host
    Host是可以随意起名的，但是需要注意的是，如果Host命名为 github而非github.com，那么在测试key时需要ssh -T git@github，而非git -T git@github.com 等一下配置多个github账户的时候就要修改这个值。
    - HostName
    远程仓库实际的域名，或IP
    - IdentityFile
    生成时命名的秘钥文件，我这里git.bbdops.com对应id_rsa；github.com对应id_rsa_github。



## github一些简介

### 设置git的用户名和邮箱

git用户名和邮箱设置有全局的，也有针对某个仓库的。

- 全局设置 
    ```bash
    vim ~/.gitconfig
    ```
    或者
    ```bash
    git config --global user.name "Firstname Lastname"
    git config --global user.email "your_email@example.com"
    ```
- 为某个仓库设置
    ```bash
    cd 仓库路径
    vim .gitconfig
    ```
    或者
    ```bash
    git config user.name "Firstname Lastname"
    git config user.email "your_email@example.com"
    ```


### github的http和ssh两种远程链接方式

- http
    http的一个实例：https://github.com/freeman2019/myWorld.git
    如果碰上push时登录失败，则更改仓库中.git/config文件的url属性加上用户名和密码，比如：
    https://mark:zbt123456@github.com/freeman2019/myWorld.git 其中mark是你github的用户名，zbt123456是密码。
    经过push,git将会把你的用户和密码缓存在～/.git-credentials中，下次push(即使是其他仓库就不需要输入密码或更改.git/config文件。

- ssh
    ssh的一个实例：git@github.com:freeman2019/myWorld.git
    可以看出ssh和http方式的格式还是有区别的



## 用ssh登录github(多用户)
1. 生成ssh key，并将公钥上传到github
2. ssh-add ~/.ssh/id_rsa 将rsa秘钥文件加入到代理
3. 可以用ssh -T git@github.com来测试是否链接成功
4. 重复前3步添加第二个账户
5. 修改仓库中.git/config文件的url属性：git@github.com:freeman2019/myWorld.git 其中github.com就是～/.ssh/config中的Host,我们就是利用不同的Host来区分不同的github账号（此时服务器即HostName相同，不能区分两个用户）





