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
Wall of shame (2022-03-02)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.243|10
162.247.74.74|9
171.25.193.77|9
185.100.87.174|9
192.42.116.16|9
171.25.193.20|9
89.185.85.253|9
45.154.168.39|9
179.43.187.173|8
89.185.85.100|8
185.117.215.9|8
5.2.76.207|8
89.234.157.254|8
179.43.175.170|8
185.220.102.247|8
5.2.69.50|8
165.22.211.85|8
171.25.193.78|8
136.144.41.22|8
23.154.177.3|8
185.100.87.72|8
185.165.168.229|8
116.105.216.128|8
5.183.209.217|8
185.220.102.4|8
107.189.29.207|8
171.25.193.25|8
80.67.167.81|8
45.153.160.133|8
45.153.160.137|8
45.153.160.135|8
185.220.101.12|8
198.98.51.189|8
37.123.163.58|8
185.220.103.115|8
