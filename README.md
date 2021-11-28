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
171.25.193.78|10
178.20.55.18|10
45.88.137.253|10
212.192.241.37|10
141.98.10.246|10
205.185.115.39|10
171.25.193.20|10
116.110.252.176|10
163.172.213.212|10
185.31.175.226|9
89.234.157.254|9
185.220.102.244|9
185.220.102.243|9
171.25.193.77|9
185.220.101.1|9
45.61.186.123|9
212.192.241.124|9
209.141.33.193|9
192.160.102.170|9
185.220.100.252|9
198.144.121.93|9
23.183.82.135|9
116.105.217.54|9
36.110.228.254|9
221.131.165.33|9
171.25.193.25|9
195.133.18.24|9
80.67.172.162|9
179.43.187.37|9
209.141.33.121|9
45.153.160.133|9
209.141.47.245|9
209.141.52.25|9
209.141.62.185|9
116.110.156.69|9
221.10.33.104|9
185.31.175.220|8
45.153.160.129|8
23.183.81.249|8
23.129.64.130|8
205.185.114.87|8
185.220.102.248|8
162.247.74.74|8
205.185.122.230|8
195.254.135.76|8
141.98.10.63|8
221.131.165.62|8
5.2.69.50|8
185.220.101.3|8
23.183.81.116|8
178.20.55.16|8
161.35.199.104|8
221.181.185.111|8
159.223.2.20|8
185.220.100.255|8
185.220.100.254|8
94.230.208.147|8
185.165.168.229|8
192.42.116.16|8
185.220.102.4|8
185.220.102.8|8
38.91.102.36|8
209.141.34.220|8
209.141.53.74|8
193.32.126.151|8
205.185.120.71|8
38.91.102.77|8
162.247.74.217|8
185.100.86.74|8
222.187.254.41|8
185.191.124.143|8
221.131.165.75|8
213.202.216.189|8
185.220.102.254|8
64.113.32.29|8
221.131.165.50|8
222.186.30.76|8
164.92.250.114|8
195.133.18.210|8
209.141.32.141|8
23.183.81.54|8
45.153.160.135|8
45.88.137.100|8
162.247.72.199|8
185.31.175.243|8
23.183.82.180|8
45.153.160.131|8
209.141.62.233|8
117.248.249.70|8
185.31.175.215|8
107.189.28.84|8
