<img alt="iptv-checker" src="https://github.com/zhimin-dev/iptv-checker/blob/react-version/src/assets/icon.png" height=80>

# iptv-checker

支持m3u链接、m3u源文件以及提供公共的源，选择对应的操作，然后点击确定，可以帮助你检查这些源是否有效，并将这些有效的另存为新的m3u文件

iptv-checker不再支持chrome扩展，后续chrome扩展将改为在线播放m3u小工具，[项目地址](https://github.com/zhimin-dev/iptv-player)

## 二次开发

如果基于源码启动`npm run dev`时,出现`No matching export in "node_modules/react-virtualized/dist/es/WindowScroller/WindowScroller.js" for import "bpfrpt_proptype_WindowScroller"` 这样的错误，请输入`npx patch-package`可解决

## Docker本地编译使用方法

下载源码，执行下面命令，再访问浏览器`http://127.0.0.1:8081/`即可

```bash
npm run build
docker build -t ipserver .
docker run -d -p 8081:8080 --name myIp ipserver
```

## Docker官方包使用方法

首先下载已经打包好的镜像（执行下面命令），[DockerHub](https://hub.docker.com/r/zmisgod/iptvchecker)地址

```bash
docker pull zmisgod/iptvchecker
docker run -d -p 8081:8080 --name myIp zmisgod/iptvchecker
```

再打开浏览器访问`http://127.0.0.1:8081/`即可

## Docker本地打多平台包方法

```bash
docker buildx create --name mybuilder
docker buildx inspect --bootstrap
docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7 -t zmisgod/iptvchecker:latest --push .
```

## Docker-Compose 部署

```bash
docker-compose up -d
```

## 变更日志

- v2.16 开发预告
  - 支持并发请求
  - 服务端更换golang
  - 支持后台服务
- v2.15.1
  - 支持显示直播源速度,并支持自动选择最快的源数据
  - 优化代码，删除无用代码
  - 更换排序组建(替换sort : https://dndkit.com/)
  - 支持node 18
  - 修复检查超市时间未生效的bug
- v2.15.0
  - 支持视频宽高、音频信息查看,并支持清晰度筛选
  - ⚠️不再支持chrome扩展，历史兼容chrome扩展代码已删除
- v2.14.0
  - 修复设置超时输入框输入字母后会出现NaN的问题
  - 增加检查直播源链接时的暂停功能
  - 增加导出csv格式
  - 尝试修复内存泄漏问题
- v2.13.1
  - 将docker模式中观看入口去掉
- v2.13
  - 支持docker
- v2.12
  - 支持本地文件上传
- v2.11
  - 修复bug
    - 详情页搜索因输入字母大小不匹配而搜索不出来的问题
    - 从详情页的在线观看按钮点进后与选中的频道不一致的问题
  - 新增更换频道分组功能
    - v2.11.1 紧急修复分组无法添加绑定的bug
  - 详情页单个频道进行修改相关信息

- v2.10
  - 导出增加结果排序
- v2.9
  - 首页输入框增加记忆功能，点击的tab以及输入的文本在刷新页面后不会清空
  - 详情页面增加页面搜索提示功能，增加了对groupTitle的支持
  - 对于非m3u格式的文件数据进行支持groupTitle字段，方便用户搜索过滤
  - 将hls.js更换为video.js，在线观看退出后，原视频不会继续缓冲视频
- v2.8
  - 列表去除相同的源地址
  - 优化了主页的选择界面，现在操作更加高效
  - 优化了详情页面的列表在数据量过多的情况下会出现卡顿的问题
  - 导出的弹框中增加了继续操作的按钮，可以对当前导出的数据进行继续操作处理
  - 增加了新版本的icon
  - 自适应浏览器的明亮/暗黑模式
- v2.7
  - 首页的【我有m3u订阅源链接】，支持多链接，多个链接请用英文的【,】逗号分隔
  - 首页的【我有m3u订阅源链接】以及【我有m3u订阅源内容】新增解析格式为多行的【名称，url】的形式直播源数据，例如

    ```bash
    测试卫视, https://static.zmis.me/test.m3u8
    测试卫视2, https://static.zmis.me/test2.m3u8
    ```
  
  - 首页的【订阅模式】支持选择多个国家/地区的订阅源
- v2.6
  - 修复了筛选输入框输入延迟的BUG
- v2.5
  - 优化了`在线观看`模式的体验
- v2.4
  - 支持`github action`打包，请至`production`分支下载最新公共版本
- v2.3
  - 首页支持`在线观看`模式
- v2.2
  - 支持检查页返回首页
  - 🌟支持在线观看
  - 修复了UI
  - 修复了搜索名称因为大小写问题而搜索不出来的问题
- v2.1
  - 优化了UI
  - 将http的超时设置开放给用户设置
- v2.0
  - 使用react进行开发
  - 优化了老版本检查源数据较慢的问题

## 联系

[知敏博客](https://zmis.me/user/zmisgod)
