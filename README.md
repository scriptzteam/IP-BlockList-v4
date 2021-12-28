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
Wall of shame (2021-12-28)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.246|10
171.25.193.78|10
45.13.104.179|10
45.153.160.133|10
81.17.18.58|10
185.220.100.254|9
185.215.167.218|9
221.131.165.65|9
171.25.193.77|9
221.181.185.94|9
81.17.18.61|9
162.247.72.199|9
185.220.100.252|9
185.220.100.255|9
185.100.87.72|9
185.220.102.4|9
45.153.160.140|9
209.141.54.15|9
209.141.34.220|9
62.233.50.53|9
38.91.102.77|9
171.25.193.25|9
195.133.18.24|9
209.141.47.245|9
209.141.53.74|9
164.90.230.201|9
45.153.160.130|9
80.82.77.33|8
5.183.209.217|8
89.234.157.254|8
89.163.249.192|8
185.220.102.240|8
185.220.102.241|8
185.220.102.248|8
185.220.102.249|8
195.133.18.104|8
23.236.146.162|8
171.25.193.20|8
165.22.204.197|8
5.2.69.50|8
164.52.24.164|8
38.91.102.84|8
185.220.101.188|8
185.14.97.147|8
51.15.43.205|8
167.99.36.169|8
23.154.177.7|8
104.244.72.132|8
5.79.109.48|8
81.17.18.62|8
45.153.160.129|8
107.189.7.88|8
185.220.100.253|8
89.163.249.244|8
176.10.99.200|8
192.42.116.16|8
2.58.149.182|8
166.70.207.2|8
107.189.31.241|8
198.98.56.60|8
185.130.44.108|8
185.56.80.65|8
60.170.247.162|8
185.243.218.50|8
205.185.120.235|8
36.110.228.254|8
162.247.74.217|8
162.247.74.213|8
45.153.160.2|8
222.187.238.58|8
185.100.86.74|8
5.2.72.73|8
134.209.83.158|8
165.232.92.17|8
104.244.73.93|8
45.61.184.103|8
185.38.175.132|8
213.202.216.189|8
185.220.102.254|8
185.220.102.251|8
80.67.172.162|8
104.244.72.168|8
64.113.32.29|8
23.154.177.6|8
179.43.187.37|8
121.134.173.39|8
209.141.47.131|8
185.100.87.129|8
89.163.252.30|8
171.252.186.42|8
45.153.160.137|8
45.153.160.136|8
45.153.160.134|8
45.153.160.139|8
107.189.1.90|8
185.220.100.242|8
185.220.100.241|8
45.88.137.100|8
107.189.1.167|8
221.181.185.111|8
198.98.51.189|8
104.244.78.62|8
92.255.85.28|8
167.172.43.16|8
212.192.246.95|8
185.100.87.202|8
