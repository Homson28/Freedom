======<Command>======

ssh -p port root@0.0.0.0


==SS Config==

$ yum install m2crypto python-setuptools
$ easy_install pip 
$ pip install shadowsocks


vi /etc/shadowsocks.json
more /etc/shadowsocks.json

{
"server":"0.0.0.0",//IP 
"server_port":8088,//Port
"local_port":1080,//local port
"password":"******",//PSW􏵎 
"timeout":600,//timeout
"method":"aes-256-cfb"//Method
}


//Start SS server
ssserver -c /etc/shadowsocks.json -d start
ssserver -c /etc/shadowsocks.json -d stop

systemctl status shadowsocks -l


//mutiple user setting
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


==firewalld==

systemctl status firewalld.service

systemctl start firewalld.service //Start the firewall

systemctl stop firewalld.service //stop the firewall

systemctl disable firewalld.service //disable firewall start with system


$ firewall-cmd --query-port=8088/tcp //check the prot status
no
$ firewall-cmd --zone=public --add-port=8089/tcp --permanent //set the port open 
success

$ firewall-cmd --reload 
success

$ ps -aux|grep shadowsocks

