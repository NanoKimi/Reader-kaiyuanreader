# Reader
A win32 txt/epub/online file reader  

最新release版本：　`v2.1.0.0`（本仓库为 fork：NanoKimi/Reader-kaiyuanreader）
版本描述  | 下载地址
------------- | -------------
正式版x64  | [Reader_v2.1.0.0_x64.7z](https://github.com/NanoKimi/Reader-kaiyuanreader/releases/download/v2.1.0.0/Reader_v2.1.0.0_x64.7z)
正式版win32  | [Reader_v2.1.0.0.7z](https://github.com/NanoKimi/Reader-kaiyuanreader/releases/download/v2.1.0.0/Reader_v2.1.0.0.7z)
<br/> 
<br/> 
原作者介绍：
```
Reader 是我个人开发的一款绿色、开源、免费的阅读器软件，主要用于小说阅读。  
为广大网络文学爱好者提供一种方便、快捷舒适的阅读体验。  
同时为广大软件开发者、爱好者提供学习参考。所有版权归作者所有。  
一直以来感谢大家对Reader的喜爱与支持，同时也感谢大家对Reader的推广与宣传。  
本软件虽然简单，但也花费了我不少时间和精力。
1. 如果需要分享或者推广，请注明软件出处。  
2. 本软件严禁用于非法用途。  
3. 本软件严禁用于商业用途,如有违反保留追究法律责任的权力。
```
<br/>
<br/>
<br/>
原作者仓库：
https://github.com/binbyu/Reader

以下是本人的功能更新
## v2.1.0.0 2026/09/10 功能更新  
1. 新增「Web 阅读」：连接局域网里手机端 legado(开源阅读) 的 web 服务，直接在电脑上读手机书架里的书，并与手机双向同步进度  
   1.1 菜单：设置 → Web 阅读；填入 web 服务地址（例如 http://192.168.1.100:1122）后点「连接」列出书架  
   1.2 网络书源的书和**手机本地书**都能读，列表带「来源」列区分；手机本地书正文由手机端解析后传回  
   1.3 输入关键词即时筛选（空格分词、全部命中），回车直接打开第一本；点「清空」看全部  
   1.4 打开书时按手机上的进度续读；电脑上翻页/切章后自动回写手机（本地立即记录，手机端 5 秒节流并补推）  
   1.5 回写字段与手机网页版一致，手机端 legado 的书架进度会同步更新，手机上接着读同一位置  
   1.6 详细说明见 [doc/web-read.md](doc/web-read.md)  
3. 应用内「检查更新」改为读取本仓库(fork)的 version.json，而不是原作者仓库  
   3.1 以后在本仓库改版本号、更新 version.json 即可，软件会按 12 小时一次自动检查并提示新版本  
   3.2 原作者仓库的其它链接（关于页面、书源文档、书源 bs.json）保持指向上游，便于继续获取书源更新  
2. 修复在新版 Visual Studio / Windows 上无法编译的问题  
   2.1 源码是 UTF-8 无 BOM 且含中文注释，工程加 /source-charset:utf-8（否则中文代码页下注释会吞掉换行，  
       导致 MobiBook.h 里 mobi_t 的成员声明被注释掉，报 71 个错误）；DisplaySet.cpp 由 GBK 转为 UTF-8  
   2.2 新增 zlib_cdecl_bridge.c：libmobi.lib 需要 cdecl 的 crc32/uncompress，而自带 zlibstat.lib 只导出  
       ZLIB_WINAPI 的 stdcall 版本，链接必然失败  
   2.3 忽略 libmobi.lib 携带的 /DEFAULTLIB:MSVCRT，避免与工程的 /MT 冲突  
   2.4 新增 build-local.bat：自动定位 VS/SDK 并重定向工具集，用 PowerShell 取版本号（替代 Windows 11  
       已移除的 wmic），7z 不可用时回退 zip  

