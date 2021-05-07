# yapi

原由 YApi 更新太慢，只支持 postman v1，实际postman已经不支持 postman v1的导出了。

基于最新 v1.9.2 版本改造 YApi 接口文档管理平台，支持导入 Postman Collection V2 的 json 数据，支持二级文件夹分组。

原体验地址：

[https://yapi.baidu.com](https://yapi.baidu.com)

原文档：
<p><a target="_blank" href="https://yapi.baidu.com/doc/documents/index.html">yapi.baidu.com/doc/documents</a></p>

YApi 是<strong>高效</strong>、<strong>易用</strong>、<strong>功能强大</strong>的 api 管理平台，旨在为开发、产品、测试人员提供更优雅的接口管理服务。可以帮助开发者轻松创建、发布、维护 API，YApi 还为用户提供了优秀的交互体验，开发人员只需利用平台提供的接口数据写入工具以及简单的点击操作就可以实现接口的管理。

### 特性
*  基于 Json5 和 Mockjs 定义接口返回数据的结构和文档，效率提升多倍
*  扁平化权限设计，即保证了大型企业级项目的管理，又保证了易用性
*  类似 postman 的接口调试
*  自动化测试, 支持对 Response 断言
*  MockServer 除支持普通的随机 mock 外，还增加了 Mock 期望功能，根据设置的请求过滤规则，返回期望数据
*  支持 postman, har, swagger 数据导入
*  免费开源，内网部署，信息再也不怕泄露了

### 内网部署
#### 环境要求
* ubuntu 14
* nodejs（12.22.1+)
* mongodb（4.2.6+）

#### 安装
 
    mkdir yapi
    cd yapi
    git clone git@github.com:nasireddin/yapi.git vendors //或者下载 zip 包解压到 vendors 目录（clone 整个仓库大概 140+ M，可以通过 `git clone --depth=1 git@github.com:nasireddin/yapi.git vendors` 命令减少，大概 10+ M）
    cp vendors/config_example.json ./config.json //复制完成后请修改相关配置
    cd vendors
    npm install --production --registry https://registry.npm.taobao.org
    npm run install-server //安装程序会初始化数据库索引和管理员账号，管理员账号名为 admin@admin.com，默认密码为 ymfe.org 登录系统（默认密码可在个人中心修改）
    node server/app.js //启动服务器后，请访问 127.0.0.1:{config.json配置的端口}，初次运行会有个编译的过程，请耐心等候
    
#### 服务管理
利用pm2方便服务管理维护。

    npm install pm2 -g  //安装pm2
    cd  {项目目录}
    pm2 start "vendors/server/app.js" --name yapi //pm2管理yapi服务
    pm2 info yapi //查看服务信息
    pm2 stop yapi //停止服务
    pm2 restart yapi //重启服务

### 赞赏
 <img width="200" width="200" src="https://img.wenhairu.com/images/2021/04/29/a0Zh6.jpg">

### License
Apache License 2.0