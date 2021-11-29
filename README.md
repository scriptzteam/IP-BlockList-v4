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
Wall of shame (2021-11-29)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.244|10
45.88.137.253|10
23.183.82.135|10
141.98.10.246|10
36.110.228.254|10
209.141.62.233|10
185.31.175.220|9
171.25.193.77|9
185.220.101.1|9
212.192.241.124|9
209.141.33.193|9
212.192.241.37|9
221.131.165.33|9
171.25.193.25|9
221.131.165.75|9
213.202.216.189|9
209.141.53.74|9
80.67.172.162|9
116.110.252.176|9
221.131.165.50|9
209.141.32.141|9
209.141.33.121|9
209.141.34.220|9
23.183.81.54|9
23.183.82.180|9
209.141.52.25|9
221.181.185.111|9
23.183.81.227|9
163.172.213.212|9
167.172.43.16|9
185.31.175.226|8
159.223.2.20|8
221.131.165.62|8
23.183.81.249|8
58.222.83.94|8
5.183.209.217|8
89.234.157.254|8
23.129.64.130|8
185.107.47.215|8
185.220.102.243|8
185.220.102.248|8
162.247.74.74|8
205.185.122.230|8
141.98.10.63|8
5.2.69.50|8
205.185.114.149|8
198.98.59.119|8
171.25.193.78|8
164.92.242.66|8
185.31.175.247|8
18.27.197.252|8
23.183.81.116|8
165.22.195.82|8
45.61.186.123|8
178.20.55.16|8
185.220.101.63|8
5.2.73.229|8
185.220.100.253|8
185.220.100.252|8
185.220.100.254|8
205.185.114.87|8
185.100.87.72|8
94.230.208.148|8
185.220.102.4|8
198.144.121.93|8
107.189.8.254|8
205.185.120.71|8
222.186.180.130|8
116.105.217.54|8
205.185.115.39|8
107.189.4.203|8
171.25.193.20|8
195.133.18.24|8
185.191.124.143|8
2.56.59.114|8
185.220.102.253|8
185.220.102.250|8
64.113.32.29|8
178.20.55.18|8
195.133.18.210|8
179.43.187.37|8
185.100.87.129|8
104.244.76.13|8
185.31.175.207|8
176.10.99.200|8
45.153.160.133|8
209.141.47.245|8
45.153.160.135|8
209.141.62.185|8
116.110.156.69|8
209.141.44.236|8
221.10.33.104|8
37.123.163.58|8
94.153.161.234|8
