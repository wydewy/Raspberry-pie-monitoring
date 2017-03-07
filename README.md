# 这是我的毕业设计，树莓派寝室安防监控
## 第一步: 用autossh打通内网控制障碍

树莓派安装autossh,并且生成公钥私钥

```bash
sudo apt-get install autossh
ssh-keygen
ssh-copy-id username@server_ip
```
新建autossh自启动脚本, chmod a+x autossh 并运行, 脚本的内容：
```
#!/bin/bash
/bin/su -c '/usr/bin/autossh -M 1234 -NR 19999:localhost:22 buhuipao@server_ip -p your_port' - pi &
```
复制autossh到/etc/init.d/目录下, 执行:
```
sudo update-rc.d autossh defaults 90
```
这样就可以在自己的服务器上登录你的树莓派了
```
ssh -p 19999 pi@localhost
```
## 第二步：安装必要的软件

## 效果图
#树莓派，小型计算机。有很多外围接口，可以连接网络适配器，连到公网服务器。
![Aaron Swartz](https://github.com/wydewy/Raspberry-pie-monitoring/raw/master/pic/%E6%A0%91%E8%8E%93%E6%B4%BE%E8%BF%9E%E6%8E%A5%E5%AE%9E%E7%89%A9%E5%9B%BE.jpg)
#邮件提醒，使用的是阿里云大于平台。申请免费账号，次数有限制。（用代码自定义邮件格式）
![Aaron Swartz](https://github.com/wydewy/Raspberry-pie-monitoring/raw/master/pic/%E9%82%AE%E4%BB%B6%E6%8F%90%E9%86%92.jpg)
#短信提醒。使用的是mailgun
![Aaron Swartz](https://github.com/wydewy/Raspberry-pie-monitoring/raw/master/pic/%E7%9F%AD%E4%BF%A1%E6%8F%90%E9%86%92.jpg)
