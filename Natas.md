# OverTheWire Natas

[介绍页](https://overthewire.org/wargames/natas/)  
省流：反正就是用浏览器打开就行了  

## Level 0

```text
Username: natas0
Password: natas0
URL:      http://natas0.natas.labs.overthewire.org
```

## Level 0 -> Level 1

用浏览器打开，填账号密码就行啦  
然后嘛，下一关的密码就在注释里面，打开控制台就能看到了  
> 浏览器按F12打开控制台  

```
<div id="content">
You can find the password for the next level on this page.

<!--The password for natas1 is g9D9cREhslqBKtcA2uocGHPfMZVzeFK6 -->
</div>
```

### 密码

```
g9D9cREhslqBKtcA2uocGHPfMZVzeFK6
```

## Level 1 -> Level 2

> You can find the password for the next level on this page, but rightclicking has been blocked!  
> 合着我刚才那关用的右键->检查是吧(ˉ▽ˉ；)...  

还是一样，打开控制台就能找到，在注释里面  

```html
<!--The password for natas2 is h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7 -->
```

### 密码

```
h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7
```

## Level 2 -> Level 3

> There is nothing on this page  
> 没有东西我找啥(ˉ▽ˉ；)...  

打开控制台，能看到有一个单像素大小的图片，当然密码不会在图片里，303B的大小感觉不会是隐写的。  

```html
<div id="content">
There is nothing on this page
<img src="files/pixel.png">
</div>
```

然后呢，这个图片有什么特别的？它是一个提示，因为可以往前面看看，其他关是没有这个图片的  
结合页面提示”这个页面什么都没有“所以，去看看这个图片的来源吧  
控制台查看元素，右键图片src=""里的部分，在新标签页中打开  
http://natas2.natas.labs.overthewire.org/files/pixel.png  
把这个链接改一下，去掉pixel.png就行了  
于是打开了natas2的文件目录页面  

```
Index of /files
[ICO]	Name	Last modified	Size	Description
[PARENTDIR]	Parent Directory	 	-	 
[IMG]	pixel.png	2023-10-05 06:15	303	 
[TXT]	users.txt	2023-10-05 06:15	145	 
Apache/2.4.52 (Ubuntu) Server at natas2.natas.labs.overthewire.org Port 80
```

> 大概就是这样，我直接复制粘贴纯文本的，能看出来就行（  

点击那个users.txt看看  

```
# username:password
alice:BYNdCesZqW
bob:jw2ueICLvT
charlie:G5vCxkVV3m
natas3:G6ctbMJ5Nb4cbFwhpMPSvxGHhQ7I6W8Q
eve:zo4mJWyNj2
mallory:9urtcpzBmH
```

ok密码就在这  

### 密码

```
G6ctbMJ5Nb4cbFwhpMPSvxGHhQ7I6W8Q 
```

## Level 3 -> Level 4

### 密码

```
```

## Level 4 -> Level 5

### 密码

```
```

## Level 5 -> Level 6

### 密码

```
```

## Level 6 -> Level 7

### 密码

```
```

## Level 7 -> Level 8

### 密码

```
```

## Level 8 -> Level 9

### 密码

```
```

## Level 9 -> Level 10

### 密码

```
```

## Level 10 -> Level 11

### 密码

```
```

## Level 11 -> Level 12

### 密码

```
```

## Level 12 -> Level 13

### 密码

```
```

## Level 13 -> Level 14

### 密码

```
```

## Level 14 -> Level 15

### 密码

```
```

## Level 15 -> Level 16

### 密码

```
```

## Level 16 -> Level 17

### 密码

```
```

## Level 17 -> Level 18

### 密码

```
```

## Level 18 -> Level 19

### 密码

```
```

## Level 19 -> Level 20

### 密码

```
```

## Level 20 -> Level 21

### 密码

```
```

## Level 21 -> Level 22

### 密码

```
```

## Level 22 -> Level 23

### 密码

```
```

## Level 23 -> Level 24

### 密码

```
```

## Level 24 -> Level 25

### 密码

```
```

## Level 25 -> Level 26

### 密码

```
```

## Level 26 -> Level 27

### 密码

```
```

## Level 27 -> Level 28

### 密码

```
```

## Level 28 -> Level 29

### 密码

```
```

## Level 29 -> Level 30

### 密码

```
```

## Level 30 -> Level 31

### 密码

```
```

## Level 31 -> Level 32

### 密码

```
```

## Level 32 -> Level 33

### 密码

```
```

## Level 33 -> Level 34

### 密码

```
```
