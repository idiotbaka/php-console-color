# php-console-color
 PHP 简易类，在控制台绘制文字样式，以及进度条

### 快速使用

打印出红色的控制台文字：

```php
echo kalor::text('hello, world', kalor::RED);
```

打印出黄色的控制台文字，并换一行（第三个参数为true）：

```php
echo kalor::text('hello, world', kalor::YELLOW, true);
```

打印出白色的控制台文字，背景色为深绿色，带有下划线（多种样式时，第二个参数是数组），并换一行：

```php
echo kalor::text('hello, world', [kalor::WHITE, kalor::BG_DARKGREEN, kalor::_UNDERLINE], true);
```



### 支持的颜色

| 颜色 | 文字值    | 背景值       |
| ---- | --------- | ------------ |
| 黑   | BLACK     | BG_BLACK     |
| 红   | RED       | BG_RED       |
| 绿   | GREEN     | BG_GREEN     |
| 黄   | YELLOW    | BG_YELLOW    |
| 蓝   | BLUE      | BG_BLUE      |
| 紫   | PURPLE    | BG_PURPLE    |
| 深绿 | DARKGREEN | BG_DARKGREEN |
| 白   | WHITE     | BG_WHITE     |

### 支持的样式

| 样式名                   | 值             |
| ------------------------ | -------------- |
| 高亮（部分环境中为加粗） | _LIGHT         |
| 弱化                     | _DIM           |
| 斜体                     | _ITALIC        |
| 下划线                   | _UNDERLINE     |
| 闪烁                     | _TWINKLE       |
| 快速闪烁                 | _TWINKLE_QUICK |
| 反色                     | _INVERSE       |
| 隐藏                     | _HIDE          |
| 删除线                   | _STRIKETHROUGH |

不是所有的控制台都支持以上样式。

### 进度条

简单的百分比进度条，进度条label显示 download... ：

```php
// 百分比进度，支持两位小数，范围0~100
$progress = 0;
while($progress < 100) {
    $progress += 10;
    // 如果进度为100时，会自动换一行
    echo kalor::progressBarPercent('download...', $progress);
    sleep(1);
}
```

在进度条的后方显示信息，例如下载速度：

```php
echo kalor::progressBarPercent(['download...', rand(100, 999).'kb/s'], $progress);
```

自定义进度条字符长度，传入第三个参数（默认50）：

```php
echo kalor::progressBarPercent(['download...', rand(100, 999).'kb/s'], $progress, 10);
```

自定义进度条字符，传入第四个参数（数组，分别是进度完成部分和未完成部分）：

```php
echo kalor::progressBarPercent(['download...', rand(100, 999).'kb/s'], $progress, 50, ['>', '_']);
```

步骤进度条，后方显示的不是百分比而是步骤进度（第二个参数为数组，分别是当前进度和总进度）：

```
$progress = 0;
while($progress < 5) {
    $progress ++;
    echo kalor::progressBarStep('download file '.$progress.'...', [$progress, 5]);
    sleep(1);
}
```

