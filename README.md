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
Wall of shame (2021-12-06)
----

|IP|Number of (black)lists|
|---|--:|
185.31.175.226|10
162.247.74.74|10
45.153.160.140|10
222.187.238.58|10
171.25.193.20|10
163.172.213.212|10
185.31.175.220|9
199.249.230.163|9
23.183.81.249|9
5.183.209.217|9
176.111.173.237|9
185.220.102.243|9
141.98.10.63|9
185.83.214.69|9
205.185.114.149|9
185.31.175.231|9
171.25.193.77|9
171.25.193.78|9
185.220.101.1|9
212.192.241.95|9
45.153.160.2|9
134.209.205.40|9
212.192.241.124|9
104.244.78.183|9
192.42.116.16|9
45.88.137.253|9
185.220.102.4|9
212.192.241.37|9
185.31.175.215|9
141.98.10.246|9
221.131.165.33|9
171.25.193.25|9
222.187.254.41|9
185.107.47.215|9
185.220.102.251|9
45.13.104.179|9
221.131.165.50|9
185.165.171.175|9
209.141.34.220|9
62.102.148.68|9
167.172.43.16|9
185.31.175.188|9
23.183.81.54|9
185.31.175.243|9
185.31.175.240|9
23.183.82.180|9
221.181.185.111|9
134.209.95.47|9
185.31.175.228|8
20.206.86.43|8
134.209.198.229|8
107.189.10.237|8
58.222.83.94|8
205.185.115.39|8
38.91.102.46|8
89.163.249.192|8
45.144.225.119|8
185.220.102.242|8
185.220.102.248|8
185.220.102.249|8
195.133.18.104|8
104.248.85.104|8
5.2.69.50|8
167.99.223.124|8
164.52.24.164|8
23.183.81.116|8
198.96.155.3|8
185.107.47.171|8
23.183.81.136|8
178.20.55.18|8
178.20.55.16|8
81.17.18.61|8
81.17.18.62|8
162.247.72.199|8
192.160.102.170|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
195.254.135.76|8
94.230.208.147|8
185.31.175.252|8
185.130.44.108|8
137.184.49.88|8
23.183.82.135|8
185.243.218.50|8
205.185.120.71|8
185.220.103.7|8
185.31.175.235|8
38.91.102.77|8
162.247.74.216|8
162.247.74.217|8
195.133.18.24|8
199.195.252.18|8
221.131.165.75|8
185.38.175.132|8
213.202.216.189|8
185.220.102.254|8
185.220.102.253|8
185.220.102.252|8
80.67.172.162|8
64.113.32.29|8
199.195.250.77|8
185.56.80.65|8
72.167.48.55|8
185.100.87.129|8
89.163.252.30|8
199.195.254.81|8
176.10.99.200|8
185.220.102.245|8
45.153.160.133|8
45.153.160.130|8
45.153.160.134|8
45.153.160.139|8
45.88.137.100|8
209.141.47.245|8
107.189.4.203|8
209.141.62.185|8
23.183.81.227|8
209.141.53.74|8
185.100.87.202|8
212.192.246.95|8
