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
Wall of shame (2022-02-20)
----

|IP|Number of (black)lists|
|---|--:|
45.153.160.2|11
185.100.87.174|11
5.183.209.217|10
185.220.102.250|10
185.56.80.65|10
45.153.160.135|10
185.146.232.25|9
185.220.102.247|9
171.25.193.77|9
171.25.193.78|9
23.154.177.21|9
185.220.100.254|9
192.42.116.16|9
171.25.193.25|9
80.67.167.81|9
23.154.177.18|9
89.185.85.253|9
185.129.62.62|9
45.153.160.133|9
45.153.160.134|9
45.153.160.139|9
185.220.103.115|9
179.43.187.173|8
128.31.0.13|8
107.189.10.237|8
89.185.85.100|8
45.61.187.112|8
185.220.100.252|8
185.117.215.9|8
89.163.249.244|8
89.234.157.254|8
116.105.212.31|8
45.9.20.73|8
91.250.242.12|8
185.36.81.95|8
179.43.175.170|8
185.220.102.244|8
185.220.102.246|8
185.220.102.240|8
185.220.102.242|8
185.220.102.243|8
185.220.102.248|8
185.220.102.249|8
162.247.74.74|8
81.17.24.154|8
5.2.69.50|8
185.107.47.171|8
185.100.87.133|8
185.254.75.32|8
81.17.18.61|8
81.17.18.60|8
81.17.18.62|8
185.220.100.253|8
185.220.100.255|8
192.42.116.14|8
166.70.207.2|8
177.124.97.50|8
185.220.102.4|8
185.220.102.8|8
23.154.177.19|8
45.153.160.140|8
176.111.173.245|8
46.19.139.18|8
27.122.59.100|8
185.220.103.7|8
162.247.74.216|8
185.100.86.74|8
171.25.193.20|8
5.2.73.169|8
118.186.201.132|8
213.202.216.189|8
185.220.102.254|8
185.220.102.253|8
185.220.102.252|8
185.220.102.251|8
64.113.32.29|8
204.8.156.142|8
36.37.82.198|8
45.9.20.25|8
23.154.177.6|8
23.154.177.5|8
62.102.148.69|8
179.43.139.10|8
209.141.58.146|8
45.153.160.136|8
179.43.159.4|8
114.241.52.59|8
198.98.51.189|8
185.100.87.202|8
