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
Wall of shame (2021-12-18)
----

|IP|Number of (black)lists|
|---|--:|
205.185.114.158|10
205.185.115.39|9
107.189.1.167|9
141.98.10.63|9
209.141.44.102|9
185.220.102.4|9
222.187.238.58|9
205.185.120.235|9
195.133.18.24|9
209.141.34.220|9
176.10.99.200|9
221.181.185.111|9
164.90.203.55|8
178.128.249.136|8
89.234.157.254|8
185.107.47.215|8
185.220.102.247|8
185.220.102.243|8
212.192.241.163|8
107.189.14.215|8
221.181.185.94|8
209.141.48.248|8
185.220.100.254|8
185.100.87.72|8
166.70.207.2|8
45.88.137.253|8
176.10.104.240|8
205.185.120.71|8
116.110.19.131|8
45.88.188.13|8
209.141.47.245|8
165.22.195.82|8
209.141.53.74|8
80.67.172.162|8
45.13.104.179|8
64.113.32.29|8
221.131.165.50|8
179.43.187.37|8
185.56.80.65|8
161.35.205.46|8
45.153.160.133|8
45.153.160.134|8
81.17.18.59|8
167.172.43.16|8
