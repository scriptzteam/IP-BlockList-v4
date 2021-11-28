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
Wall of shame (2021-11-28)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.244|10
178.20.55.18|10
45.88.137.253|10
141.98.10.246|10
36.110.228.254|10
80.67.172.162|10
116.110.156.69|10
185.31.175.226|9
185.31.175.220|9
45.153.160.129|9
185.220.102.243|9
185.220.102.248|9
171.25.193.77|9
185.220.101.1|9
221.181.185.111|9
209.141.33.193|9
185.220.100.252|9
212.192.241.37|9
116.105.217.54|9
205.185.115.39|9
171.25.193.20|9
171.25.193.25|9
195.133.18.24|9
185.191.124.143|9
221.131.165.75|9
185.220.102.253|9
209.141.53.74|9
116.110.252.176|9
221.131.165.50|9
209.141.32.141|9
209.141.33.121|9
209.141.34.220|9
185.31.175.207|9
45.153.160.133|9
209.141.47.245|9
209.141.52.25|9
185.31.175.215|9
163.172.213.212|9
107.189.10.137|8
185.31.175.228|8
199.249.230.163|8
23.183.81.249|8
5.183.209.217|8
89.234.157.254|8
89.163.249.192|8
185.220.102.246|8
185.220.102.242|8
185.220.102.249|8
162.247.74.74|8
205.185.122.230|8
141.98.10.63|8
221.131.165.62|8
205.185.114.87|8
5.2.69.50|8
205.185.114.149|8
171.25.193.78|8
23.129.64.217|8
23.183.81.116|8
167.99.45.124|8
45.61.186.123|8
185.220.101.4|8
81.17.18.62|8
167.99.130.6|8
212.192.241.124|8
31.210.20.110|8
161.35.199.104|8
5.2.73.229|8
209.127.17.242|8
159.223.2.20|8
192.160.102.170|8
185.220.100.253|8
185.220.100.254|8
185.31.175.252|8
185.165.168.229|8
192.42.116.16|8
185.220.102.4|8
185.130.44.108|8
38.91.102.36|8
198.144.121.93|8
45.153.160.140|8
23.183.82.135|8
185.243.218.50|8
205.185.120.71|8
185.31.175.235|8
185.31.175.231|8
221.131.165.33|8
162.247.74.217|8
45.153.160.2|8
185.220.102.254|8
64.113.32.29|8
23.154.177.2|8
185.165.171.175|8
164.92.250.114|8
195.133.18.210|8
179.43.187.37|8
164.92.242.15|8
185.56.80.65|8
185.100.87.129|8
104.244.72.120|8
185.129.61.6|8
176.10.99.200|8
45.153.160.134|8
45.88.137.100|8
185.31.175.196|8
185.31.175.247|8
23.183.82.180|8
45.153.160.135|8
45.153.160.139|8
209.141.62.233|8
209.141.62.185|8
23.183.81.227|8
221.10.33.104|8
167.172.43.16|8
185.100.87.202|8
