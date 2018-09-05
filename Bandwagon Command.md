# Server Command
#### Connect to server
```
ssh -p port root@0.0.0.0
```

# SS Setting

#### Install command
```
$ yum install m2crypto python-setuptools
$ easy_install pip
$ pip install shadowsocks
```

#### Check the config file
```
vi /etc/shadowsocks.json
more /etc/shadowsocks.json
```

#### Config file content
```
{
"server":"0.0.0.0",//IP 
"server_port":8088,//Port
"local_port":1080,//local port
"password":"******",//PSW􏵎 
"timeout":600,//timeout
"method":"aes-256-cfb"//Method
}
```

#### SS Service
create the new shell "/etc/systemd/system/shadowsocks.service"
```
[Unit]
Description=Shadowsocks

[Service]
TimeoutStartSec=0
ExecStart=/usr/bin/ssserver -c /etc/shadowsocks.json

[Install]
WantedBy=multi-user.target
```
#### Start SS Servie 
```
systemctl enable shadowsocks
systemctl start shadowsocks

systemctl status shadowsocks -l
```
The second way to start SS Server directly
```
ssserver -c /etc/shadowsocks.json -d start
ssserver -c /etc/shadowsocks.json -d stop
```

#### mutiple user setting
```
{
"server":"",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
"8000":"123456",
"8001":"123456"
},
"timeout":300,
"method":"aes-256-cfb",
"fast_open":false
}
```

# firewalld

#### Command 
```
systemctl status firewalld.service

systemctl start firewalld.service //Start the firewall

systemctl stop firewalld.service //stop the firewall

systemctl disable firewalld.service //disable firewall start with system
```
```
$ firewall-cmd --query-port=8088/tcp //check the prot status
no
$ firewall-cmd --zone=public --add-port=8089/tcp --permanent //set the port open 
success
$ firewall-cmd --reload 
success
```
$ ps -aux|grep shadowsocks


# SSR Setting
#### Install command
```
apt-get install wget
or
yum -y install wget

wget -N --no-check-certificate https://softs.fun/Bash/ssr.sh && chmod +x ssr.sh && bash ssr.sh
or
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
```

#### Install BBR command
```
wget https://github.com/teddysun/across/archive/master.zip
unzip master.zip
chmod +x ./across-master/bbr.sh
./across-master/bbr.sh
```
重启完成后，进入 VPS,验证一下是否成功安装最新内核并开启 TCP BBR,输入以下命令：
```
uname -r
```
查看内核版本，含有 4.10 就表示 OK 了,最后输入命令,返回值有 tcp_bbr 模块即说明bbr已启动。
```
lsmod | grep bbr
```

