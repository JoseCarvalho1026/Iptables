# Iptables

◻️ `sudo su -` ;

◻️ `apt update -y && apt upgrade -y` ;

◻️ `apt install netfilter-persistent iptables-persistent` ; 

◻️ `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE` ;

◻️ `iptables -t nat -L -nv` ;

◻️ `netfilter-persistant save` ;

◻️ `nano /etc/iptables/rules.v4` ;

### HTTP/HTTPS on "www.inova.pt":
```
-A PREROUTING -i eth0 -p tcp -m multiport --dports 80,443 -j DNAT --to-destination 192.168.1.101
```
### FTP on "www.inova.pt":
```
-A PREROUTING -i eth0 -p tcp -m tcp --dport 20 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 21 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 10000:10100 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 990 -j DNAT --to-destination 192.168.1.101
```
### For "marketing.inova.pt" and "sales.inova.pt" to be able to use the Elastic IP of "control.inova.pt":
```
-A PREROUTING -i eth0 -p tcp -m tcp --dport 3389 -j DNAT --to-destination 192.168.2.152
-A PREROUTING -i eth0 -p tcp -m tcp --dport 3390 -j DNAT --to-destination 192.168.2.153:3389
```
### HTTPS on "wazuh.inova.pt" using the IP elastic band of "control.inova.pt":
```
-A PREROUTING -i eth0 -p tcp -m tcp --dport 443 -j DNAT --to-destination 192.168.2.151
-A PREROUTING -i eth0 -p tcp -m tcp --dport 444 -j DNAT --to-destination 192.168.2.151:443
```
◻️ `netfilter-persistent restart` ;

◻️ `netfilter-persistent reload` ;

◻️ `netfilter-persistent save` .
