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
162.247.74.74|10
141.98.10.60|10
141.98.10.81|10
141.98.10.82|10
89.234.157.254|9
185.220.102.240|9
171.25.193.78|9
209.141.60.103|9
167.88.161.219|9
205.185.126.71|9
185.100.87.72|9
179.43.175.26|9
185.73.124.253|9
171.25.193.20|9
171.25.193.25|9
212.193.30.101|9
80.67.172.162|9
209.141.55.232|9
205.185.120.183|9
185.129.62.62|9
45.153.160.133|9
199.195.253.210|9
139.59.144.149|9
159.223.24.19|9
68.183.180.46|9
163.172.213.212|9
185.100.87.202|9
199.195.248.175|8
165.22.100.49|8
185.31.175.228|8
185.107.47.215|8
89.163.249.192|8
104.244.77.37|8
185.220.102.244|8
198.98.54.17|8
141.98.10.63|8
221.131.165.62|8
5.2.69.50|8
116.105.30.143|8
171.25.193.77|8
185.107.47.171|8
185.220.101.4|8
18.27.197.252|8
185.220.101.40|8
180.76.137.231|8
212.193.30.32|8
221.181.185.111|8
185.220.100.252|8
185.220.100.255|8
89.163.249.244|8
141.98.10.121|8
136.144.41.253|8
185.165.168.229|8
185.220.101.12|8
45.153.160.140|8
162.247.74.27|8
117.68.2.93|8
162.247.74.217|8
209.141.40.64|8
209.141.33.121|8
209.141.59.77|8
185.38.175.132|8
213.202.216.189|8
8.209.91.186|8
64.113.32.29|8
221.131.165.50|8
209.141.59.9|8
104.244.76.13|8
185.56.80.65|8
185.247.225.43|8
45.153.160.138|8
45.153.160.132|8
45.153.160.131|8
45.153.160.137|8
185.220.100.240|8
209.141.49.147|8
45.153.160.136|8
185.220.101.16|8
107.189.30.134|8
