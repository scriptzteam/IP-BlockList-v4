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
Wall of shame (2021-12-09)
----

|IP|Number of (black)lists|
|---|--:|
116.110.19.131|9
185.31.175.226|9
116.110.92.217|9
141.98.10.246|9
205.185.120.71|9
116.105.77.214|9
221.131.165.75|9
221.131.165.50|9
185.31.175.215|9
222.187.238.58|9
185.165.171.175|8
134.209.205.40|8
185.31.175.228|8
185.31.175.220|8
80.82.77.33|8
136.144.41.139|8
185.100.86.74|8
185.31.175.231|8
199.249.230.163|8
221.131.165.33|8
45.153.160.131|8
222.186.42.137|8
205.185.115.39|8
185.31.175.196|8
195.133.18.24|8
212.192.241.124|8
23.183.82.180|8
185.220.102.244|8
185.220.102.241|8
221.181.185.111|8
185.38.175.132|8
209.141.53.74|8
141.98.10.63|8
45.88.137.253|8
104.248.85.104|8
205.185.114.149|8
37.123.163.58|8
171.25.193.78|8
167.172.43.16|8
212.192.241.37|8
163.172.213.212|8
185.56.80.65|8
185.100.87.202|8
209.141.34.220|8
