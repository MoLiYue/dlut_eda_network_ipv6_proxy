# 初步建成ipv6 proxy

[ipv6 proxy教学](https://www.youtube.com/watch?v=Txfh0a4YqzQ&t=32s)

[学长图文教程](https://buuubuuu.notion.site/ipv6-VPS-a626565bac9e47ddb1980a4c81fbf988)

## 树梅派做服务器

我们使用树梅派在教学区充当ipv6 proxy服务器使用。

首先在树梅派上通过[rpi image](https://www.raspberrypi.com/software/)刷好树梅派专用的ubuntu server。

刷好系统后可以先在pc上把镜像源换了。目录在 `/etc/apt/sources.list` 。

镜像源我选择[清华源](https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu-ports/)直接替换原来的就行。

接下来将树梅派连接好并开机，第一次接入我考虑使用外接显示器。熟悉ubuntu的同学也可以事先将ip地址写好等直接远程登陆。

在ubuntu server中先更新apt `sudo apt update` `sudo apt upgrade` 。

更新后需要部署科学上网。

科学上网建议使用v2raya（推荐）或clash（比较复杂不推荐）。

v2raya的安装与使用详见[使用手册](https://v2raya.org/docs/prologue/installation/debian/)

使用时需要的命令我简单总结如下

```
curl -Ls https://mirrors.v2raya.org/go.sh | sudo bash

sudo systemctl disable v2ray --now ### Xray 需要替换服务为 xray

wget -qO - https://apt.v2raya.mzz.pub/key/public-key.asc | sudo apt-key add -

echo "deb https://apt.v2raya.mzz.pub/ v2raya main" | sudo tee /etc/apt/sources.list.d/v2raya.list
sudo apt update

sudo apt install v2raya
```