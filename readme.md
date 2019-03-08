# 根据 [Aria2 Manual](https://aria2.github.io/manual/en/html/) 汉化大部分的配置文件  

[汉化的配置文件](https://github.com/lilyvya/aria2-conf/blob/master/aria2.conf)  
**请勿直接使用此配置文件，至少需要更改** `rpc-secret=` **的值**  

Windows 要运行还需要 [Aria2c.exe](https://github.com/aria2/aria2/releases) ，建议和 [webui-aria2](https://github.com/ziahamza/webui-aria2) 搭配使用，或者 [AriaNg](https://github.com/mayswind/AriaNg) , [yaaw](https://github.com/binux/yaaw)  


### Chrome 扩展
[Linkle](https://chrome.google.com/webstore/detail/linkle/okcgleaeeoddghoiabpapmnkckncbjba?hl=zh-CN)  
[Aria2c Integration](https://chrome.google.com/webstore/detail/aria2c-integration/cnkefpcjiolhnmhfpjbjpidgncnajlmf?hl=zh-CN)  
[Camtd](https://chrome.google.com/webstore/detail/camtd-aria2-download-mana/lcfobgbcebdnnppciffalfndpdfeence/related?utm_source=chrome-ntp-icon)（使用这个扩展不需要 webui-aria2 或 AriaNg ）  
[Aria2 for Chrome](https://chrome.google.com/webstore/detail/aria2-for-chrome/mpkodccbngfoacfalldjimigbofkhgjn)（使用这个扩展不需要 webui-aria2 或 AriaNg ）  

## Windows 的启动方式和 Firefox FlashGot 调用  

### Windows  
Windows CMD 启动双击 start.bat ，后台运行双击 HideRun.vbs ，关闭双击 stop.bat

如需开机自启动，将 HideRun.vbs 创建快捷方式，将快捷方式放至Startup文件夹

> Startup 路径：%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup

### Firefox 57 以前 FlashGot 的调用方式  
需要 [Python2](https://www.python.org/downloads/windows/) 环境  
以 Windows 为例  

* 新增一个下载管理  
* 如果你的系统环境不对：  
  * 可执行路径：`PATH\Python2\pythonw.exe`  
  * 参数模板：`PATH\Aria2\run.pyw --secret <SECRET> --dir PATH [--cookie COOKIE] [--referer REFERER] [--user-agent UA] [URL]`  
* 如果系统环境正确：  
  * 可执行路径：`PATH\Aria2\run.pyw`  
  * 参数模板： `--secret <SECRET> --dir PATH [--cookie COOKIE] [--referer REFERER] [--user-agent UA] [URL]`  
* 参数模板 `--secret <SECRET>` 里的 `<SECRET>` 替换为 `aria2.conf` 里的 `rpc-secret=` 后面的值  
* 如果需要局域网或互联网使用，在参数模板里加上`--rpc http://127.0.0.1:6800/jsonrpc` ，127.0.0.1:6800 替换为你需要的 IP/域名和端口  
* 如果文件名不正确可以加上 `[--output FNAME]` ，加上之后可能会导致文件无法下载  
* 如果百度账号在百度云限速黑名单里则去掉 `[--cookie COOKIE]`  

Firefox Quantum （57以后的版本）参照 Chome
