# JPush API PHP Client

这是 JPush REST API 的 PHP 版本封装开发包，是由极光推送官方提供的，一般支持最新的 API 功能。

对应的 REST API 文档: https://docs.jiguang.cn/jpush/server/push/server_overview/


## Installation

#### 使用 Composer 安装

```json
composer require nizerin/jpush-mini
```

## Usage

- [Init API](https://github.com/jpush/jpush-api-php-client/blob/master/doc/api.md#init-api)
- [Push API](https://github.com/jpush/jpush-api-php-client/blob/master/doc/api.md#push-api)
- [Exception Handle](https://github.com/jpush/jpush-api-php-client/blob/master/doc/api.md#schedule-api)
- [HTTP/2 Support](https://github.com/jpush/jpush-api-php-client/blob/master/doc/http2.md)
- [Group Push](https://github.com/jpush/jpush-api-php-client/blob/master/doc/grouppush.md)

#### 初始化

```php
use JPush\Client as JPush;
...
...

    $client = new JPush($app_key, $master_secret);

...
```

OR

```php
$client = new \JPush\Client($app_key, $master_secret);
```

#### 简单推送

```php
$client->push()
    ->setPlatform('all')
    ->addAllAudience()
    ->setNotificationAlert('Hello, JPush')
    ->send();
```

#### 异常处理

```php
$pusher = $client->push();
$pusher->setPlatform('all');
$pusher->addAllAudience();
$pusher->setNotificationAlert('Hello, JPush');
try {
    $pusher->send();
} catch (\JPush\Exceptions\JPushException $e) {
    // try something else here
    print $e;
}
```

## Examples

**注意: 这只是使用样例, 不应该直接用于实际环境中!!**

在下载的中的 [examples](https://github.com/jpush/jpush-api-php-client/tree/master/examples) 文件夹有简单示例代码, 开发者可以参考其中的样例快速了解该库的使用方法。

> **注：所下载的样例代码不可马上使用，需要在 `examples/config.php` 文件中填入相关的必要参数，或者设置相关环境变量，不进行这个操作则示例运行会失败。**另外为保护开发者隐私 examples/config.php 文件不在版本控制中，需要使用如下命令手动复制：

```bash
$ cp examples/config.php.example examples/config.php
```

**简单使用方法**

若要运行 push_example.php 中的示例代码：

``` bash
# 假定当前目录为 JPush 源码所在的根目录
$ php examples/push_example.php
```
> 同时也可编辑相关的示例文件，更改参数查看执行效果

## Testing

```bash
# 编辑 tests/bootstrap.php 文件，填入必须的变量值
# OR 设置相应的环境变量

# 运行全部测试用例
$ composer tests

# 运行某一具体测试用例
$ composer tests/JPush/xxTest.php
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/jpush/jpush-api-php-client.

## License

The library is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
