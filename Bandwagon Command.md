======<Command>======
<br/>
<br/>ssh -p port root@0.0.0.0
<br/>
<br/>
==SS Config==
<br/>
<br/>$ yum install m2crypto python-setuptools
<br/>$ easy_install pip
<br/>$ pip install shadowsocks
<br/>
<br/>
<br/>vi /etc/shadowsocks.json
<br/>more /etc/shadowsocks.json
<br/>
<br/>{
<br/>"server":"0.0.0.0",//IP 
<br/>"server_port":8088,//Port
<br/>"local_port":1080,//local port
<br/>"password":"******",//PSW􏵎 
<br/>"timeout":600,//timeout
<br/>"method":"aes-256-cfb"//Method
<br/>}
<br/>
<br/>
<br/>//Start SS server
<br/>ssserver -c /etc/shadowsocks.json -d start
<br/>ssserver -c /etc/shadowsocks.json -d stop
<br/>
<br/>systemctl status shadowsocks -l
<br/>
<br/>
<br/>//mutiple user setting
<br/>{
<br/>"server":"",
<br/>"local_address":"127.0.0.1",
<br/>"local_port":1080,
<br/>"port_password":{
<br/>"8000":"123456",
<br/>"8001":"123456"
<br/>},
<br/>"timeout":300,
<br/>"method":"aes-256-cfb",
<br/>"fast_open":false
<br/>}
<br/>
<br/>
<br/>==firewalld==
<br/>
<br/>systemctl status firewalld.service
<br/>
<br/>systemctl start firewalld.service //Start the firewall
<br/>
<br/>systemctl stop firewalld.service //stop the firewall
<br/>
<br/>systemctl disable firewalld.service //disable firewall start with system
<br/>
<br/>
<br/>$ firewall-cmd --query-port=8088/tcp //check the prot status
<br/>no
<br/>$ firewall-cmd --zone=public --add-port=8089/tcp --permanent //set the port open 
<br/>success
<br/>$ firewall-cmd --reload 
<br/>success
<br/>
<br/>$ ps -aux|grep shadowsocks
<br/>
<br/>
<br/>
==SSR Config==
<br/>
<br/>apt-get install wget
<br/>or
<br/>yum -y install wget
<br/>
<br/>wget -N --no-check-certificate https://softs.fun/Bash/ssr.sh && chmod +x ssr.sh && bash ssr.sh
<br/>or
<br/>wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
<br/>
<br/>
