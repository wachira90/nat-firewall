# nat-firewall
nat firewall

## allow forward package 

````
nano /etc/sysctl.conf 

net.ipv4.ip_forward = 1

echo 1 > /proc/sys/net/ipv4/ip_forward
````

## check command and reboot

````
cat /proc/sys/net/ipv4/ip_forward
````

## POSTROUTING MASQUERADE

````
iptables -t nat -A POSTROUTING -s 192.168.11.0/24 -o eth0 -j MASQUERADE
````

## exaplain

````
iptables -t nat -A POSTROUTING -s <วงIPภายใน>/24 -o <LAN ขาออก> -j MASQUERADE
````

## clear firewall

````
/sbin/iptables -F
/sbin/iptables -t nat -F
/sbin/iptables -X
````

## check nat command

````
iptables -t nat -L -n -v
````


