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
Wall of shame (2021-12-01)
----

|IP|Number of (black)lists|
|---|--:|
185.31.175.220|10
171.25.193.77|10
45.88.137.253|10
171.25.193.20|10
185.191.124.143|10
185.220.102.250|10
80.67.172.162|10
185.31.175.215|10
163.172.213.212|10
185.31.175.226|9
136.144.41.139|9
107.189.11.153|9
23.183.81.249|9
89.234.157.254|9
205.185.115.39|9
45.144.225.119|9
185.220.102.244|9
141.98.10.63|9
136.144.41.3|9
171.25.193.78|9
185.220.101.1|9
185.220.100.252|9
185.220.100.254|9
205.185.114.87|9
185.31.175.252|9
222.187.238.58|9
205.185.120.71|9
171.25.193.25|9
209.141.33.121|9
221.131.165.75|9
2.56.59.114|9
64.113.32.29|9
221.131.165.50|9
195.133.18.210|9
209.141.32.141|9
221.181.185.111|9
116.110.156.69|9
23.183.81.227|9
45.153.160.2|9
128.31.0.13|8
5.183.209.217|8
167.99.38.54|8
185.107.47.215|8
185.220.102.249|8
162.247.74.74|8
205.185.114.149|8
23.183.81.136|8
178.20.55.18|8
212.192.241.124|8
104.244.78.183|8
209.141.33.193|8
192.160.102.170|8
54.36.108.162|8
176.10.99.200|8
94.230.208.147|8
192.42.116.16|8
166.70.207.2|8
185.220.102.4|8
185.130.44.108|8
198.144.121.93|8
45.153.160.140|8
212.192.241.37|8
185.31.175.213|8
23.183.82.135|8
141.98.10.246|8
107.189.30.85|8
23.183.82.117|8
221.131.165.33|8
195.133.18.24|8
185.220.102.253|8
185.220.102.252|8
104.244.73.169|8
116.110.252.176|8
164.92.250.114|8
179.43.187.37|8
209.141.34.220|8
89.163.252.30|8
185.129.61.1|8
167.99.39.128|8
23.183.81.54|8
45.153.160.133|8
45.153.160.132|8
45.153.160.131|8
45.153.160.139|8
185.220.100.240|8
185.220.100.249|8
45.88.137.100|8
209.141.47.245|8
23.183.82.180|8
209.141.52.25|8
209.141.62.185|8
221.10.33.104|8
167.172.43.16|8
209.141.53.74|8
107.189.8.65|8
