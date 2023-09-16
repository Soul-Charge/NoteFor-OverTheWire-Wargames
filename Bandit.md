# OverTheWire Bandit

[网页](https://overthewire.org/wargames/bandit/)
注释：具体操作部分的内容，代码块为终端回显内容，<>内为输入内容

## Level 0

### 原文翻译分析

> The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

> 这个关卡的目标是让你使用SSH登录游戏。您需要连接的主机是bandit.labs.overthewire.org，端口2220。用户名为bandit0，密码为bandit0。一旦登录，进入level0 -> level1的页面，找出完成level1的线索。

### 相关知识

`ssh`

### 具体操作

`ssh bandit0@bandit.labs.overthewire.org -p 2220`
```
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames
bandit0@bandit.labs.overthewire.org's password: <bandit0>
```

### 密码

```
bandit0
```

## Level 0 -> Level 1

### 原文翻译分析


> The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

> 下一级的密码保存在主目录下名为 readme 的文件中。使用此密码通过 SSH 登录 bandit1。找到某个关卡的密码后，使用 SSH（2220 端口）登录该关卡并继续游戏。

### 相关知识

`ls`, `cat`

### 具体操作

`ls`
```
readme
```
`cat readme`
```
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```

### 密码

```
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```

## Level 1 -> Level 2

### 原文翻译分析

> The password for the next level is stored in a file called - located in the home directory

> 下一个level的密码存储在一个名为"-"的文件，该文件位于home目录

### 相关知识

`ls`, `cat`
`./`匹配当前目录
处理`-`文件名

### 具体操作

`ls`
```
-
```
`cat ./-`
```
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

### 密码

```
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

## Level 2 -> Level 3

### 原文翻译分析

> The password for the next level is stored in a file called spaces in this filename located in the home directory

> 下一个level的密码存储在名为"spaces in this filename"的文件，该文件位于home目录

### 相关知识

`ls` , `cat`
匹配带有空格的文件名
1. `\`
    用`\`转义空格，使空格作为文件名的一部分而不是隔开命令或文件名，其他特殊符号同理
    > Tab键补全不会有人不知道吧，不会吧不会吧
2. `"`
    用`""`包裹文件名

### 具体操作

`ls`
```
spaces in this filename
```
1. 用`\`
    `cat <Tab>`
    `cat spaces\ in\ this\ filename`
2. 用`""`包裹文件名
    `cat "spaces in this filename"`

```
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

### 密码

```
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```
## Level 3 -> Level 4

### 原文翻译分析

> The password for the next level is stored in a hidden file in the inhere directory.

> 下一个level的密码存储在一个隐藏文件，该文件位于"inhere"目录

### 相关知识

`ls -a`, `cd`
`.`开头的隐藏文件

### 具体操作

`ls`
```
inhere
```
`cd inhere`
`ls -a`
```
.  ..  .hidden
```
`cat .hidden`
```
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```

### 密码

```
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```

## Level 4 -> Level 5

### 原文翻译分析

> The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

> 下一个level的密码存储在一个[只有人类可读的文件](https://learnblockchain.cn/ethers_v5/api/utils/abi/formats/#abi-formats--human-readable-abi)，该文件位于inhere目录。提示：如果你的终端一团乱，试试`reset`命令
> 不是很懂"only human-readable file"的意思，目前来看总之就是里面的内容你至少看起来不是乱码

### 相关知识

`ls`, `cd`, `*通配符`, `file`, `reset`
用`./*`匹配当前目录下所有文件
用`file`查看文件类型

### 具体操作

`ls`
```
inhere
```
`cd inhere`
`ls`
```
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
```
1. 不多才10个文件大不了一个一个看
    用`cat ./-file00`这样的方法一个个看没什么好说的
2. 用一个通配符全显示出来
    `cat ./*`
    ```
    �Ű��Bη���b<Q�Ƞ�+V�iO�1�[5{�jmD�B�0D�tQ*��)�A���V �]Ȕl�x(�z�.T26 F8qqlY���v�FN#��'~�E�Q�"�p�
    ����4�}�]��G�A��u[�/9��Mrj�S�r_E�,���G+�h|�+
    �=>KQ�2��]o-p8q�츑���D�
                       .~�&ϯ"PT�I'�cwk^j�����M����;,��co�9lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
    ```
    > 中间好像有个东西很像密码哎，这里只有一部分，问就是全塞了有问题
3. `file`查看文件内容类型
    `file ./*`
    ```
    ./-file00: data
    ./-file01: data
    ./-file02: data
    ./-file03: data
    ./-file04: data
    ./-file05: data
    ./-file06: data
    ./-file07: ASCII text
    ./-file08: data
    ./-file09: Non-ISO extended-ASCII text, with no line terminators
    ```
    `-file07`如此明显

`cat -file07`
```
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```

### 密码

```
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```

## Level 5 -> Level 6

### 原文翻译分析

> The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
> human-readable
> 1033 bytes in size
> not executable

> 下一个level的密码存储在位于"inhere"目录的某处的文件，并且该文件具有以下特点：
> 人类可读
> 大小 1033 bytes
> 不可执行

### 相关知识

`ls`, `cd`, `find`

### 具体操作

因为直接按找文件大小就找到了所以我懒得管其他两个了

`ls`
```
inhere
```
`cd inhere`
`ls`
```
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
```
`find -size 1033c`
```
./maybehere07/.file2
```
`cat ./maybehere07/.file2`

```
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```

### 密码

```
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```

## Level 6 -> Level 7

### 原文翻译分析

>The password for the next level is stored somewhere on the server and has all of the following properties:
> owned by user bandit7
> owned by group bandit6
> 33 bytes in size

> 下一个level的密码存储在此服务器的某处，并且具有以下所有特点
> 所有者为bandit7
> 用户组为bandit6
> 大小为 33 bytes

### 相关知识

`find -user`, `find -group`, `find -size`

### 具体操作

在根目录按照三个条件搜索
`find / -user bandit7 -group bandit6 -size 33c`
> 因为没权限显示的一堆消息不知道怎么清除只能先这样了╮(╯-╰)╭

```
find: ‘/var/log’: Permission denied
find: ‘/var/crash’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
find: ‘/var/spool/bandit24’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/tmp’: Permission denied
find: ‘/var/lib/polkit-1’: Permission denied
/var/lib/dpkg/info/bandit7.password
find: ‘/var/lib/chrony’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/amazon’: Permission denied
find: ‘/var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘/var/lib/snapd/void’: Permission denied
find: ‘/var/lib/snapd/cookie’: Permission denied
find: ‘/var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/snap/lxd/common/lxd’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/pollinate’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/cache/apparmor/a4dd844e.0’: Permission denied
find: ‘/var/cache/apparmor/8eeb6286.0’: Permission denied
find: ‘/drifter/drifter14_src/axTLS’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/drifter6/data’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/drifter8/chroot’: Permission denied
find: ‘/home/ubuntu’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/bandit31-git’: Permission denied
find: ‘/boot/efi’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/429783/task/429783/fd/6’: No such file or directory
find: ‘/proc/429783/task/429783/fdinfo/6’: No such file or directory
find: ‘/proc/429783/fd/5’: No such file or directory
find: ‘/proc/429783/fdinfo/5’: No such file or directory
find: ‘/etc/polkit-1/localauthority’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/multipath’: Permission denied
find: ‘/etc/sudoers.d’: Permission denied
find: ‘/dev/mqueue’: Permission denied
find: ‘/dev/shm’: Permission denied
find: ‘/tmp’: Permission denied
find: ‘/snap’: Permission denied
find: ‘/lost+found’: Permission denied
find: ‘/run/chrony’: Permission denied
find: ‘/run/user/11022’: Permission denied
find: ‘/run/user/8006’: Permission denied
find: ‘/run/user/11004’: Permission denied
find: ‘/run/user/8005’: Permission denied
find: ‘/run/user/11015’: Permission denied
find: ‘/run/user/11019’: Permission denied
find: ‘/run/user/8004’: Permission denied
find: ‘/run/user/11003’: Permission denied
find: ‘/run/user/11009’: Permission denied
find: ‘/run/user/11007’: Permission denied
find: ‘/run/user/11002’: Permission denied
find: ‘/run/user/8003’: Permission denied
find: ‘/run/user/8002’: Permission denied
find: ‘/run/user/11017’: Permission denied
find: ‘/run/user/11014’: Permission denied
find: ‘/run/user/11024’: Permission denied
find: ‘/run/user/11016’: Permission denied
find: ‘/run/user/11011’: Permission denied
find: ‘/run/user/11020’: Permission denied
find: ‘/run/user/11010’: Permission denied
find: ‘/run/user/0’: Permission denied
find: ‘/run/user/11001’: Permission denied
find: ‘/run/user/11013’: Permission denied
find: ‘/run/user/11005’: Permission denied
find: ‘/run/user/11008’: Permission denied
find: ‘/run/user/11000’: Permission denied
find: ‘/run/user/11012’: Permission denied
find: ‘/run/user/11023’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/run/screen/S-bandit25’: Permission denied
find: ‘/run/screen/S-bandit20’: Permission denied
find: ‘/run/multipath’: Permission denied
find: ‘/run/cryptsetup’: Permission denied
find: ‘/run/lvm’: Permission denied
find: ‘/run/credentials/systemd-sysusers.service’: Permission denied
find: ‘/run/systemd/propagate’: Permission denied
find: ‘/run/systemd/unit-root’: Permission denied
find: ‘/run/systemd/inaccessible/dir’: Permission denied
find: ‘/run/lock/lvm’: Permission denied
find: ‘/root’: Permission denied
find: ‘/sys/kernel/tracing’: Permission denied
find: ‘/sys/kernel/debug’: Permission denied
find: ‘/sys/fs/pstore’: Permission denied
find: ‘/sys/fs/bpf’: Permission denied
```

看到了输出中有这一行即为密码的文件
`/var/lib/dpkg/info/bandit7.password`

`cat /var/lib/dpkg/info/bandit7.password`

```
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```

### 密码

```
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```

## Level 7 -> Level 8

### 原文翻译分析

> The password for the next level is stored in the file data.txt next to the word millionth

> 下一个level的密码存储在文件"data.txt"中，密码在单词`millionth`后面

### 相关知识

`egrep`

### 具体操作

`ls`

```
data.txt
```

`egrep millionth data.txt`

```
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```

### 密码

```
TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```

## Level 8 -> Level 9

### 原文翻译分析

> The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

> 下个level的密码存储在文件"date.txt"里，密码是该文件内唯一一个只出现一次的行

### 相关知识

`sort`, `uniq -u`


### 具体操作

用`uniq -u`显示输入文本内容中只出现了一次的行
但是需要内容已被整理排序（就是相同行都放一起）
所以`uniq -u`前面用`sort`加管道`|`把排序好的内容传入`uniq -u`

`ls`

```
data.txt
```

`sort data.txt | uniq -u`

```
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```

### 密码

```
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```

## Level 9 -> Level 10

### 原文翻译分析

> The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

> 下个level的密码存储在 data.txt 文件中，是为数不多的人类可读字符串之一，前面有几个"="字符。

### 相关知识

`grep -a`

### 具体操作

> 那些重复了10次的占位置的`ls`什么的不写了

`grep -a "=" data.txt`
会看到有很多匹配了=的，这时候添加=
`grep -a "==" data.txt`
三个=的时候就只剩下三个匹配了，最后一个很明显是密码
```
���R-�C�========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```

### 密码

```
G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```

## Level 10 -> Level 11

### 原文翻译分析

> The password for the next level is stored in the file data.txt, which contains base64 encoded data

> 下个level的密码存储在 data.txt 文件中，该文件包含 base64 编码的数据

### 相关知识

`base64`

### 具体操作

用`base64 -d`就能解码base64编码的数据了
`base64 -d data.txt`

```
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```

### 密码

```
6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```

## Level 11 -> Level 12

### 原文翻译分析

> The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

> 下个level的密码存储在"data.txt"文件，里面所有的大小写字母都移动了13位

### 相关知识

[关于Rot13这里从简介到转换全给你了](https://lzltool.cn/Tools/Rot13)

### 具体操作

自己随便搜Rot13找一个网站就能转换

### 密码

```
JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```

## Level 12 -> Level 13

### 原文翻译分析

> The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

> 下一个level的密码存储在"data.txt"中，该文件是一个经过反复压缩的十六进制转储文件。
>  因为你没权限直接在这个用户的目录下创建文件，所以先在/temp目录下创建个文件夹然后把`data.txt`复制过去，之后按需用`mv`重命名
> 例如：`mkdir /tmp/myname123`

### 相关知识

`mkdir`, `cp`, `mv`
> `cd -`可以返回上一个目录，是上一个不是上一级

`xxd`, `hexdump`
[hexdump](https://en.wikipedia.org/wiki/Hex_dump)
[十六进制转储](https://zh.wikipedia.org/wiki/十六进制转储)
> 虽然题目提到了hexdump，但`hexdump`命令，只是具有转换十六进制转储(hexdump)的功能的命令之一，除此之外还有`xxd`
> 没错就是因为hexdump这个词同时是一个命令，所以有点迷糊人

`gzip`, `bzip2`, `tar`

### 具体操作

`mkdir /tmp/test-SoulCharge`
`cp data.txt /tmp/test-SoulCharge`
`cd /tmp/test-SoulCharge`

> `test-SoulCharge`为你要用的文件夹名，取一个特殊一点的名字以防创建不了

`cat data.txt`

```
00000000: 1f8b 0808 2773 4564 0203 6461 7461 322e  ....'sEd..data2.
00000010: 6269 6e00 0145 02ba fd42 5a68 3931 4159  bin..E...BZh91AY
00000020: 2653 597b 4f96 5f00 0018 ffff fd6f e7ed  &SY{O._......o..
00000030: bff7 bef7 9fdb d7ca ffbf edff 8ded dfd7  ................
00000040: bfe7 bbff bfdb fbff ffbf ff9f b001 3b56  ..............;V
00000050: 0400 0068 0064 3400 d341 a000 0680 0699  ...h.d4..A......
00000060: 0000 69a0 0000 1a00 1a0d 0034 0034 d3d4  ..i........4.4..
00000070: d1a3 d464 6834 6403 d469 b422 0d00 3400  ...dh4d..i."..4.
00000080: 1a68 068d 3403 4d06 8d00 0c80 00f5 0003  .h..4.M.........
00000090: 4031 3119 00d0 1a68 1a34 c86d 4640 00d0  @11....h.4.mF@..
000000a0: 0007 a80d 000d 00e9 a340 d034 0341 a000  .........@.4.A..
000000b0: 0699 07a9 881e a0d0 da80 6834 0c43 4068  ..........h4.C@h
000000c0: 6432 0340 0c80 6800 0346 8006 8000 d034  d2.@..h..F.....4
000000d0: 0001 f0e1 810e 1958 b7a4 92c7 640e 421a  .......X....d.B.
000000e0: a147 6142 a67e 3603 a756 3ba9 1b08 e034  .GaB.~6..V;....4
000000f0: 41fd 1247 661d b380 00b7 cd8c b23e b6b2  A..Gf........>..
00000100: 1947 e803 0be5 6077 a542 e9ea 7810 29f0  .G....`w.B..x.).
00000110: 429d e1d7 ad8b 0b78 056b e37c 06df 4917  B......x.k.|..I.
00000120: 9b46 f69d 4473 80b4 edc2 ee10 04e3 3e52  .F..Ds........>R
00000130: dd34 2244 08cb 5e64 9314 9521 505e e767  .4"D..^d...!P^.g
00000140: 9021 d029 85e7 9ce2 d1ce d44f 5ec5 f6d6  .!.).......O^...
00000150: d918 de31 f1f5 d149 4695 0937 d06b f046  ...1...IF..7.k.F
00000160: 789d 1bd0 ca69 11eb 2c9a 3290 3d9e 0511  x....i..,.2.=...
00000170: 6cad 205b edc8 c4b5 4691 379a 5978 58c3  l. [....F.7.YxX.
00000180: 4846 a4a0 3ba5 a89a a794 1f93 c588 8160  HF..;..........`
00000190: 016e 2504 2c74 643b 5046 4154 751c 33b1  .n%.,td;PFATu.3.
000001a0: c3e5 53d8 a959 5fdc 6c12 f2bd 02f3 2d83  ..S..Y_.l.....-.
000001b0: b965 3188 0d3c b097 4156 e950 9d49 64f6  .e1..<..AV.P.Id.
000001c0: da4a 2db5 a4ea 5365 27c0 1e79 8109 5f31  .J-...Se'..y.._1
000001d0: c184 46c9 74a5 f923 5ea1 6861 f058 226c  ..F.t..#^.ha.X"l
000001e0: 3df6 5d10 d11f d966 77c9 e488 448c 5a6f  =.]....fw...D.Zo
000001f0: 2c10 410b 4280 140a 0818 8afa 0cfa 8bf7  ,.A.B...........
00000200: ad34 3308 4077 6552 9849 378e 7d85 1fd8  .43.@weR.I7.}...
00000210: f287 1238 7639 11e2 f1e6 483b 7548 25e2  ...8v9....H;uH%.
00000220: 7de4 24ff 1a69 0b85 4b4c ebd0 1231 a512  }.$..i..KL...1..
00000230: f9fb 109c e7ea d932 98fd eb76 f4f8 fa29  .......2...v...)
00000240: 967c e152 9c69 c607 6207 eaef 2095 9441  .|.R.i..b... ..A
00000250: a64e 9ffc 5dc9 14e1 4241 ed3e 597c 9f2e  .N..]...BA.>Y|..
00000260: f0c8 4502 0000                           ..E...
```

结合题目提示**多次压缩的十六进制转储**文件，然后看看这个内容
发现这个文本内容就是`hexdump`和`xxd`之类的十六进制转储命令的输出结果
于是只需把该文本转换回原内容即可得到压缩文件内容
[用`xxd -r`可以把十六进制转储内容转换回二进制内容，并输出到一个文件](https://www.topbyte.cn/2018/11/hexdump-binary-file-and-reverse/)

`xxd -r data.txt > data`
`file data`                         # 查看该压缩文件的类型

```
data: gzip compressed data, was "data2.bin", last modified: Sun Apr 23 18:04:23 2023, max compression, from Unix, original size modulo 2^32 581
```

`mv data data.gz`            # 不改名加一个对应的后缀不能解压（不懂
`gzip -d data.gz`
`file data`

```
data: bzip2 compressed data, block size = 900k
```

`mv data data.bz2`
`bzip2 -d data.bz2`
`file data`

```
data: gzip compressed data, was "data4.bin", last modified: Sun Apr 23 18:04:23 2023, max compression, from Unix, original size modulo 2^32 20480
```

`mv data data.gz`
`gzip -d data.gz`
`file data`

```
data: POSIX tar archive (GNU)
```

`tar -xf data`
`ls`

```
data  data5.bin  data.txt
```

`file data5.bin`

```
data5.bin: POSIX tar archive (GNU)
```

`tar -xf data5.bin`
`ls`

```
data  data5.bin  data6.bin  data.txt
```

`file data6.bin`

```
data6.bin: bzip2 compressed data, block size = 900k
```

`mv data6.bin data6.bin.bz2`
`bzip2 -d data6.bin.bz2`
`ls`

```
data  data5.bin  data6.bin  data.txt    # bzip2解压以后原文件被替换了所以看起来没变化，但其实解压后的就是data6.bin
```

`file data6.bin`

```
data6.bin: POSIX tar archive (GNU)
```

`tar -xf data6.bin`
`ls`

```
data  data5.bin  data6.bin  data8.bin  data.txt
```

`file data8.bin`

```
data8.bin: gzip compressed data, was "data9.bin", last modified: Sun Apr 23 18:04:23 2023, max compression, from Unix, original size modulo 2^32 49
```

`mv data8.bin data8.bin.gz`
`gzip -d data8.bin.gz`
`ls`

```
data  data5.bin  data6.bin  data8.bin  data.txt    # 同上一条
```

`file data8.bin`

```
data8.bin: ASCII text
```

`cat data8.bin`

```
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```

> 你怎么就是不出来（密码）
> 八重套娃，小子！

### 密码

```
wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```

## Level 13 -> Level 14

### 原文翻译分析

### 相关知识

### 具体操作

### 密码
