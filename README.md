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
Wall of shame (2021-10-23)
----

|IP|Number of (black)lists|
|---|--:|
209.141.53.99|10
165.22.100.49|10
222.187.238.58|10
185.73.124.253|10
171.25.193.20|10
198.98.52.12|10
221.131.165.75|10
141.98.10.60|10
199.195.253.199|10
221.181.185.94|10
209.141.40.193|10
199.19.224.76|10
141.98.10.81|10
141.98.10.82|10
209.141.55.232|10
198.98.48.67|10
199.195.251.49|10
128.31.0.13|9
162.247.74.27|9
185.220.102.4|9
209.141.56.75|9
171.25.193.25|9
89.234.157.254|9
95.172.47.98|9
212.193.30.101|9
185.220.102.244|9
185.220.102.248|9
162.247.74.74|9
221.131.165.50|9
221.131.165.65|9
185.73.124.100|9
5.2.69.50|9
171.25.193.77|9
18.27.197.252|9
136.144.41.253|9
185.100.87.72|9
185.129.62.62|9
89.163.252.12|9
185.31.175.247|9
139.59.144.149|9
167.88.161.219|9
163.172.213.212|9
185.31.175.226|8
185.31.175.220|8
162.247.74.206|8
185.220.103.7|8
185.31.175.231|8
179.43.175.26|8
117.68.2.93|8
221.131.165.33|8
162.247.74.217|8
5.183.209.217|8
176.10.99.200|8
198.98.49.124|8
222.186.30.112|8
185.100.86.74|8
176.111.173.237|8
209.141.47.39|8
89.163.249.192|8
195.133.18.116|8
199.19.226.61|8
185.220.102.241|8
185.220.102.243|8
198.98.54.17|8
185.38.175.132|8
185.220.102.253|8
185.220.102.250|8
80.67.172.162|8
8.209.91.186|8
64.113.32.29|8
185.83.214.69|8
209.141.59.9|8
209.141.60.103|8
185.220.101.1|8
103.47.14.246|8
185.56.80.65|8
45.153.160.2|8
209.141.42.170|8
212.193.30.32|8
5.199.143.202|8
209.127.17.234|8
162.247.72.199|8
45.153.160.133|8
45.153.160.136|8
45.153.160.139|8
185.247.225.61|8
185.220.100.242|8
185.220.100.240|8
185.220.100.241|8
209.127.17.242|8
54.36.108.162|8
185.220.100.253|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
198.96.155.3|8
185.31.175.243|8
205.185.126.71|8
221.181.185.111|8
141.98.10.121|8
205.185.116.163|8
166.70.207.2|8
89.163.243.88|8
185.130.44.108|8
159.223.24.19|8
68.183.180.46|8
198.144.121.93|8
222.187.232.39|8
45.153.160.140|8
185.31.175.213|8
185.31.175.215|8
185.100.87.202|8
