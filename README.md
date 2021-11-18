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
Wall of shame (2021-11-18)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.20|11
162.247.74.74|10
45.88.137.253|10
209.141.44.165|10
171.25.193.25|10
5.183.209.217|9
141.98.10.63|9
141.98.10.60|9
205.185.114.87|9
199.19.225.172|9
171.25.193.77|9
195.133.18.210|9
209.141.33.193|9
185.220.100.252|9
185.165.168.229|9
116.110.99.56|9
185.130.44.108|9
198.144.121.93|9
212.192.241.37|9
60.170.247.162|9
185.31.175.231|9
36.110.228.254|9
195.133.18.24|9
222.187.254.41|9
185.220.102.250|9
116.110.252.176|9
221.131.165.50|9
62.102.148.69|9
205.185.119.112|9
185.31.175.240|9
199.19.224.231|9
209.141.62.185|9
185.31.175.215|9
185.220.101.1|8
185.31.175.228|8
185.31.175.226|8
185.31.175.220|8
80.82.77.33|8
162.247.74.206|8
199.249.230.163|8
199.19.225.198|8
209.141.43.8|8
89.234.157.254|8
185.107.47.215|8
116.110.121.105|8
185.220.102.244|8
185.220.102.240|8
185.220.102.248|8
211.22.65.18|8
80.82.77.139|8
178.20.55.18|8
178.20.55.16|8
199.19.224.157|8
185.107.47.171|8
161.35.199.104|8
45.153.160.129|8
185.220.100.253|8
185.220.100.255|8
185.220.100.254|8
89.163.249.244|8
185.31.175.252|8
185.100.87.72|8
192.42.116.16|8
185.220.102.4|8
141.98.10.92|8
93.123.93.104|8
185.31.175.213|8
193.142.146.242|8
193.32.126.151|8
93.174.95.106|8
185.220.103.7|8
185.31.175.235|8
38.91.102.77|8
205.185.115.39|8
176.10.104.240|8
209.141.33.121|8
185.191.124.143|8
209.141.59.77|8
221.131.165.75|8
185.38.175.132|8
185.220.102.253|8
80.67.172.162|8
94.230.208.147|8
64.113.32.29|8
185.220.101.57|8
209.141.32.141|8
185.56.80.65|8
104.244.76.13|8
185.31.175.207|8
176.10.99.200|8
209.127.17.234|8
45.153.160.136|8
45.153.160.135|8
205.185.119.40|8
185.220.100.242|8
185.220.100.241|8
45.88.137.100|8
2.56.59.198|8
209.141.47.245|8
185.220.101.35|8
185.31.175.247|8
221.181.185.111|8
209.141.62.233|8
141.98.10.82|8
163.172.213.212|8
