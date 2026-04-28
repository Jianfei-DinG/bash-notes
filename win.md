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
