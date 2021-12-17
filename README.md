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
Wall of shame (2021-12-17)
----

|IP|Number of (black)lists|
|---|--:|
205.185.114.158|10
141.98.10.63|10
222.187.238.58|9
205.185.115.39|9
195.133.18.24|9
185.220.102.243|9
185.38.175.132|9
80.67.172.162|9
64.113.32.29|9
185.100.87.72|9
221.181.185.111|9
185.220.100.254|9
107.189.1.167|9
209.141.44.102|9
166.70.207.2|9
185.220.102.4|9
185.56.80.65|9
205.185.120.235|8
205.185.120.71|8
178.20.55.16|8
38.91.102.77|8
164.90.203.55|8
45.88.188.13|8
89.234.157.254|8
171.25.193.25|8
185.107.47.215|8
209.141.47.245|8
185.220.102.247|8
162.247.74.74|8
213.202.216.189|8
185.220.102.254|8
209.141.53.74|8
107.189.11.153|8
221.131.165.50|8
171.25.193.77|8
171.25.193.78|8
23.154.177.6|8
185.107.47.171|8
179.43.187.37|8
209.141.34.220|8
176.10.104.240|8
161.35.205.46|8
107.189.14.215|8
221.181.185.94|8
165.22.195.82|8
178.20.55.18|8
176.10.99.200|8
162.247.72.199|8
45.153.160.133|8
45.153.160.134|8
209.141.48.248|8
81.17.18.59|8
185.220.100.255|8
195.254.135.76|8
192.42.116.13|8
45.88.137.253|8
198.98.51.189|8
167.172.43.16|8
45.153.160.140|8
