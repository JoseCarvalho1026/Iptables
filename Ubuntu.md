# Iptables

◻️ `sudo su -` ;

◻️ `apt update -y && apt upgrade -y` ;

◻️ `apt install netfilter-persistent iptables-persistent` ; 

◻️ `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE` ;

◻️ `iptables -t nat -L -nv` ;

◻️ `netfilter-persistant save` ;

◻️ `nano /etc/iptables/rules.v4` ;

### HTTP/HTTPS no "www.inova.pt":
```
-A PREROUTING -i eth0 -p tcp -m multiport --dports 80,443 -j DNAT --to-destination 192.168.1.101
```
### FTP no "www.inova.pt":
```
-A PREROUTING -i eth0 -p tcp -m tcp --dport 20 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 21 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 10000:10100 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 990 -j DNAT --to-destination 192.168.1.101
```
### Para o "marketing.inova.pt" e o "sales.inova.pt" conseguirem usar o IP Elastic do "control.inova.pt":
```
-A PREROUTING -i eth0 -p tcp -m tcp --dport 3389 -j DNAT --to-destination 192.168.2.152
-A PREROUTING -i eth0 -p tcp -m tcp --dport 3390 -j DNAT --to-destination 192.168.2.153:3389
```
