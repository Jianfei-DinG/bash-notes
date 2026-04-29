<!-- ====================================================================== -->
</details>
<hr style="border: none; height: 1px; background-color: green;">
<details>  
<summary>esxi 命令</summary> 
> 适用于 esxi 
<a name="22"></a>
<hr style="all: unset; display: block; margin: 12px auto; height: 6px; border-top: 1px solid #7ee7878f; width: 100%;">
<!-- ====================================================================== -->

```
vim-cmd vmsvc/getallvms 				#查看所有虚拟机
vim-cmd vmsvc/power.on 1  				#开机
vim-cmd vmsvc/power.shutdown <vmid> 	#关机（优雅）
vim-cmd vmsvc/power.off <vmid> 			#强制关机
vim-cmd vmsvc/power.reboot <vmid> 		#重启
vim-cmd vmsvc/power.getstate <vmid>  	#查看虚拟机状态 
```