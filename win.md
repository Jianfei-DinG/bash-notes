<!-- ====================================================================== -->
</details>
<hr style="border: none; height: 1px; background-color: green;">
<details>  
<summary>windows</summary> 
> 适用于 windows 
<a name="2"></a>
<hr style="all: unset; display: block; margin: 12px auto; height: 6px; border-top: 1px solid #7ee7878f; width: 100%;">
<!-- ====================================================================== -->

> cmd 定时任务
```
schtasks /create /tn "每日定时重启" /tr "shutdown /r /f /t 0" /sc daily /st 02:00:00 /ru SYSTEM
```
> 查看任务
```
taskschd.msc  
```
设置时间时区
```
tzutil /s "China Standard Time" && w32tm /config /syncfromflags:manual /manualpeerlist:"ntp.aliyun.com" /update && net start w32time && w32tm /resync
```
```
tzutil /s "China Standard Time"
```
关闭自动更新
```
reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /v NoAutoUpdate /t REG_DWORD /d 1 /f && net stop wuauserv
```
<!-- ====================================================================== -->
</details>
<hr style="border: none; height: 1px; background-color: green;">
<details>  
<summary>PowerShell 生成 API Token</summary> 
> 适用于 windows 
<a name="2"></a>
<hr style="all: unset; display: block; margin: 12px auto; height: 6px; border-top: 1px solid #7ee7878f; width: 100%;">
<!-- ====================================================================== -->
>   PowerShell  Hex
  
```
$bytes = New-Object byte[] 32
[System.Security.Cryptography.RandomNumberGenerator]::Create().GetBytes($bytes)
([BitConverter]::ToString($bytes)).Replace("-", "").ToLower()
```
>   示例：
```
25f85499d31bd327e6e3eb59e32d61f3f2d009a90fc9a61c3f68bb6f8bb83808
```

>   URL 转换成 固定值 SHA256（推荐）哈希（Hash）
```
$url = "https://example.com"

$sha256 = [System.Security.Cryptography.SHA256]::Create()
$bytes = [System.Text.Encoding]::UTF8.GetBytes($url)
$hash = $sha256.ComputeHash($bytes)

([BitConverter]::ToString($hash)).Replace("-", "").ToLower()
```

<!-- ====================================================================== -->
</details>
<hr style="border: none; height: 1px; background-color: green;">
<details>  
<summary>网站设计风格</summary> 
> 适用于 风格
<a name="2"></a>
<hr style="all: unset; display: block; margin: 12px auto; height: 6px; border-top: 1px solid #7ee7878f; width: 100%;">
<!-- ====================================================================== -->
开发组合
FastAPI (后端) + Jinja2 (模板) + Tailwind (样式) + Vue (局部交互)
  
科技 SaaS 风格

<!-- ====================================================================== -->
</details>
<hr style="border: none; height: 1px; background-color: green;">
<details>  
<summary>支付宝私钥公钥生成</summary> 
> 适用于 windows
<a name="2"></a>
<hr style="all: unset; display: block; margin: 12px auto; height: 6px; border-top: 1px solid #7ee7878f; width: 100%;">
<!-- ====================================================================== -->
  
> 生成私钥
```
ssh-keygen -t rsa -b 2048 -m PEM -f alipay_private_key -N ""
```
> 导出支付宝专用公钥
```
ssh-keygen -f alipay_private_key -e -m PKCS8 > alipay_public_key.pem
```
> 结果：
```
alipay_private_key         # 私钥
alipay_private_key.pub     # 默认 OpenSSH 公钥格式
alipay_public_key.pem      # PKCS8 格式公钥（上传支付宝）
```
<!-- ====================================================================== -->
</details>
<hr style="border: none; height: 1px; background-color: green;">
<details>  
<summary>windows 驱动备份或恢复 </summary> 
> 适用于 windows 10 11
<a name="2"></a>
<hr style="all: unset; display: block; margin: 12px auto; height: 6px; border-top: 1px solid #7ee7878f; width: 100%;">
<!-- ====================================================================== -->
  
> 以管理员身份打开 CMD：
```
dism /online /export-driver /destination:D:\DriverBackup
```
```
pnputil /export-driver * D:\DriverBackup
```
> 恢复驱动
```
pnputil /add-driver D:\DriverBackup\*.inf /subdirs /install
```
<!-- ====================================================================== -->
</details>
