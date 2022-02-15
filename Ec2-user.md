# Iptables

◻️ `sudo su -` ;

◻️ `yum update -y` ;

◻️ `yum install iptables-services` ; 

◻️ `systemctl enable --now iptables` ;

◻️ `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE` ;

◻️ `iptables -t nat -L -nv` ;

◻️ `iptables -F` ;

◻️ `nano /etc/sysconfig/iptables` ;

### HTTP/HTTPS on "www.enta.pt":
```
-A PREROUTING -i eth0 -p tcp -m multiport --dports 80,443 -j DNAT --to-destination 172.31.1.101
```
### FTP on "www.enta.pt":
```
-A PREROUTING -i eth0 -p tcp -m tcp --dport 20 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 21 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 10000:10100 -j DNAT --to-destination 192.168.1.101
-A PREROUTING -i eth0 -p tcp -m tcp --dport 990 -j DNAT --to-destination 192.168.1.101
```

◻️ `service iptables restart` ;

◻️ `service iptables reload` ;

◻️ `service iptables save` ;
