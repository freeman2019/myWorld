[TOC]

# 组装台式机（硬件）
台式机的挑选主要有以下几个部分的选购：机箱、主板、内存、显卡、电源、CPU、硬盘

## 内存
>内存尽量用双通道，即将两个内存条插在主板颜色相同的插槽中，比如买两个4g组成双通道比直接买一个8g的好

- 频率
    买了高频的内存条要在BIOS里面设置内存的频率
- 厂家
    只有3家能自己生产：三星，海力士，镁光

宇瞻


## 显卡
[显卡天梯图](https://www.mydrivers.com/zhuanti/tianti/gpu/index.html)
[NVIDIA各系列显卡](https://zh.m.wikipedia.org/wiki/NVIDIA%E9%A1%AF%E7%A4%BA%E6%A0%B8%E5%BF%83%E5%88%97%E8%A1%A8)

### NVIDIA
- 系列（版本从旧到新）：GeForce千系列，GeForce百系列，GeForce十系列（在各个系列里面，一般数字越大性能越好）
- 版本（性能从好到坏）：GTS(超了频的高端卡)，GTX(高端卡)，GT(中上配)，GE（超了频的GS），GS(标准版)，LE(缩水版)
- 接口
    1. 管脚的数量
    >一般来说x16的显卡可以插进x8的内存卡槽中，但是性能得不到充分的发挥。

    用几张图来说明
        各式不同的PCI Express插槽（由上而下：x4, x16, x1，与x16），相较于传统的32-bit PCI插槽（最下方），取自于DFI的LanParty nF4 Ultra-D机板
        @import "./pic/computerChoose/PCI-E各种接口.jpg"
        @import "./pic/computerChoose/X8接口.jpg"
        @import "./pic/computerChoose/X16接口.jpg"
    2. 接口的代
    1.0 2.0 3.0 显卡和插槽全部兼容

### AMD



## CPU
[CPU性能天梯图](https://www.mydrivers.com/zhuanti/tianti/cpu/index.html)

### CPU总体的性能分析
>核显会消耗CPU的性能吗？不会，是独立出来的
- 架构
    好的架构使得计算更快更高效，所以买新不买旧
- 核心
    多核心可以同事处理多个任务，可以给每个核心分配多线程
- 频率
    - 基本频率：平时工作的频率
    - 睿频：火力全开频率
    - 超频：极限频率
- 缓存

### intel
酷睿系列的性价比不高，不推荐

### AMD
看软件是否做了多线程的优化，锐龙系列的优势之一就是核心和线程多

| 处理器型号 | 核心架构 | 制造工艺(nm) | 核心/线程 | 核心频率（GHz） | 加速频率（GHz） | 二/三级缓存（MB） | 核显                      | 热设计功耗（W） | 插槽 | 价格 |
|----------|----------|--------------|-----------|---------------|---------------|-----------------|---------------------------|---------------|------|------|
| 锐龙2600   | zen+     | 12           | 6/12      | 3.4           | 3.9           | 3/16            | 无                        | 65            | AM4  | 1100 |
| 锐龙2400G  | zen      | 14           | 4/8       | 3.6           | 3.9           | 2/8             | Vega11(GT 1030)           | 65            | AM4  | 1100 |
| 锐龙2200G  | zen      | 14           | 4/4       | 3.5           | 3.7           | 2/8             | Vega8(和英特尔核显差不多) | 65            | AM4  | 700  |

## 硬盘

### 固态硬盘
>固态硬盘的容量越大寿命越长
#### 总线
| 总线     | 速度        |
|----------|-----------|
| SATA总线 | 最快550M/s  |
| PCIE     | 最快3000M/s |

#### 参数
- 接口参数
从上到下速度逐渐变快

    | 接口 | 走总线 | PCIE总线代              | 是否支持NVME协议 |
    | ---- | ------ | ----------------------- | ---------------- |
    | SATA | SATA   |                         |
    | M.2  | SATA   |                         |
    | ^    | PCIE   | PCIE3.0*2（三根金手指） |
    | ^    | ^      | PCIE3.0*4（两根金手指） | 不支持           |
    | ^    | ^      | ^                       | 支持             |

- 顺序读写速度和4k读写速度（这个是关键，平时用的就是这个速度）
- 闪存颗粒：SLC,MLC,TLC（寿命和速度都是从快到慢）其中大部分用的都是TLC
- 缓存：ddr(空间小，提升有限),SLC(用明显提升)
- 主控：慧荣，群联，marvell,三星，瑞昱

#### 厂家
- 自己生产颗粒
    英特尔，三星，镁光（英睿达），海力士，东芝，闪迪
- 主控厂家
    牛逼3家：marvell（马牌）,三星，英特尔  实惠：东芝，慧荣，群联，瑞昱

#### 推荐

| 厂家   | 型号                      |
|------|---------------------------|
| 三星   | 860EVO(sata),970EVO(NVME) |
| 东芝   | TR200                     |
| 英特尔 | 760P                      |
| 铭瑄   | 复仇者                    |


### 机械硬盘
- 容量
- 碟片数
- 转速
- 缓存（这里有坑，一定先要看碟片数，不要买瓦碟式硬盘，64M一定不是瓦碟式硬盘）
- 西部蓝盘，希捷酷鱼


## 主板
可以考虑和CPU一起买套装
- 主板的大小
    E-ATX ATX M-ATX MINI-ITX（顺序由大到小）
- 主板的芯片组
    intel/LGA1151 intel是指用于intel的cpu LGA1151是cpu的接口类型
    AMDB350/socketAM4 用于AMD
- 内存条的插槽（是否支持ddr4、插槽的数量、通道数，有时4个插槽有2个通道A通道和B通道）
- PCI-E拓展口:既可以差独立显卡，也可以插固态硬盘，考虑是否接口支持
- 固态硬盘是否支持M.2以及NVME协议

### 用于intel平台的主板

| 芯片组          | 接口    | 推荐的cpu型号                           |
|---------------|---------|-----------------------------------------|
| H310(入门)      | LGA1151 | i3-8100                                 |
| B360(主流)      | LGA1151 | i3-8100 i3-8400 i3-8500 i3-8600 i3-8700 |
| H310(中高)      | LGA1151 | i7-8700                                 |
| Z370 Z390(高端) | LGA2066 | i7-7820x等后缀有x的                     |

### AMD
版U套装,最后确认是否支持双通道,内存频率是否支持

套装    芯片组  主板大小    内存插槽   供电相数     M.2插口（固态硬盘）     SATA    PCI-E   price
技嘉B450M DS3H  B450    M-ATX   4     7     2   4   1249
技嘉B450 AORUS M    B450    M-ATX   4   11  1   6   1399
微星B450M PRO M2 V2     B450    ^   2   7   1   4   1.16
微星B450M MORTAR 钛金   B450    ^   4   6   2   4   2.16




## 电源

## 机箱




# 新电脑软件的安装

Bios 升级
换桌面
换bash
shaw
设置Ubuntu常亮

安装vim
安装git

## 操作的顺序

- 将.bashrc和.ssh文件复制到新电脑
- 更改terminal的样式（手动preferences）
- 连接网络
- [16屏幕常亮](http://www.linuxdiyf.com/linux/19321.html) 18 privacy
- 安装vim
- [安装shadowsocks](https://secure.shadowsocks.nu/knowledgebase/40/Shadowsocks----Linux.html)
- 安装chrome
- 安装vscode(ideb)
- [安装搜狗拼音输入法](https://blog.csdn.net/superstar_zbt/article/details/81698831)
- 安装pip3 sudo apt-get install python3-pip
- [配置命令行代理](http://www.totorocyx.me/2018/10/02/ubuntu_shadowsocks/)
- [chrome配置代理](https://portal.shadowsocks.ch/index.php?rp=/knowledgebase/50)

碰到的问题  解决办法
不能识别U盘 modprobe usb-storage，再重新插入


## 用户的配置文件
文件    作用
.bashrc 用户的快捷键

## 系统必备软件

- 搜狗拼音输入法
- chrome

## 编程软件
vscode


















