# Moja 远程终端安装脚本
Moja Remote Terminal Setup Script

Link: https://terminal.moja-lab.com/

### 什么是远程终端
如果你：

* 有设备放在家里，要做一系列复杂的内网穿透，把内网暴露在公网环境中才能在外面登录设备
* 有设备放在公司，复杂的网络环境无法做到内网穿透
* 有设备放在用户厂房，无法控制网络条件，每次出问题都要上门服务
* 有大一堆设备，想要批量上传文件、批量执行脚本
* 设备经常无故死机，想要监控 cpu、内存用量

那么远程终端，通过本脚本一键安装后，只要设备可以联上互联网，只要你能找到 Chrome 浏览器，就能随时通过 SSH 登录到设备。

远程终端使用 nodejs 为客户端，兼容所有 Linux 平台，目前已测试通过：
* ✔︎ MacOS
* ✔︎ Raspbian
* ✔︎ Debian
* ✔︎ CentOS
* ✔︎ Ubuntu
* ✔︎ RedHat
* ✔︎ hassbian

目前远程终端尚是 Beta 版，可能有些许问题，大家可以在 Issue 中提问题，我们将竭尽全力改善产品。

### 团队
我们是阿里云 Moja 解决方案实验室团队，针对物联网的应用场景给出落地的解决方案，推动物联网应用的发展。

联系我们：

`邮件：lichen.dlc@alibaba-inc.com`

### 目录结构
* setup.sh 安装脚本
  1. 安装nodejs
  1. 安装pm2
  1. 客户端依赖包安装
  1. pm2 守护进程任务
  1. 日志打包清除任务挂载
  1. 开机自启动任务添加
* deamon 守护程序
  * deamon.sh pm2进程守护脚本 功能：每隔1分钟检测一次客户端代码进程，如果进程不存在就通过pm2 启动
* handleLog 日志打包
  * clearLog.sh 日志清除脚本 功能：每隔一周清除一次 维持7天以内到日志文件数量
  * tarlog.sh  日志打包脚本 功能：每天打包一次日志
* useAge 监控数据采集
  * useAge.sh 监控数据采集脚本 功能：采集内存 cpu 磁盘使用率
