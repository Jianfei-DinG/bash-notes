<img src="https://cdn.jsdmirror.com/gh/Jianfei-DinG/bash-notes/img/ufw.webp" width="%100" height="auto" align="center" style="border-radius: 10px;" />
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
先写 DENY（黑名单）
再写 ALLOW（白名单）

ufw insert 1 deny 9321  #插入最前面
ufw allow 22
ufw allow 80
ufw allow 443
ufw allow 7000
```
查看放行配置
```
ufw show added 
cat /etc/ufw/user.rules
```
```
开关防火墙
ufw enable   # 开启
ufw disable  # 关闭

把“入站流量”的默认规则改成：允许（allow）
ufw default allow incoming
ufw status verbose

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
