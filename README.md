![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IP-BlockList-v4** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/scriptzteam/IP-BlockList-v4/master/ips.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ips
ipset -q create ips hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/scriptzteam/IP-BlockList-v4/master/ips.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ips $ip; done
iptables -I INPUT -m set --match-set ips src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).
Wall of shame (2021-10-27)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.25|10
162.247.74.74|9
185.73.124.253|9
171.25.193.20|9
80.67.172.162|9
64.113.32.29|9
185.56.80.65|9
205.185.120.183|9
141.98.10.82|9
199.195.248.175|8
162.247.74.204|8
165.22.100.49|8
5.183.209.217|8
89.234.157.254|8
185.107.47.215|8
185.220.102.249|8
141.98.10.60|8
171.25.193.77|8
171.25.193.78|8
185.107.47.171|8
45.153.160.2|8
62.210.37.82|8
54.36.108.162|8
185.220.100.253|8
185.220.100.254|8
205.185.126.71|8
185.100.87.72|8
185.165.168.229|8
192.42.116.16|8
185.220.101.12|8
185.220.102.4|8
198.144.121.93|8
45.153.160.140|8
185.31.175.231|8
176.10.99.200|8
209.141.33.121|8
212.193.30.101|8
213.202.216.189|8
209.141.55.232|8
209.141.59.9|8
104.244.76.13|8
209.127.17.234|8
185.129.62.62|8
45.153.160.133|8
45.153.160.132|8
185.220.100.242|8
185.220.100.240|8
199.195.253.210|8
141.98.10.81|8
209.141.59.184|8
159.223.24.19|8
163.172.213.212|8
