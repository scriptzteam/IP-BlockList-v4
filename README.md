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
Wall of shame (2021-11-21)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.20|11
171.25.193.78|10
45.153.160.135|10
185.31.175.226|9
162.247.74.27|9
185.220.102.246|9
162.247.74.74|9
141.98.10.63|9
5.2.69.50|9
171.25.193.77|9
45.153.160.129|9
185.220.100.254|9
45.88.137.253|9
185.31.175.213|9
38.91.102.77|9
171.25.193.25|9
209.141.47.245|9
45.153.160.131|9
221.181.185.111|9
185.31.175.228|8
128.31.0.13|8
221.131.165.62|8
209.14.131.233|8
5.183.209.217|8
185.107.47.215|8
185.220.102.240|8
185.220.102.243|8
185.220.102.248|8
211.22.65.18|8
205.185.123.252|8
141.98.10.60|8
185.83.214.69|8
185.220.101.1|8
45.61.186.123|8
178.20.55.16|8
199.19.224.157|8
185.220.101.4|8
185.220.100.255|8
185.31.175.252|8
94.230.208.148|8
192.42.116.13|8
81.6.43.167|8
45.153.160.140|8
212.192.241.37|8
185.31.175.235|8
185.31.175.231|8
221.131.165.33|8
162.247.74.217|8
205.185.115.39|8
195.133.18.24|8
209.141.33.121|8
221.131.165.75|8
185.220.102.253|8
185.220.102.250|8
80.67.172.162|8
64.113.32.29|8
116.110.252.176|8
221.131.165.50|8
199.195.250.77|8
195.133.18.210|8
179.43.187.36|8
62.102.148.68|8
185.220.101.62|8
185.31.175.207|8
135.148.171.69|8
45.153.160.137|8
205.185.119.40|8
185.220.100.241|8
205.185.113.226|8
185.31.175.243|8
185.31.175.240|8
198.98.51.189|8
185.31.175.215|8
107.189.28.84|8
