
<hr style="border: none; height: 1px; background-color: green;">
<details>  
<summary>debian 基础设置</summary> 
> 适用于 esxi 
<a name="22"></a>
<hr style="all: unset; display: block; margin: 12px auto; height: 6px; border-top: 1px solid #7ee7878f; width: 100%;">
<!-- ====================================================================== -->

> 更新系统
```
sudo apt update && sudo apt upgrade -y
```

> 一键结束端口进程
```
sudo kill -9 $(lsof -t -i :31375)
```

> 文件指纹
```
md5sum frps.log 		#文件内容指纹
sha256sum frps.log 		#文件内容指纹
stat frps.log 			#文件元信息
```

> 文件属性
```
lsattr  | 查看文件属性
chattr | 添加文件属性

   a：让文件或目录仅供附加用途。
   b：不更新文件或目录的最后存取时间。
   c：将文件或目录压缩后存放。
   d：将文件或目录排除在倾倒操作之外。
   i：不得任意更动文件或目录。
   s：保密性删除文件或目录。
   S：即时更新文件或目录。
   u：预防意外删除。
```

> 示例
```
root@VM-20-13-ubuntu:/etc/haproxy# chattr +i 13.gg 
root@VM-20-13-ubuntu:/etc/haproxy# lsattr 
----i---------e----- ./13.gg
```

> ssh 远程访问设置
```
UseDNS no
AddressFamily inet
SyslogFacility AUTHPRIV

PubkeyAuthentication yes
PasswordAuthentication no
PermitRootLogin prohibit-password
```

> 一键全部改（推荐）
```
#!/bin/bash

set -e

CFG="/etc/ssh/sshd_config"

cp $CFG ${CFG}.bak

sed -i 's/^#*UseDNS.*/UseDNS no/' $CFG || echo "UseDNS no" >> $CFG
sed -i 's/^#*AddressFamily.*/AddressFamily inet/' $CFG || echo "AddressFamily inet" >> $CFG
sed -i 's/^#*SyslogFacility.*/SyslogFacility AUTHPRIV/' $CFG || echo "SyslogFacility AUTHPRIV" >> $CFG

sed -i 's/^#*PubkeyAuthentication.*/PubkeyAuthentication yes/' $CFG || echo "PubkeyAuthentication yes" >> $CFG
sed -i 's/^#*PasswordAuthentication.*/PasswordAuthentication no/' $CFG || echo "PasswordAuthentication no" >> $CFG
sed -i 's/^#*PermitRootLogin.*/PermitRootLogin prohibit-password/' $CFG || echo "PermitRootLogin prohibit-password" >> $CFG

sshd -t && systemctl restart sshd

echo "SSH hardened successfully"
```

> 时区语言设置

手动修改（直接改配置文件）
```
sudo nano /etc/default/locale          # 手动编辑语言/编码设置
sudo timedatectl set-timezone Asia/Shanghai   # 直接设置时区
```

```
# 生成语言包
sudo locale-gen en_US.UTF-8
sudo locale-gen zh_CN.UTF-8

# 写入配置文件
sudo tee /etc/default/locale <<EOF
LANG=en_US.UTF-8
LC_ALL=en_US.UTF-8
EOF

# 当前会话生效
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8

# 验证
locale
```

图形化/交互式设置（菜单界面）
```
sudo dpkg-reconfigure tzdata           # 弹出菜单选城市（Asia -> Shanghai）
sudo dpkg-reconfigure locales          # 弹出菜单勾选语言包（空格键选择）选择 en_US.UTF-8 UTF-8
sudo update-locale LANG=zh_CN.UTF-8    # 设置系统默认语言
sudo update-locale LANG=en_US.UTF-8    # 设置系统默认语言

locale
```
<!-- ====================================================================== -->
</details>