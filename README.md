# Captive Wifi on Raspberry

## Captive Portal

sudo nano /etc/dnsmasq.conf

```
address=/#/172.24.1.1
```

sudo nano /etc/resolve.conf

```
nameserver 127.0.0.1
```

sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 172.24.1.1:80
sudo iptables -t nat -A PREROUTING -p tcp --dport 443 -j DNAT --to-destination 172.24.1.1:443
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
