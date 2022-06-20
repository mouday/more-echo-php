# more-echo-php

a demo for PHP composer

一个PHP的composer包发布示例

## 1、初始化项目

```bash
mkdir more-echo-php

cd more-echo-php

# 初始化项目, 填写好项目的信息
$ composer init
```

项目目录
```bash
$ tree -I vendor
.
├── README.md
├── composer.json
└── src
    └── EchoText.php

```

composer.json
```json
{
    "name": "mouday/more-echo",
    "description": "a demo for Composer",
    "type": "library",
    "license": "MIT",
    "autoload": {
        "psr-4": {
            "Mouday\\MoreEcho\\": "src/"
        }
    },
    "authors": [
        {
            "name": "pengshiyu",
            "email": "1940607002@qq.com"
        }
    ],
    "require": {}
}
```

src/EchoText.php
```php
<?php


namespace Mouday\MoreEcho;

/**
 * a demo for php composer
 * Class EchoText
 * @package Mouday\MoreEcho
 */
class EchoText
{
    public static function echoText($text)
    {
        echo $text;
    }
}
```

## 发布项目

1. 将项目提交到github
2. 将项目发布到packagist，点击submit输入github的项目地址

发布包地址：
- packagist: [https://packagist.org/packages/mouday/more-echo](https://packagist.org/packages/mouday/more-echo)
- github: [https://github.com/mouday/more-echo-php](https://github.com/mouday/more-echo-php)

## 使用发布的包

安装包

```
composer require mouday/more-echo
```
示例

```php
<?php

require './vendor/autoload.php';

use  Mouday\MoreEcho\EchoText;

EchoText::echoText('Hello World!');
// Hello World!
```

## 问题

1、提示composer.json找不到

```
[RuntimeException]                                                                                    
  No composer.json present in the current directory (./composer.json), 
  this may be the cause of the following exception. 
```

```bash
echo '{}' > composer.json
```

2、包不存在

通常我们使用的是阿里云的镜像地址，刚提交的包，可能没有及时同步，可以临时设置一下包下载地址

```bash
$ composer config repo.packagist composer https://packagist.org/
```

3、版本号找不到

```
  [InvalidArgumentException]                                                                            
  Could not find a version of package mouday/more-echo matching your minimum-stability (stable). 
  Require it with an explicit version constraint allowing its desired stability. 
```

给项目打一个版本号的标签
```
git tag 1.0.0
 
git push --tag 
```

>参考
[php composer Packagist 创建第一个自己的包](https://blog.csdn.net/Kai_Wai/article/details/120473898)
[101- composer \[packagist\]包制作（入门篇）](https://www.jianshu.com/p/1eeaad7ec31a/)