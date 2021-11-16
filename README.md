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
Wall of shame (2021-11-16)
----

|IP|Number of (black)lists|
|---|--:|
195.133.18.210|10
45.88.137.253|10
171.25.193.20|10
195.133.18.24|10
5.183.209.217|9
199.19.224.231|9
171.25.193.77|9
209.141.33.193|9
205.185.114.87|9
209.141.43.8|9
60.170.247.162|9
36.110.228.254|9
221.131.165.50|9
209.141.32.141|9
135.148.171.69|9
205.185.119.112|9
221.181.185.111|9
209.141.62.185|9
107.189.30.134|9
80.82.77.33|8
89.163.249.244|8
176.111.173.237|8
116.110.121.105|8
162.247.74.74|8
211.22.65.18|8
141.98.10.60|8
185.83.214.69|8
5.2.69.50|8
199.19.225.172|8
185.220.101.1|8
80.82.77.139|8
199.19.224.157|8
198.144.121.93|8
45.153.160.140|8
93.123.93.104|8
185.31.175.213|8
209.141.44.165|8
205.185.120.71|8
185.31.175.231|8
38.91.102.77|8
205.185.115.39|8
45.144.225.69|8
171.25.193.25|8
222.187.254.41|8
209.141.33.121|8
185.191.124.143|8
209.141.59.77|8
221.131.165.75|8
185.38.175.132|8
213.202.216.189|8
185.220.102.253|8
185.220.102.250|8
80.67.172.162|8
64.113.32.29|8
185.220.101.57|8
209.127.17.234|8
45.153.160.135|8
205.185.119.40|8
185.220.100.242|8
141.98.10.109|8
209.141.47.245|8
185.31.175.243|8
185.31.175.240|8
185.31.175.247|8
209.141.62.233|8
185.31.175.215|8
209.141.59.180|8
141.98.10.142|8
163.172.213.212|8
185.100.87.202|8
