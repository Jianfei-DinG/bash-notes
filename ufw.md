
<!-- ====================================================================== -->
</details>
<hr style="border: none; height: 1px; background-color: green;">
<details>  
<summary>ufw防火墙 使用</summary> 
> 适用于 Debian / Ubuntu 
<a name="2"></a>
<hr style="all: unset; display: block; margin: 12px auto; height: 6px; border-top: 1px solid #7ee7878f; width: 100%;">
<!-- ====================================================================== -->


```
apt update && apt install ufw -y
```
```
ufw --version
ufw status verbose
一定先放行
```
```
ufw allow 22
ufw allow 80
ufw allow 443
ufw allow 7000
```
查看放行配置
```
ufw show added 
cat /etc/ufw/user.rules

开关防火墙
ufw enable   # 开启
ufw disable  # 关闭

禁止外网所有 IP 访问 8321
ufw deny 8321/tcp

查看所有规则（确认成功）
ufw status numbered

删除规则
ufw delete 编号
# 或者直接删除规则
ufw delete deny 8321/tcp

全部重置清空
ufw reset

禁止 8000–8010 所有 TCP 端口
ufw deny 8000:8010/tcp

放行 9000–9005
ufw allow 9000:9005/tcp
```
