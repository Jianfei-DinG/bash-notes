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
