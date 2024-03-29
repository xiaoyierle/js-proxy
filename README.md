# gh-proxy

## 简介

github release、archive以及项目文件的加速项目，支持clone，有Cloudflare Workers无服务器版本以及Python版本

## 演示


## 使用

直接在copy出来的url前加`https://cloudflare.xiaoyierle.workers.dev/`即可

也可以直接访问，在input输入

***大量使用请自行部署，以上域名仅为演示使用。***

以下都是合法输入（仅示例，文件不存在）：

- 分支源码：https://github.com/xiaoyierle/project/archive/master.zip

- release源码：https://github.com/xiaoyierle/project/archive/v0.1.0.tar.gz

- release文件：https://github.com/xiaoyierle/project/releases/download/v0.1.0/example.zip

- 分支文件：https://github.com/xiaoyierle/project/blob/master/filename

- commit文件：https://github.com/xiaoyierle/project/blob/xxxxxxxxxxxxxxxxxxxx/filename


## cf worker版本部署

首页：https://workers.cloudflare.com

注册，登陆，`Start building`，取一个子域名，`Create a Worker`。

复制 [index.js](https://github.com/xiaoyierle/js-proxy/index.js)  到左侧代码框，`Save and deploy`。如果正常，右侧应显示首页。

`index.js`默认配置下clone走github.com.cnpmjs.org，项目文件会走jsDeliver，如需走worker，修改Config变量即可

`ASSET_URL`是静态资源的url（实际上就是现在显示出来的那个输入框单页面）

`PREFIX`是前缀，默认（根路径情况为"/"），如果自定义路由为example.com/gh/*，请将PREFIX改为 '/gh/'，注意，少一个杠都会错！

### 注意

python版本的机器如果无法正常访问github.io会启动报错，请自行修改静态文件url

workers版本默认配置下clone走github.com.cnpmjs.org，项目文件会走jsDeliver，如需走服务器，修改配置即可

python版本默认走服务器（2021.3.27更新）

## Cloudflare Workers计费

到 `overview` 页面可参看使用情况。免费版每天有 10 万次免费请求，并且有每分钟1000次请求的限制。

如果不够用，可升级到 $5 的高级版本，每月可用 1000 万次请求（超出部分 $0.5/百万次请求）。

## Changelog

* 2020.04.09 增加Python版本（使用Flask）
* 2020.03.23 新增了clone的支持
* 2020.03.22 初始版本

## 参考

[jsproxy](https://github.com/EtherDream/jsproxy/)

