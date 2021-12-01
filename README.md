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
221.181.185.111|10
185.31.175.220|9
141.98.10.246|9
116.105.217.54|9
222.187.238.58|9
221.131.165.75|9
209.141.62.233|9
221.131.165.50|9
212.192.241.37|9
163.172.213.212|9
185.31.175.215|9
23.183.82.135|9
209.141.34.220|9
185.31.175.226|8
80.82.77.33|8
205.185.120.71|8
36.110.228.254|8
45.153.160.133|8
221.131.165.33|8
23.183.81.54|8
212.192.241.124|8
222.186.42.13|8
45.153.160.129|8
185.220.100.252|8
171.25.193.20|8
205.185.115.39|8
205.185.114.87|8
209.141.33.121|8
23.183.82.180|8
45.144.225.119|8
185.220.102.244|8
185.220.102.248|8
116.110.156.69|8
185.31.175.252|8
209.141.53.74|8
45.88.137.253|8
45.153.160.2|8
116.110.252.176|8
195.133.18.210|8
167.172.43.16|8
45.153.160.140|8
209.141.32.141|8
185.31.175.213|8
