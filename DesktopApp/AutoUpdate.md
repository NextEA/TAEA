# 需求目标
本节定义了客户端应用程序自动更新的一些常见的目标和需求。 在不同的场景下，对自动更新的需求和目标会有所不同，甚至在不同场景下或出现完全相反的需求，比如有些场景下要求客户端必须全部更新到最新版本后才允许用户使用，而有些场景下要求客户先进入应用开展工作，当使用到需要更新的模块时在更新该模块。

以下，从不同用户的角度来分析对自动更新的需求和目标：

## 运维角度
* **提前预热**：在版本生效前将版本包推送到客户端，避免版本生效时终端同时下载对服务器和带宽照成的压力；
* **错峰下载**：在提前预热的基础上，可以控制终端分批次下载版本包，控制下载节奏，避免提前预热时并发下载产生的服务器和带宽压力；
* **流量控制**：控制服务端的并发数，拒绝处理超出服务器处理能力的请求，保证服务端高速处理链接上来的请求，尽快完成任务；
* **终端管理**：在服务端可以查看终端的状态，如：终端硬/软件信息，系统版本情况，更新下载状态等；
* **版本回退**：支持在新版本生效后，回退到之前版本的功能；
* **灰度发布**：可以选择部分终端先行应用更新，进行小范围生产环境的测试，在经过小范围测试后，在大面积推广更新

## 用户角度
* **无人干预**：客户端自动下载/应用更新，其过程不需要人为干预
* **版本正确**：客户端需要保证全部DLL版本正确（包括DLL防篡改）
* **闲时下载**：在预推阶段，客户端下载更新包不应该影响正常的业务通讯
* **按需下载**：仅下载安装的插件版本包
* **增量下载**：客户端应只下载更新的DLL，没有变化的DLL应无需下载

# 需要解决的问题
## 程序的自我更新
### ClickOnce
* 优势：
  - .Net Framework自带机制，稳定，简单
  - 初始安装方便，用户点击网页链接即可
  - 其他网页应用启动方便
* 劣势：
  - 安装在User目录下，如是多用户公用一台计算机，不同用户需要独立安装，独立更新版本
  - 程序权限受限，如需提权，需要客户端进行配置
  - 无法有效避免非法的下载
  - 在程序版本升级时，文件移动到不同的目录，如果客户端有大量缓存文件，会花费较长时间
### A/B 程序
* 优势：
  - 程序访问本地资源不受限
  - 安装目录不受限
* 劣势：
  - 需要用户手动安装
  - 其他网页启动程序困难，需要配置客户端注册表
### Service
* 优势：
  - 程序访问本地资源不受限
  - 安装目录不受限
  - 下载进程同系统交互界面进程隔离，互不影响
* 劣势：
  - 需要用户手动安装
  - 其他网页启动程序困难，需要配置客户端注册表
### Restart Manager
* 优势
* 劣势
# Design

# Reference
* http://www.devx.com/dotnet/Article/10045 --- Automatically Upgrade Your .NET Applications On-the-Fly
* http://msdn.microsoft.com/en-us/magazine/cc188766.aspx --- Write Auto-Updating Apps with .NET and the Background Intelligent Transfer Service API
* https://github.com/Squirrel/Squirrel.Windows 
* https://github.com/synhershko/NAppUpdate --- synhershko  / NAppUpdate 
* http://www.codeproject.com/Articles/700435/Windows-service-auto-update-plugin-framework
* https://github.com/LogosBible/bsdiff.net
* http://community.bartdesmet.net/blogs/bart/archive/2006/11/12/Exploring-Windows-Vista_2700_s-Restart-Manager-in-C_2300_.aspx
* http://www.codeproject.com/Articles/772868/Restart-Manager-Support-For-Windows-Application
* https://autoupdaterdotnet.codeplex.com/
* http://sharpbits.codeplex.com/
* http://www.cnblogs.com/superch0054/archive/2004/10/22/4010244.html
* https://msdn.microsoft.com/en-us/library/bb968799(v=vs.85).aspx --- Background Intelligent Transfer Service 
* http://www.cnblogs.com/zhuweisky/p/5085099.html --- 自动升级系统的设计与实现（续2） -- 增加断点续传功能 （附最新源码） 
* http://www.cnblogs.com/JamesLi2015/p/4749476.html --- 解析大型.NET ERP系统 自动更新 
* https://technet.microsoft.com/en-us/library/hh831696.aspx#Operating --- system versions for BranchCache
