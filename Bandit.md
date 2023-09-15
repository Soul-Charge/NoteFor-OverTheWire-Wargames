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

`ls` , `cat`

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

`ls` `cat`
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

`ls` `cat`
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

### 相关知识

### 具体操作

### 密码

## Level 4 -> Level 5

### 原文翻译分析

### 相关知识

### 具体操作

### 密码

## Level 5 -> Level 6

### 原文翻译分析

### 相关知识

### 具体操作

### 密码

## Level 6 -> Level 7

### 原文翻译分析

### 相关知识

### 具体操作

### 密码

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
