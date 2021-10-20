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
Wall of shame (2021-10-20)
----

|IP|Number of (black)lists|
|---|--:|
221.181.185.94|10
136.144.41.253|10
199.19.224.76|10
222.187.238.58|10
199.195.251.49|10
141.98.10.81|10
141.98.10.82|10
141.98.10.60|10
165.22.100.49|9
205.185.121.149|9
185.73.124.100|9
199.19.226.61|9
198.98.54.17|9
221.131.165.65|9
209.141.51.168|9
212.193.30.32|9
209.127.17.242|9
141.98.10.121|9
45.153.160.140|9
60.170.247.162|9
209.141.53.99|9
179.43.175.26|9
221.131.165.33|9
209.141.56.75|9
198.98.49.124|9
185.73.124.253|9
212.193.30.84|9
212.193.30.101|9
221.131.165.75|9
68.183.180.46|9
222.187.232.39|9
209.141.55.232|9
221.131.165.50|9
209.141.59.9|9
185.56.80.65|9
136.144.138.169|9
205.185.116.163|9
185.31.175.215|9
159.223.24.19|9
199.195.248.175|8
162.247.74.206|8
5.183.209.217|8
222.186.30.112|8
176.111.173.238|8
185.220.102.244|8
185.220.102.243|8
185.220.102.249|8
5.2.69.50|8
209.141.60.103|8
23.129.64.160|8
60.8.87.190|8
45.153.160.129|8
54.36.108.162|8
185.31.175.252|8
199.195.248.54|8
107.189.31.248|8
185.220.102.4|8
212.192.246.88|8
89.163.243.88|8
45.135.232.159|8
107.189.5.248|8
93.174.95.106|8
185.220.103.7|8
185.31.175.235|8
185.31.175.231|8
45.153.160.2|8
185.100.86.74|8
171.25.193.20|8
195.133.18.116|8
209.141.55.125|8
116.105.72.49|8
185.220.102.253|8
185.220.102.252|8
185.220.102.251|8
80.67.172.162|8
8.209.91.186|8
45.129.56.200|8
116.110.124.53|8
185.31.175.207|8
45.153.160.133|8
45.153.160.132|8
185.247.225.67|8
212.193.30.64|8
185.247.225.85|8
185.31.175.243|8
185.31.175.240|8
185.31.175.247|8
221.181.185.111|8
139.59.144.149|8
162.247.74.27|8
163.172.213.212|8
107.189.30.134|8
