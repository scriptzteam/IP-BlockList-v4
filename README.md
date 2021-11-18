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
5.183.209.217|10
162.247.74.74|10
171.25.193.20|10
45.88.137.253|10
60.170.247.162|10
171.25.193.25|10
209.127.17.234|10
199.249.230.163|9
209.141.43.8|9
89.234.157.254|9
185.107.47.215|9
162.247.74.27|9
185.220.102.240|9
141.98.10.63|9
141.98.10.60|9
199.19.225.172|9
199.19.224.157|9
45.153.160.129|9
185.220.100.252|9
198.144.121.93|9
209.141.44.165|9
185.31.175.235|9
185.31.175.231|9
185.100.86.74|9
195.133.18.24|9
222.187.254.41|9
221.131.165.75|9
185.220.102.250|9
64.113.32.29|9
116.110.252.176|9
221.131.165.50|9
185.220.101.57|9
62.102.148.69|9
45.153.160.135|9
209.141.62.233|9
199.19.224.231|9
185.31.175.215|9
185.220.101.1|8
185.31.175.228|8
159.223.2.20|8
162.247.74.206|8
199.19.225.198|8
222.186.30.112|8
176.111.173.238|8
185.220.102.244|8
185.220.102.246|8
185.220.102.242|8
185.220.102.243|8
185.220.102.248|8
211.22.65.18|8
205.185.123.252|8
205.185.114.87|8
185.83.214.69|8
5.2.69.50|8
164.52.24.164|8
171.25.193.77|8
171.25.193.78|8
80.82.77.139|8
195.133.18.210|8
161.35.199.104|8
209.141.33.193|8
192.160.102.170|8
185.220.100.254|8
89.163.249.244|8
176.10.99.200|8
185.31.175.252|8
185.165.168.229|8
166.70.207.2|8
185.220.102.4|8
116.110.99.56|8
93.123.93.104|8
212.192.241.37|8
89.163.243.88|8
193.32.126.151|8
205.185.120.71|8
222.186.180.130|8
185.220.103.7|8
38.91.102.77|8
162.247.74.217|8
205.185.115.39|8
222.187.238.58|8
176.10.104.240|8
209.141.33.121|8
209.141.59.77|8
185.38.175.132|8
185.220.102.254|8
178.17.174.14|8
80.67.172.162|8
94.230.208.147|8
199.195.250.77|8
185.31.175.207|8
205.185.119.40|8
185.220.100.242|8
185.220.100.241|8
185.170.114.25|8
205.185.119.112|8
205.185.113.226|8
209.141.47.245|8
185.31.175.243|8
185.31.175.240|8
185.31.175.247|8
221.181.185.111|8
209.141.62.185|8
209.141.59.180|8
45.153.160.2|8
107.189.30.134|8
107.189.8.65|8
