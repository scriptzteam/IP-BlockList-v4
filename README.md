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
209.141.40.193|11
209.141.53.99|10
18.27.197.252|10
222.187.238.58|10
185.73.124.253|10
198.98.52.12|10
221.131.165.75|10
141.98.10.60|10
221.181.185.94|10
141.98.10.81|10
141.98.10.82|10
198.98.48.67|10
199.195.251.49|10
165.22.100.49|9
221.131.165.33|9
209.141.56.75|9
5.183.209.217|9
212.193.30.101|9
185.220.102.242|9
198.98.54.17|9
221.131.165.50|9
221.131.165.65|9
185.73.124.100|9
5.2.69.50|9
199.195.253.199|9
209.141.59.9|9
185.56.80.65|9
45.153.160.2|9
136.144.41.253|9
5.199.143.202|9
209.127.17.234|9
45.153.160.140|9
167.88.161.219|9
199.19.224.76|9
89.163.243.88|9
209.141.55.232|9
163.172.213.212|9
222.187.232.39|9
45.135.232.159|8
60.170.247.162|8
185.31.175.226|8
185.31.175.220|8
128.31.0.13|8
162.247.74.27|8
185.220.103.5|8
185.220.102.4|8
185.31.175.231|8
179.43.175.26|8
171.25.193.25|8
89.234.157.254|8
198.98.49.124|8
176.111.173.237|8
95.172.47.98|8
209.141.47.39|8
185.107.47.215|8
195.133.18.116|8
185.220.102.244|8
185.220.102.252|8
185.220.102.250|8
80.67.172.162|8
185.247.225.85|8
171.25.193.77|8
209.141.60.103|8
209.141.42.170|8
212.193.30.32|8
185.100.87.72|8
136.144.138.169|8
89.163.252.12|8
162.247.72.199|8
45.153.160.133|8
45.153.160.136|8
45.153.160.134|8
185.247.225.61|8
209.127.17.242|8
198.96.155.3|8
185.31.175.243|8
185.31.175.247|8
205.185.126.71|8
221.181.185.111|8
139.59.144.149|8
107.189.31.248|8
199.19.226.61|8
159.223.24.19|8
68.183.180.46|8
185.31.175.207|8
185.31.175.213|8
185.31.175.215|8
