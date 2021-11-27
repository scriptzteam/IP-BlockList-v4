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
Wall of shame (2021-11-27)
----

|IP|Number of (black)lists|
|---|--:|
205.185.115.39|10
171.25.193.78|10
45.61.186.123|10
116.110.252.176|10
179.43.187.37|10
185.31.175.226|9
23.129.64.130|9
141.98.10.63|9
23.183.81.116|9
178.20.55.18|9
195.133.18.210|9
212.192.241.124|9
209.141.33.193|9
185.220.100.252|9
45.88.137.253|9
212.192.241.37|9
185.31.175.215|9
141.98.10.246|9
116.105.217.54|9
36.110.228.254|9
221.131.165.33|9
185.100.86.74|9
171.25.193.25|9
209.141.47.245|9
209.141.33.121|9
209.141.53.74|9
221.181.185.111|9
209.141.62.185|9
116.110.156.69|9
221.10.33.104|9
185.31.175.228|8
185.31.175.220|8
159.223.2.20|8
162.247.74.206|8
199.249.230.163|8
205.185.114.87|8
185.220.102.244|8
185.220.102.240|8
185.220.102.243|8
162.247.74.74|8
205.185.122.230|8
221.131.165.62|8
5.2.69.50|8
171.25.193.77|8
206.189.58.12|8
162.247.72.199|8
167.71.11.216|8
89.163.243.88|8
23.183.82.135|8
205.185.120.71|8
171.25.193.20|8
195.133.18.24|8
185.191.124.143|8
221.131.165.75|8
185.38.175.132|8
80.67.172.162|8
45.13.104.179|8
221.131.165.50|8
209.141.32.141|8
185.56.80.65|8
185.100.87.129|8
89.163.252.30|8
23.183.81.54|8
45.153.160.133|8
45.153.160.130|8
45.153.160.135|8
45.88.137.100|8
185.31.175.243|8
45.153.160.139|8
209.141.52.25|8
117.248.249.70|8
163.172.213.212|8
185.100.87.202|8
