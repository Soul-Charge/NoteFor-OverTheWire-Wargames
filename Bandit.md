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

> The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

> 下个level的密码存储在 /etc/bandit_pass/bandit14 ，该文件只能被用户bandit14读取。所以这关你不需要获得密码，你需要获取一个SSH key私钥来登录到bandit14。提示：`localhost`是一个代表了当前你用的主机的主机名。

### 相关知识

[SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)  
> 没错我照搬这一页的提示，用翻译看一下就差不多知道了  

[关于多私钥管理，可参考这个](https://www.jianshu.com/p/fe215c52c534)  
> 因为如果你用github基本上你的`id_rsa`已经被占用了，估计没人想为了这关删了自己github的key，所以干脆配置多私钥，这里我用的上述方法二  

### 具体操作

**登录上bandit13**  
`cat sshkey.private`  

```
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
-----END RSA PRIVATE KEY-----
```

复制该文件所有内容  
> 就是上面的，BEGIN和END那些也复制  

**接下来回到自己电脑**  
`cd ~/.ssh`  
自己创建一个文件用来放复制的内容，这里用的是vim  
`touch id_rsa_bandit14`  
`chmod 600 id_rsa_bandit14` # 这里要把私钥文件的权限设置一下，不然登录的时候因为权限太开放用不了  
`vim id_rsa_bandit14`  
按`i`然后右键即可粘贴，然后按`Esc`再输入`:wq`即可保存退出  

然后创建并编辑`config`文件  
`touch  config`  
`chmod  600  config`  
`vim config`  

```
# 这一段是确保你github的私钥能正常使用
Host         github.com
HostName     github.com
User         Soul-Charge   # 当然用户名写自己的
IdentityFile ~/.ssh/id_rsa

# 这一段就是登录bandit14的私钥
Host         bandit.labs.overthewire.org
HostName     bandit.labs.overthewire.org
User         bandit14
IdentityFile ~/.ssh/id_rsa_bandit14
```

`cat /etc/bandit_pass/bandit14`  
> 登录上bandit14以后就能看密码了（有什么必要吗？  

### 密码

```
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```

## Level 14 -> Level 15

### 原文翻译分析

> The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

> 要获取下个level的密码，你需要把当前level的密码发送到当前level的`localhost`主机的`30000`端口上，然后会返回下一level的密码

### 相关知识

`telnet`

### 具体操作

`telnet localhost 30000`  

```Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
```

接下来直接粘贴密码，以下是完整通信过程  

```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

Connection closed by foreign host.
```

### 密码

```
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```

## Level 15 -> Level 16

### 原文翻译分析

> The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.  
> Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…  

> 下一个level的密码需要向`localhost`的`30001`端口发送bandit15的密码，但是要用SSL加密，所以不能用`telnet`（那就用s_client）  
> 有用的提示：如果你觉得一堆"Read R BLOCK"很烦，可以用`ign_eof`，并且读一下帮助页面里"CONNECTED COMMANDS"的内容  

### 相关知识

`openssl s_client`

查看帮助然后`/CONNECTED`查找题目提示的内容  
`man opeenssl s_client`  

```
CONNECTED COMMANDS
       If a connection is established with an SSL server then any data received from the server is displayed and any
       key presses will be sent to the server. If end of file is reached then the connection will be closed down.
       When used interactively (which means neither -quiet nor -ign_eof have been given), then certain commands are
       also recognized which perform special operations. These commands are a letter which must appear at the start
       of a line. They are listed below.

       Q   End the current SSL connection and exit.

       R   Renegotiate the SSL session (TLSv1.2 and below only).

       k   Send a key update message to the server (TLSv1.3 only)

       K   Send a key update message to the server and request one back (TLSv1.3 only)
```

### 具体操作

`openssl s_client -quiet -ign_eof -connect localhost:30001`  
> `-quiet`和`-ign_eof`用来清除多余的内容，剩下的我不知道怎么清掉  

```
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Sep 17 08:03:36 2023 GMT
verify return:1
depth=0 CN = localhost
notAfter=Sep 17 08:03:36 2023 GMT
verify return:1
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt # 自己粘贴的密码
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```




### 密码

```
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```

## Level 16 -> Level 17

### 原文翻译分析

> The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000.  
> First find out which of these ports have a server listening on them.  
> Then find out which of those speak SSL and which don’t.  
> There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.  

> 下个level的凭证(其实就是ssh key)可通过从当前level向主机的31000到32000范围的端口发送密码获得。  
> 首先找到这些端口中哪些有服务在监听。  
> 然后找出其中使用了SSL的。  
> 只有一个服务会给你下个level的凭证，其他的只是复读机  
> `server`翻译存疑  


### 相关知识

`nmap`, `openssh s_client`, ssh多密钥管理  
或许不需要： `grep`, `xargs`  

### 具体操作

> `-pn-n`就是指定扫描端口范围，如果不指定要扫描的端口，Nmap默认扫描从1到1024再加上nmap-services列出的端口  
> [关于nmap的参考](https://www.cnblogs.com/nmap/p/6232207.html)  
检查SSL是问GPT问出来的，就是`pn-n`前面两个参数可以检查SSL  
`nmap --script ssl-cert -p31000-32000 localhost`  

```
Starting Nmap 7.80 ( https://nmap.org ) at 2023-09-28 12:06 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00010s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
| ssl-cert: Subject: commonName=localhost
| Subject Alternative Name: DNS:localhost
| Issuer: commonName=localhost
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2023-09-28T06:01:07
| Not valid after:  2023-09-28T06:02:07
| MD5:   3955 5f2c e723 4b38 8c8e 48d4 ef99 df37
|_SHA-1: 0558 1969 324e a6c2 c886 137f 9ff3 1a81 64b5 3f9a
31691/tcp open  unknown
31790/tcp open  unknown
| ssl-cert: Subject: commonName=localhost
| Subject Alternative Name: DNS:localhost
| Issuer: commonName=localhost
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2023-09-28T06:01:06
| Not valid after:  2023-09-28T06:02:06
| MD5:   337a 4e98 8f60 cb08 f702 f90f b4c5 7037
|_SHA-1: 589b bee2 091f 3742 5900 071c 5622 8d01 1683 0549
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 3.31 seconds
```

可以看到31518和31790都有SSL，接下来都试一遍  
`openssl s_client -quiet -connect localhost:31518`  

```
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Sep 28 06:02:07 2023 GMT
verify return:1
depth=0 CN = localhost
notAfter=Sep 28 06:02:07 2023 GMT
verify return:1
JQttfApK4SeyHwDlI9SXGR50qclOAil1
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```

很明显31518是复读机，试试31790(这时候按下`Ctrl + C`关掉和31518的连接  
`openssl s_client -quiet -connect localhost:31790`  

```
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Sep 28 06:02:06 2023 GMT
verify return:1
depth=0 CN = localhost
notAfter=Sep 28 06:02:06 2023 GMT
verify return:1
JQttfApK4SeyHwDlI9SXGR50qclOAil1
Correct!
```

```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

所以就得到bandit17的ssh key了  
接下来把这个保存为`id_rsa_bandit17`，并且添加到配置文件  
`vim ~/.ssh/config`  
添加以下内容：  

```
Host         bandit.labs.overthewire.org
HostName     bandit.labs.overthewire.org
User         bandit17
IdentityFile ~/.ssh/id_rsa_bandit17
```

> 其他细节看Level13 -> Level14

---
下面的是一个智熄操作，因为不知道怎么检测SSL，所以就打算把扫出来的端口全部连接一遍，用了一下grep过滤到只有端口  
`nmap -p31000-32000 localhost | grep "^[0-9]*" -o`  

```
31046
31518
31691
31790
31960
```

然后是怎么把这些传到`s_client`，问了下GPT，可以用`xargs`  
所以这就是我把这个智熄操作写下来的原因：`somecommand |xargs -item  command`详见菜鸟教程之类的  
下面是GPT的：  


如果您希望将 `grep` 的结果传递给 `openssl s_client -connect` 命令，可以使用 `xargs` 来执行此操作。下面是一个示例命令：  

```bash
nmap -p31000-32000 localhost | grep "^[0-9]*" -o | xargs -I {} openssl s_client -connect localhost:{}
```

在这个命令中，`xargs` 将 `grep` 的结果逐行传递给 `openssl s_client -connect` 命令，并使用 `{}` 占位符来插入每行的内容，以形成要连接的地址和端口。这将允许您使用 `openssl s_client` 连接到匹配的端口。  

请注意，这假设 `grep` 命令在 `nmap` 扫描结果中找到了匹配的端口号。如果没有匹配项，`xargs` 将不会运行 `openssl s_client -connect` 命令。确保 `grep` 的正则表达式与您要匹配的端口号格式一致。  

### 密码

```
VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e
```

## Level 17 -> Level 18

### 原文翻译分析

> There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new  
> NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19  

> home目录下有两个文件：passwords.old 和 passwords.new。下个level的密码是这两个文件之间唯一被改动的行  
> 注意：如果你搞定这关了，但是连接到bandit19的时候却看到一个拜拜了您嘞(Byebye!)，这跟bandit19有关，去下一个看看。  

### 相关知识

`diff`  

### 具体操作

`diff passwords.old passwords.new`  

```
42c42
< glZreTEH1V3cGKL6g4conYqZqaEj0mte
---
> hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
```

下面那个就是该过以后的，就是密码  

### 密码

```
hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
```

## Level 18 -> Level 19

### 原文翻译分析

> The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.   

> 下level的密码就在home目录的readme文件里，但是有个货把你的.bashrc改了，搞得你一登录就登出  

### 相关知识

问ChatGPT3.5:linux系统上，如何在通过ssh登录的同时运行命令  
GPT3.5:  
在Linux系统上，您可以使用SSH来远程登录到另一台计算机，并在登录时执行命令。有两种主要的方法可以实现这一目标：  

使用SSH的命令行选项：  
您可以在SSH命令中使用以下方式来在登录时执行命令：  

```bash
ssh user@hostname 'command'
```

其中：  
- `user` 是远程主机上的用户名。
- `hostname` 是远程主机的主机名或IP地址。
- `command` 是要在远程主机上执行的命令。

例如，如果要远程登录到主机 `example.com` 并执行 `ls` 命令，您可以这样做：

```bash
ssh user@example.com 'ls'
```

这将登录到远程主机，并在登录后立即执行 `ls` 命令，然后显示结果并退出。

### 具体操作

ssh登录的同时运行命令了解一下(￣▽￣)"  
`ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"`  
这样做只会在连接后自动执行命令获得结果后退出  

### 密码

```
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

## Level 19 -> Level 20

### 原文翻译分析

> To gain access to the next level, you should use the setuid binary in the homedirectory.   
> Execute it without arguments to find out how to use it.  
> The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.  

> 为了获得通往下个level的权限，你应该使用home目录的，setuid二进制可执行文件(和setuid有关，可以给你提权)  
> 不带参数直接运行这个文件，你会知道怎么用它的  
> 使用这个文件后你能在老位置(/etc/bandit_pass)，找到密码  

### 相关知识

`setuid`  
其实你根本不需要知道这是什么，但凡仔细看看英文都知道这玩意用就行了（  

### 具体操作

`./bandit20-do`  

```
Run a command as another user.
  Example: ./bandit20-do id
```

所以这玩意就是你输个命令作为参数给它，然后就能作为另一个用户来运行命令（看密码）  
`./bandit20-do cat /etc/bandit_pass/bandit20`  

```
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
```

### 密码

```
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
```

## Level 20 -> Level 21

### 原文翻译分析

> There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument.  
> It then reads a line of text from the connection and compares it to the password in the previous level (bandit20).  
> If the password is correct, it will transmit the password for the next level (bandit21).  
> NOTE: Try connecting to your own network daemon to see if it works as you think  

> home目录有一个setuid的可执行文件，它会在您作为命令行参数指定的端口上与 localhost 建立连接  
> 然后，它会从连接中读取一行文本，并将其与上一级密码（bandit20）进行比较。
> 如果密码正确，它将发送下一级密码（bandit21）。
> 提示：尝试连接到您自己的网络守护进程，看看它是否如您所想的那样工作（等下再来改翻译

### 相关知识

`nc -l`  
多终端窗口：`screen`, `tmux`  
前后台切换：`job control`  
> 最重要的可能还是™看仔细一点程序的用法描述(ノ｀Д)ノ  

### 具体操作

```
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
该程序将使用 TCP 连接到 localhost 上的指定端口。如果从对方接收到正确的密码，就会回传下一个密码。
```

也就是说，这个程序要首先连接到一个端口，等待对方发来bandit20的密码，然后才显示bandit21的密码  
可以用`nc -l 端口号`来开启对一个端口的监听，并发送消息  
下面这里直接把全过程全粘贴了，^Z是按下了`Ctrl + Z`的结果(就是挂起  ，`fg`是把挂起进程切回前台运行  

```
bandit20@bandit:~$ nc -l 2333
^Z
[1]+  Stopped                 nc -l 2333
bandit20@bandit:~$ ./suconnect 2333
^Z
[2]+  Stopped                 ./suconnect 2333
bandit20@bandit:~$ fg %1
nc -l 2333
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
^Z
[1]+  Stopped                 nc -l 2333
bandit20@bandit:~$ fg %2
./suconnect 2333
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
bandit20@bandit:~$
```

下面的是走偏了的思路，我舍不得删掉qwq，主要是舍不得那个匹配只留下端口号和把一堆端口号作为参数发过去的实现思路  

---

题目个人理解：跟你说什么用一个程序对一个端口发密码就完了，结果tm不告诉你哪个端口，  
nmap全部扫一下虽然不算特别多，但是总不能一个个试吧，最sb的是它其他端口会卡住你，  
所以，直接全部试一遍，但是用一个超时自动断开  `timeout 5`(5秒无反应就自动断开)  
然后等结束，看看反应  

`nmap -p0-65535 localhost | grep "^[0-9]*" -o | xargs -I {}; timeout 5 ./suconnect {}`  
`nmap -p0-65535 localhost | grep "^[0-9]*" -o | xargs -I {} bash -c 'echo {}; timeout 5 ./suconnect {}`  
> 下面一行是一个优化的，可以看到是哪一个端口的反应，问就是GPT教的  


```
22
Read: SSH-2.0-OpenSSH_8.9p1
ERROR: This doesn't match the current password!
1111
1234
1840
2220
Read: SSH-2.0-OpenSSH_8.9p1
ERROR: This doesn't match the current password!
2230
Read: SSH-2.0-OpenSSH_8.9p1
ERROR: This doesn't match the current password!
2231
Read: SSH-2.0-OpenSSH_8.9p1
ERROR: This doesn't match the current password!
2232
Read: SSH-2.0-OpenSSH_8.9p1
ERROR: This doesn't match the current password!
4091
Read: Password:
ERROR: This doesn't match the current password!
4321
Read: 100 phrack search daemon, type help for more information
ERROR: This doesn't match the current password!
8000
30000
30001
30002
Read: I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secr
ERROR: This doesn't match the current password!
31046
31518
31691
31790
31960
60917
```

可以看出来30002就是那个交密码的端口，因为后面那一堆话  

---

### 密码

```
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
```

## Level 21 -> Level 22

### 原文翻译分析


> A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  

> 基于时间的工作调度程序 cron 正在定期自动运行一个程序。查看 /etc/cron.d/ 中的配置，看看执行的是什么命令。  

### 相关知识

`Linux cron`  
[参考资料](https://www.runoob.com/w3cnote/linux-crontab-tasks.html)  

### 具体操作

先照着提示看看有什么就行了  
`cd /etc/cron.d`  
`ls`  

```
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24       e2scrub_all  sysstat
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root  otw-tmp-dir
```

看一下属于bandit22的  
`cat cronjob_bandit22`  

```
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

这是个bandit22的crontab文件，表示在系统启动的时候，以bandit22的身份运行`/usr/bin/cronjob_bandit22.sh`，并且丢弃所有输出  
第二行是每分钟都以bandit22的身份运行，细节同上  
所以看一下它运行的sh脚本是什么  

`cat /usr/bin/cronjob_bandit22.sh`  

```
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

可以看到该脚本把bandit22的密码输出到一个文件里了，看一下就行  

`cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`  

```
WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
```

至于密码明明就在老位置，为什么不直接看，因为没权限┑(￣Д ￣)┍  
明明定时任务也是以bandit22的身份运行的  
不懂，放着先_(:з)∠)_  

### 密码

```
WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
```

## Level 22 -> Level 23

### 原文翻译分析

> A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

> NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

> 基于时间的工作调度程序 cron 正在定期自动运行一个程序。查看 /etc/cron.d/ 中的配置，看看执行的是什么命令。

> 注意：查看他人编写的 shell 脚本是一项非常有用的技能。本关卡的脚本故意做得简单易读。如果在理解脚本内容时遇到困难，请尝试执行脚本，查看脚本打印的调试信息。

### 相关知识

`Linux crontab`  
`Linux shell脚本`  

### 具体操作

`cd /etc/cron.d/`  
`ls`  

```
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24       e2scrub_all  sysstat
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root  otw-tmp-dir
```

`cat cronjob_bandit23`  
```
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
```

`cat /usr/bin/cronjob_bandit23.sh`  
目前为止都和上一关没什么主要的区别，但是运行的shell脚本这里开始不同，需要理解脚本内容  

```bash
#!/bin/bash

myname=$(whoami) # 把变量myname赋值为当前用户名
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1) # 把变量mytarget赋值为根据变量myname计算出来的值

# 下面两行都只是调用变量
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

如果不太懂这写的啥可以运行一下  
`/usr/bin/cronjob_bandit23.sh`  

```
Copying passwordfile /etc/bandit_pass/bandit22 to /tmp/8169b67bd894ddbb4412f91573b38db3
```

看运行结果好像和上一关的一样，都是把密码写出来，但是你细看，为毛写的是bandit22的密码，这不bandit23运行的东西吗  
因为该shell脚本里输出密码的部分用了变量，输出的密码根据运行该脚本的用户而决定  
看上面代码写的注释吧（  

**TL;DR** 
总之因为没有bandit23的身份，自己运行这个脚本只能打出现在bandit22的密码  
但是，因为这个脚本是被crontab定时运行的，所以密码是已经被存到一个位置了的，找到那个位置就行  
那么只要把计算出变量`mytarget`这一行复制一下，然后把`$myname`改成`bandit23`就能得到bandit23用户运行该脚本时的位置了  

`echo I am user bandit23 | md5sum | cut -d ' ' -f 1`  
这是结果：8ca319486bfbbc3663ea0fbe81326349  
`cat /tmp/8ca319486bfbbc3663ea0fbe81326349`  

```
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
```

### 密码

```
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
```

## Level 23 -> Level 24

### 原文翻译分析

> A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  
> NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!  
> NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…  

> 基于时间的工作调度程序 cron 正在定期自动运行一个程序。查看 /etc/cron.d/ 中的配置，看看执行的是什么命令。  
> 注 1：该level要要你自己写一个shell 脚本哩。这是非常重要的一步，当你通过这一关时，你应该为自己感到骄傲！（迫真  
> 注 2：对了哟，你的脚本执行完就会被删掉了，所以注意自己存一下哈  

### 相关知识

### 具体操作

```
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```

`cd /var/spool/bandit24/foo`  
`vim a`  
切到可以运行脚本的文件夹，用vim创建一个shell脚本，记得给脚本加可执行权限  

```bash
#!/bin/bash
mkdir /tmp/Soul
cat /etc/bandit_pass/bandit24 > /tmp/Soul/bandit24
```

`chmod -x a`  
一定要加  
一定要加  
一定要加  

然后等就行了，可以`cat a`看一下文件还在不在，不在了就是执行了，然后去看看密码有没有生成  
`cat /tmp/Soul/bandit24`  

```
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
```

### 密码

```
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
```

## Level 24 -> Level 25

### 原文翻译分析

> A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.  
> You do not need to create new connections each time  

> 一个守护进程在 30002 端口监听，如果给你 bandit24 的密码和一个 4 位数的数字密码，它就会告诉你 bandit25 的密码。
> 除了遍历所有 10000 种组合（称为 "暴力破解"）之外，没有其他办法获取密码。  
> 小提示：不用每次都创建新的连接。  

### 相关知识

### 具体操作

`for i in {0..9999}; do echo $i ; echo VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i | nc -q 0 localhost 30002; done`  
一开始我是这样做的，然后因为每一次尝试都要重新开启连接，所以速度奇慢。  

那么为什么不直接把所有可能性作为一个输入传给`nc`呢  
所以先在`/tmp`里面创建一个文件夹用来写文件  
`mkdir /tmp/Soul`  
`cd /tmp/Soul`  

接下来用一个循环把密码加上一个空格，和所有可能的四位数字输出到一个文件  
`for i in {1000..9999}; do echo VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i >> a.txt; done`  

然后用`nc`连接，并且把输入重定向到刚才的文件，并且把输出重定向到一个文件  
（不然几千条Wrong!你看什么，这样可以完事后直接`/pass`搜就能搜到密码的位置  
`nc localhost 30002 < a.txt > out.txt`  

```
/pass
...skipping
Wrong! Please enter the correct pincode. Try again.
Correct!
The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d
```

### 密码

```
p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d
```

## Level 25 -> Level 26

### 原文翻译分析

> Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

> 从bandit25登录到bandit26本应该很容易的...，但是bandit26的shell不是/bin/bash/，而是其他的什么，找到它是什么，以及怎么摆脱它。

### 相关知识

`more`  
在`more`的显示部分文本的状态下，按`v`键可以进入`vi`  
![more](_v_images/20231008232035163_14416.png)  

按下`v`后  
![vi](_v_images/20231008232101622_3420.png)

`vi`  
`vi`可以运行外部命令，`:!command`  
`vi`运行命令时使用的貌似是用户的默认shell，但是可以更改vi里使用的shell，以bash为例，`(:set shell=/bin/bash)`（必须系统有）  


### 具体操作

bandit25的home目录下就有bandit26的ssh key，具体添加和多密钥管理不想第三次重复了，直接看前面的  

```
-----BEGIN RSA PRIVATE KEY-----
MIIEpQIBAAKCAQEApis2AuoooEqeYWamtwX2k5z9uU1Afl2F8VyXQqbv/LTrIwdW
pTfaeRHXzr0Y0a5Oe3GB/+W2+PReif+bPZlzTY1XFwpk+DiHk1kmL0moEW8HJuT9
/5XbnpjSzn0eEAfFax2OcopjrzVqdBJQerkj0puv3UXY07AskgkyD5XepwGAlJOG
xZsMq1oZqQ0W29aBtfykuGie2bxroRjuAPrYM4o3MMmtlNE5fC4G9Ihq0eq73MDi
1ze6d2jIGce873qxn308BA2qhRPJNEbnPev5gI+5tU+UxebW8KLbk0EhoXB953Ix
3lgOIrT9Y6skRjsMSFmC6WN/O7ovu8QzGqxdywIDAQABAoIBAAaXoETtVT9GtpHW
qLaKHgYtLEO1tOFOhInWyolyZgL4inuRRva3CIvVEWK6TcnDyIlNL4MfcerehwGi
il4fQFvLR7E6UFcopvhJiSJHIcvPQ9FfNFR3dYcNOQ/IFvE73bEqMwSISPwiel6w
e1DjF3C7jHaS1s9PJfWFN982aublL/yLbJP+ou3ifdljS7QzjWZA8NRiMwmBGPIh
Yq8weR3jIVQl3ndEYxO7Cr/wXXebZwlP6CPZb67rBy0jg+366mxQbDZIwZYEaUME
zY5izFclr/kKj4s7NTRkC76Yx+rTNP5+BX+JT+rgz5aoQq8ghMw43NYwxjXym/MX
c8X8g0ECgYEA1crBUAR1gSkM+5mGjjoFLJKrFP+IhUHFh25qGI4Dcxxh1f3M53le
wF1rkp5SJnHRFm9IW3gM1JoF0PQxI5aXHRGHphwPeKnsQ/xQBRWCeYpqTme9amJV
tD3aDHkpIhYxkNxqol5gDCAt6tdFSxqPaNfdfsfaAOXiKGrQESUjIBcCgYEAxvmI
2ROJsBXaiM4Iyg9hUpjZIn8TW2UlH76pojFG6/KBd1NcnW3fu0ZUU790wAu7QbbU
i7pieeqCqSYcZsmkhnOvbdx54A6NNCR2btc+si6pDOe1jdsGdXISDRHFb9QxjZCj
6xzWMNvb5n1yUb9w9nfN1PZzATfUsOV+Fy8CbG0CgYEAifkTLwfhqZyLk2huTSWm
pzB0ltWfDpj22MNqVzR3h3d+sHLeJVjPzIe9396rF8KGdNsWsGlWpnJMZKDjgZsz
JQBmMc6UMYRARVP1dIKANN4eY0FSHfEebHcqXLho0mXOUTXe37DWfZza5V9Oify3
JquBd8uUptW1Ue41H4t/ErsCgYEArc5FYtF1QXIlfcDz3oUGz16itUZpgzlb71nd
1cbTm8EupCwWR5I1j+IEQU+JTUQyI1nwWcnKwZI+5kBbKNJUu/mLsRyY/UXYxEZh
ibrNklm94373kV1US/0DlZUDcQba7jz9Yp/C3dT/RlwoIw5mP3UxQCizFspNKOSe
euPeaxUCgYEAntklXwBbokgdDup/u/3ms5Lb/bm22zDOCg2HrlWQCqKEkWkAO6R5
/Wwyqhp/wTl8VXjxWo+W+DmewGdPHGQQ5fFdqgpuQpGUq24YZS8m66v5ANBwd76t
IZdtF5HXs2S5CADTwniUS5mX1HO9l5gUkk+h0cH5JnPtsMCnAUM+BRY=
-----END RSA PRIVATE KEY-----
```

加了bandit26的密钥以后就能登录了，只是，给个字符画以后就给踢出来了qwq  
先把自己终端的窗口高度拉小，只有一两行那样  
然后登录到bandit26，之后会触发`more`  
![more](_v_images/20231008235620729_16992.png)  
这时候按`v`键，会进入`vi`  
然后可以把窗口调回去了  
![vi](_v_images/20231008235758881_18254.png)  

接下来把`vi`的shell改成bash  
`:set shell=/bin/bash`  

然后从vi里面启动shell，打开一个终端  
`:shell`  
![shell](_v_images/20231009000221135_493.png)  

不管怎样先看密码  
`cat /etc/bandit_pass/bandit26`  

```
c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
```

然后先别退，直接跟着继续搞27，因为这里连着的，退了搞27又要重来上面这些  

### 密码

```
c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
```

## Level 26 -> Level 27

### 原文翻译分析

> Good job getting a shell! Now hurry and grab the password for bandit27!

> 好耶你搞到shell力！，现在快去搞bandit27的密码！  

### 相关知识

### 具体操作

`ls`  

```
bandit27-do  text.txt
```

`./bandit27-do cat /etc/bandit_pass/bandit27`  

```
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
```

### 密码

```
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
```

## Level 27 -> Level 28

### 原文翻译分析

> There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.  
> Clone the repository and find the password for the next level.  

> 经由2220端口，ssh://bandit27-git@localhost/home/bandit27-git/repo，有一个git仓库，用户bandit27-git的密码和用户bandit27的密码一样  
> 克隆仓库找密码  

### 相关知识

`git`, `git clone`  
`git clone`使用ssh并且指定端口，方法是在主机名后面加上`:端口号`  
[可以参考这个](https://zhuanlan.zhihu.com/p/337388772)  

### 具体操作

`mkdir /tmp/Soul`  
`cd /tmp/Soul`  
`git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo`  

```
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

输入yes  

```
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit27-git@localhost's password:
```

粘贴bandit27的密码：YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS  

```
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```

`cd repo/`  
`cat README`  
`The password to the next level is: AVanL161y9rsbcJIsFHuw35rjaOM19nR`  

### 密码

```
AVanL161y9rsbcJIsFHuw35rjaOM19nR
```

## Level 28 -> Level 29

### 原文翻译分析

> There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.  
> Clone the repository and find the password for the next level.  

> 经由2220端口，ssh://bandit28-git@localhost/home/bandit28-git/repo，有一个git仓库，用户bandit28-git的密码和用户bandit28的密码一样  
> 克隆仓库找密码  
> 不是这两个除了数字7变成8，一点变化没有，太水了吧  

### 相关知识

`git`, `git clone`, `git reset --hard`  

### 具体操作

创建文件夹到clone的步骤都和上一关一样所以不赘述了，只说不同的地方  
`cat README.md`  

```
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
```

很明显这个文件被改过了，所以看一下git仓库的历史，找到修改前的提交回溯就行了  
`git log`  

```
commit 14f754b3ba6531a2b89df6ccae6446e8969a41f3 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    fix info leak

commit f08b9cc63fa1a4602fb065257633c2dae6e5651b
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    add missing data

commit a645bcc508c63f081234911d2f631f87cf469258
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    initial commit of README.md
```

就三个提交，看描述，瞎猜都能猜到是第二次提交写了密码上去  
复制第二次提交的哈希值，然后用`git reset --hard 哈希值`回溯版本  
`git reset --hard f08b9cc63fa1a4602fb065257633c2dae6e5651b`  
`cat README.md`  

```
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
```

### 密码

```
tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
```

## Level 29 -> Level 30

### 原文翻译分析

> There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.  
> Clone the repository and find the password for the next level.  

>  不想翻译了，除了8变成9其他都一样，没必要翻译了  

### 相关知识

`git branch -a`  
 `git checkout -b 远程分支`  

### 具体操作

一样，相同的创建文件夹clone仓库什么的不说了  
`cat README.md`  

```
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```

`git log`  

```
commit 4364630b3b27c92aff7b36de7bb6ed2d30b60f88 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:43 2023 +0000

    fix username

commit fca34ddb7d1ff1f78df36538252aea650b0b040d
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:43 2023 +0000

    initial commit of README.md
```

看这历史，这个分支根本没密码，那个`fix username`真的只是改了下用户名（问就是我看过了  
`git branch`  

```
* master
```

现在仓库也没有别的分支，能想到的关于这个仓库藏东西的就是远程仓库了  
`git branch -a`  

```
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
```

其中，`remotes/origin/master`就是当前指向的分支，所以不用看了，看看dev那个  
`git checkout -b dev remotes/origin/dev`  
`ls`  

```
code  README.md
```

`cat README.md`  

```
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS
```

所以bandit30的密码就这个了，`sploits-dev`那个分支一样的，还有那个`code`文件夹也没东西，只有一个空的`gif2ascii.py`  

### 密码

```
xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS
```

## Level 30 -> Level 31

### 原文翻译分析

> There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.  
Clone the repository and find the password for the next level.  

> (ˉ▽ˉ；)...  

### 相关知识

`git tag`  
[更多关于git 标签的参考](https://zhuanlan.zhihu.com/p/622331227)  

### 具体操作

```
cat README.md
just an epmty file... muahaha
```

> 《muhaha》  

上面两关的都试了也找不到，然后...git的标签了解一下  
`git tag`  

```
secret
```

`git show secret`  

```
OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt
```

这应该是个附注标签，把密码藏标签里了  


### 密码

```
OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt
```

## Level 31 -> Level 32

### 原文翻译分析

> There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.  
> Clone the repository and find the password for the next level.

> 不想多说什么了...  

### 相关知识

`git commit`, `git push`  

### 具体操作

`cat README.md`  

```
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

看来是要用`git push`提交一个文件，细节都写上了，文件名，内容，所处的分支，照着创建这个文件就好了  

这里要加`-f`强制提交，因为仓库设置了忽略  
`"a"`是提交的描述，随便写也行  
`git add -f key.txt`  
`git commit -m "a"`  
`git push`  

直接把提交后的过程全部贴下面了  

```
bandit31@bandit:/tmp/Soul4/repo$ git push
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit31/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 315 bytes | 315.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
remote: Well done! Here is the password for the next level:
remote: rmCBvG56y58BXzv98yZGdO7ATVL5dW8y
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
To ssh://localhost:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://localhost:2220/home/bandit31-git/repo'
```

> .o0o.中间就是......  

### 密码

```
rmCBvG56y58BXzv98yZGdO7ATVL5dW8y
```

## Level 32 -> Level 33

### 原文翻译分析

> After all this git stuff its time for another escape. Good luck!
> 搞了半天的git，现在搞点别的。

### 相关知识

[Linux里shell下$](https://blog.csdn.net/u012114090/article/details/81123535)  

### 具体操作

```
bandit31@bandit:~$ cat /etc/passwd | grep bandit32
bandit32:x:11032:11032:bandit level 32:/home/bandit32:/home/bandit32/uppershell
bandit31@bandit:~$ cat /home/bandit32/uppershell
cat: /home/bandit32/uppershell: Permission denied
```

bandit32的shell被改了，但是看不了那个uppershell具体是什么  
登录时`more`也触发不了  
然后，懵逼了半天去discord问，看到个$才想起什么，  
我刚刚还写shell脚本用来生成标题...`$1`可以代表第一个参数，`$0`就是shell本身的名字  
所以，字母被搞了就别输入字母呗，用符号你怎么转大写（  

---

`$0`  
![shell](_v_images/20231024220945675_18044.png)  

`cat /etc/bandit_pass/bandit33`  

```
odHo63fHiFqcWWJG9rLiLDtPm45KzUKy
```

### 密码

```
odHo63fHiFqcWWJG9rLiLDtPm45KzUKy
```