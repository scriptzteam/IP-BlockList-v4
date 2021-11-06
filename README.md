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
Wall of shame (2021-11-06)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.240|10
141.98.10.60|10
171.25.193.25|10
45.153.160.135|10
89.234.157.254|9
162.247.74.74|9
141.98.10.63|9
5.2.69.50|9
171.25.193.77|9
185.107.47.171|9
185.220.101.4|9
195.133.18.210|9
45.153.160.129|9
185.100.87.72|9
166.70.207.2|9
198.144.121.93|9
45.88.137.253|9
162.247.74.27|9
185.31.175.235|9
185.31.175.231|9
185.100.86.74|9
185.220.102.253|9
80.67.172.162|9
136.144.41.253|9
64.113.32.29|9
2.56.59.39|9
205.185.120.180|9
185.31.175.240|9
141.98.10.82|9
209.141.59.184|9
185.100.87.202|9
185.31.175.228|8
185.31.175.226|8
185.220.102.241|8
185.83.214.69|8
171.25.193.78|8
185.220.101.1|8
80.82.77.139|8
121.17.188.179|8
185.90.136.171|8
185.220.100.252|8
185.220.100.254|8
141.98.10.121|8
198.96.155.3|8
185.31.175.252|8
185.220.102.4|8
38.91.102.38|8
5.189.168.79|8
45.153.160.140|8
185.31.175.213|8
198.98.49.124|8
171.25.193.20|8
209.141.33.121|8
221.131.165.75|8
185.38.175.132|8
185.220.102.251|8
8.209.91.186|8
94.230.208.147|8
185.31.175.207|8
176.10.99.200|8
117.7.122.163|8
141.98.10.109|8
185.31.175.243|8
45.153.160.139|8
198.98.51.189|8
141.98.10.81|8
37.123.163.58|8
