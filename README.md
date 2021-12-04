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
Wall of shame (2021-12-04)
----

|IP|Number of (black)lists|
|---|--:|
185.31.175.226|10
185.31.175.220|10
185.220.102.244|10
205.185.122.230|10
45.88.137.253|10
212.192.241.37|10
141.98.10.246|10
185.31.175.215|10
23.183.81.249|9
176.111.173.237|9
141.98.10.63|9
5.2.69.50|9
171.25.193.77|9
171.25.193.78|9
212.192.241.124|9
45.153.160.129|9
23.183.81.136|9
185.31.175.252|9
199.249.230.119|9
45.153.160.140|9
222.187.238.58|9
205.185.120.71|9
185.31.175.231|9
116.105.217.54|9
221.131.165.33|9
185.100.86.74|9
171.25.193.20|9
221.131.165.75|9
185.38.175.132|9
2.56.59.114|9
185.220.102.254|9
80.67.172.162|9
45.13.104.179|9
221.131.165.50|9
209.141.32.141|9
185.56.80.65|9
185.100.87.129|9
185.31.175.207|9
23.183.81.54|9
209.141.47.245|9
185.31.175.247|9
23.183.82.180|9
221.181.185.111|9
209.141.62.185|9
163.172.213.212|9
167.172.43.16|9
209.141.53.74|9
89.163.252.230|8
185.31.175.228|8
80.82.77.33|8
134.209.198.229|8
185.117.215.9|8
5.183.209.217|8
89.234.157.254|8
205.185.115.39|8
136.144.41.139|8
185.220.102.246|8
185.220.102.240|8
185.220.102.243|8
162.247.74.74|8
104.248.85.104|8
167.99.223.124|8
205.185.125.72|8
107.189.10.237|8
185.220.101.4|8
185.220.101.1|8
23.129.64.210|8
18.27.197.252|8
212.192.241.95|8
45.154.255.147|8
134.209.205.40|8
23.183.81.116|8
165.22.195.82|8
178.20.55.18|8
178.20.55.16|8
81.17.18.61|8
81.17.18.62|8
162.247.72.199|8
185.42.170.203|8
104.244.78.183|8
209.141.33.193|8
185.220.100.252|8
185.220.100.254|8
137.184.49.249|8
89.163.249.244|8
185.31.175.213|8
89.163.243.88|8
23.183.82.135|8
185.31.175.235|8
23.183.82.117|8
198.98.57.230|8
104.244.72.120|8
45.153.160.2|8
171.25.193.25|8
195.133.18.24|8
209.141.33.121|8
213.202.216.189|8
185.220.102.253|8
185.220.102.250|8
116.110.252.176|8
107.189.30.23|8
89.163.154.91|8
209.141.34.220|8
185.220.101.61|8
185.31.175.188|8
185.129.61.1|8
5.199.143.202|8
185.220.102.245|8
185.220.102.247|8
45.153.160.132|8
45.153.160.131|8
45.153.160.130|8
45.153.160.137|8
45.153.160.135|8
45.153.160.139|8
45.153.160.138|8
81.17.18.59|8
45.88.137.100|8
104.244.77.80|8
185.31.175.243|8
185.31.175.240|8
116.110.156.69|8
23.183.81.227|8
162.247.73.192|8
209.141.44.236|8
134.209.95.47|8
37.123.163.58|8
185.220.102.252|8
212.192.246.95|8
