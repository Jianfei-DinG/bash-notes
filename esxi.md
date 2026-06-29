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
远程定时关机

```
0 2 * * * /usr/bin/ssh -T -o StrictHostKeyChecking=no root@192.168.1.4 "/bin/vim-cmd vmsvc/power.shutdown 11 || /bin/vim-cmd vmsvc/power.off 11" >> /tmp/vm_shutdown.log 2>&1
```
```
sudo apt update && sudo apt install sshpass
```
```
0 2 * * * /usr/bin/sshpass -p '' ssh -o StrictHostKeyChecking=no root@192.168.1.4 "vim-cmd vmsvc/power.shutdown 11 || vim-cmd vmsvc/power.off 11" >> /tmp/vm_shutdown.log 2>&1
```
```
sshpass -p '' ssh -o StrictHostKeyChecking=no root@192.168.1.4 "vim-cmd vmsvc/power.getstate 11"
```
虚拟机管理（核心）
```
# 查看所有虚拟机
vim-cmd vmsvc/getallvms

# 查看虚拟机状态
vim-cmd vmsvc/power.getstate <VMID>

# 开机
vim-cmd vmsvc/power.on <VMID>

# 关机（正常）
vim-cmd vmsvc/power.shutdown <VMID>

# 强制关机
vim-cmd vmsvc/power.off <VMID>

# 重启
vim-cmd vmsvc/power.reboot <VMID>

# 查看虚拟机详细信息
vim-cmd vmsvc/get.summary <VMID>

esxcli system hostname set --host=TianYun

esxcli vm process list
esxcli network nic list
esxtop
```
主机信息
```
# 查看 ESXi 版本
vmware -v

# 查看硬件平台信息
esxcli hardware platform get

# 查看 CPU 信息
esxcli hardware cpu list

# 查看内存信息
esxcli hardware memory get
```
SSH 管理
```
# 开启 SSH
vim-cmd hostsvc/enable_ssh

# 启动 SSH
vim-cmd hostsvc/start_ssh

# 停止 SSH
vim-cmd hostsvc/stop_ssh

#保持 SSH 运行
vim-cmd hostsvc/enable_ssh

#启动 SSH 服务
/etc/init.d/SSH start

#验证 SSH 是否开启
/etc/init.d/SSH status	
```
