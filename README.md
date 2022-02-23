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
Wall of shame (2022-02-23)
----

|IP|Number of (black)lists|
|---|--:|
185.56.80.65|11
185.129.62.62|11
171.25.193.78|10
185.254.75.32|10
45.153.160.2|10
89.185.85.100|9
185.117.215.9|9
5.183.209.217|9
89.163.249.244|9
185.220.102.246|9
185.220.102.240|9
5.2.69.50|9
185.220.100.254|9
185.100.87.72|9
192.42.116.16|9
116.105.212.31|9
23.154.177.19|9
171.25.193.20|9
171.25.193.25|9
209.141.58.240|9
185.220.102.253|9
23.154.177.5|9
80.67.167.81|9
89.185.85.253|9
45.154.168.39|9
45.153.160.135|9
45.153.160.134|9
179.43.187.173|8
104.244.74.57|8
89.163.252.230|8
128.31.0.13|8
45.61.187.112|8
89.234.157.254|8
45.9.20.73|8
185.107.47.215|8
179.43.175.170|8
185.220.102.244|8
185.220.102.247|8
185.220.102.241|8
185.220.102.243|8
185.220.102.248|8
185.220.102.249|8
162.247.74.74|8
81.17.24.154|8
171.25.193.77|8
185.107.47.171|8
185.220.101.4|8
185.220.101.3|8
185.220.101.1|8
23.154.177.3|8
5.79.109.48|8
81.17.18.61|8
81.17.18.60|8
23.154.177.21|8
23.154.177.20|8
185.220.100.253|8
185.220.100.255|8
185.100.87.174|8
166.70.207.2|8
185.220.102.4|8
45.153.160.140|8
46.19.139.18|8
185.220.103.5|8
116.110.3.253|8
107.189.29.207|8
118.186.201.132|8
213.202.216.189|8
185.220.102.251|8
185.220.102.250|8
64.113.32.29|8
45.9.20.25|8
23.154.177.6|8
62.102.148.69|8
104.244.76.13|8
185.129.61.1|8
45.153.160.133|8
45.153.160.136|8
45.153.160.139|8
61.177.172.92|8
185.220.100.242|8
114.241.52.59|8
162.247.72.199|8
23.154.177.7|8
162.247.73.192|8
37.123.163.58|8
185.220.103.115|8
81.17.18.58|8
46.166.139.111|8
185.100.87.202|8
