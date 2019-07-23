#[远程桌面]  

frp使用实例：
##公网服务器端：  
1.下载  
wget https://github.com/fatedier/frp/releases/download/v0.27.1/frp_0.27.1_linux_amd64.tar.gz  
tar -xvf frp_0.27.1_linux_amd64.tar.gz  
mv frp_0.27.1_linux_amd64 frp && cd frp  
2.配置服务端、启动  
vim frps.ini  
'''
[common]
bind_port = 7007
vhost_http_port = 1080

dashboard_port = 7500
// WEB dashboard用户名密码，默认都为 admin
dashboard_user = admin
dashboard_pwd = cls108!@#
'''
./frps -c ./frps.ini  
3.开启防火墙  
ufw allow 7007   
ufw allow 7500  
  
##内网电脑端：   
1.下载  
https://github.com/fatedier/frp/releases/download/v0.27.1/frp_0.27.1_windows_amd64.zip  
解压  
2.配置服务端、启动  
'''
[common]
server_addr = 106.12.145.198
server_port = 7007

[ssh]
type = tcp
local_ip = 127.0.0.1
#本机访问自己会端口占用
local_port = 3389
remote_port = 7005
'''
