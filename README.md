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
Wall of shame (2021-10-29)
----

|IP|Number of (black)lists|
|---|--:|
141.98.10.60|9
136.144.41.253|9
171.25.193.25|9
212.193.30.101|9
141.98.10.81|9
141.98.10.82|9
128.31.0.13|8
199.195.248.175|8
89.234.157.254|8
162.247.74.74|8
141.98.10.63|8
171.25.193.78|8
209.141.60.103|8
185.220.101.4|8
167.88.161.219|8
185.220.100.252|8
185.220.100.255|8
205.185.126.71|8
205.185.120.183|8
162.247.74.27|8
179.43.175.26|8
162.247.74.217|8
171.25.193.20|8
209.141.33.121|8
209.141.59.77|8
80.67.172.162|8
68.183.180.46|8
64.113.32.29|8
209.141.55.232|8
185.129.62.62|8
45.153.160.133|8
185.220.100.242|8
185.220.100.240|8
199.195.253.210|8
139.59.144.149|8
159.223.24.19|8
