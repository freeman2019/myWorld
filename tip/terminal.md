快捷键 | 命令
----|---
ctrl + l | 清屏 。 cLear
ctrl + c | 终止命令。 
ctrl + d | 退出 shell，好像也可以表示EOF。 
ctrl + z | 将当前进程置于后台，fg还原。 
ctrl + r | 从命令历史中找 。 Reverse-i-search
ctrl + a | 光标移到行首 。 A
ctrl + e | 光标移到行尾。 End
ctrl + u | 清除光标到行首的字符 。U
ctrl + w | 清除光标之前一个单词 。Word
ctrl + k | 清除光标到行尾的字符。K
ctrl + t | 交换光标前两个字符。swiTch
ctrl + y | 粘贴前一ctrl+u类命令删除的字符。Y
ctrl + p | 上一条命令。Prev
ctrl + n | 下一条命令。Next
ctrl + v | 输入控制字符 如ctrl+v <ENTER>，会输入^M 
ctrl + f | 光标后移一个字符。Fore
ctrl + b | 光标前移一个字符。Back
ctrl + h | 删除光标前一个字符。H
N+<ESC>+f | 光标后移N个单词，N为1时可省略
N+<ESC>+b | 光标前移N个单词，N为1时可省略 
ctrl + s | 挂起当前shell。Stop
ctrl + q | 重新启用
<ESC>+d | 从光标开始处删除到行尾。Delete
!! | 上一条命令 
!-n | 倒数第N条历史命令 
!-n:p | 打印上一条命令（不执行） 
!?string？ | 最新一条含有“string”的命令 
!-n:gs/str1/str2/ | 将倒数第N条命令的str1替换为str2，并执行（若不加g,则仅替换第一个）

