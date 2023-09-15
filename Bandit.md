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

### 相关知识

### 具体操作

### 密码

## Level 8 -> Level 9

### 原文翻译分析

### 相关知识

### 具体操作

### 密码

## Level 9 -> Level 10

### 原文翻译分析

### 相关知识

### 具体操作

### 密码

## Level 10 -> Level 11

### 原文翻译分析

### 相关知识

### 具体操作

### 密码

## Level 11 -> Level 12

### 原文翻译分析

### 相关知识

### 具体操作

### 密码

## Level 12 -> Level 13

### 原文翻译分析

### 相关知识

### 具体操作

### 密码

## Level 13 -> Level 14

### 原文翻译分析

### 相关知识

### 具体操作

### 密码
