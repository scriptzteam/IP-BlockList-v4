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
Wall of shame (2021-10-28)
----

|IP|Number of (black)lists|
|---|--:|
5.183.209.217|9
185.220.102.249|9
162.247.74.74|9
45.153.160.2|9
185.100.87.72|9
45.153.160.140|9
185.31.175.231|9
171.25.193.25|9
185.38.175.132|9
213.202.216.189|9
80.67.172.162|9
185.56.80.65|9
45.153.160.133|9
45.153.160.132|9
185.220.100.242|9
185.31.175.240|9
185.31.175.226|8
185.31.175.220|8
162.247.74.204|8
185.31.175.228|8
89.163.249.244|8
185.107.47.215|8
104.244.77.37|8
185.220.102.240|8
185.220.102.248|8
141.98.10.60|8
116.105.30.143|8
185.107.47.171|8
18.27.197.252|8
185.220.101.40|8
54.36.108.162|8
185.220.100.253|8
185.220.100.254|8
192.42.116.17|8
198.144.121.93|8
45.135.232.159|8
185.220.103.7|8
162.247.74.217|8
185.73.124.253|8
171.25.193.20|8
185.220.102.251|8
185.220.102.250|8
64.113.32.29|8
104.244.76.13|8
205.185.120.183|8
185.247.225.43|8
209.127.17.234|8
45.153.160.131|8
45.153.160.136|8
45.153.160.138|8
185.220.100.240|8
199.195.253.210|8
141.98.10.81|8
141.98.10.82|8
163.172.213.212|8
