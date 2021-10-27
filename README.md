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
Wall of shame (2021-10-27)
----

|IP|Number of (black)lists|
|---|--:|
162.247.74.74|10
198.144.121.93|10
185.220.102.253|10
185.56.80.65|10
5.183.209.217|9
185.31.175.228|9
185.107.47.215|9
185.220.102.246|9
5.2.69.50|9
18.27.197.252|9
209.127.17.242|9
185.100.87.72|9
45.153.160.140|9
141.98.10.60|9
185.31.175.231|9
185.73.124.253|9
171.25.193.20|9
171.25.193.25|9
185.220.102.250|9
205.185.120.183|9
185.129.62.62|9
199.195.253.210|9
141.98.10.82|9
163.172.213.212|9
116.110.223.93|8
185.31.175.226|8
185.31.175.220|8
128.31.0.13|8
162.247.74.200|8
162.247.74.206|8
162.247.74.204|8
89.234.157.254|8
91.250.242.12|8
162.247.74.27|8
185.220.102.244|8
185.220.102.247|8
185.220.102.243|8
185.220.102.248|8
198.98.54.17|8
221.131.165.62|8
116.105.30.143|8
171.25.193.77|8
171.25.193.78|8
209.141.60.103|8
205.185.126.71|8
45.153.160.2|8
81.17.18.61|8
167.88.161.219|8
45.153.160.129|8
185.220.100.253|8
185.220.100.255|8
185.220.100.254|8
141.98.10.121|8
185.31.175.252|8
199.19.224.76|8
205.185.119.4|8
185.220.102.4|8
45.135.232.159|8
60.170.247.162|8
209.141.53.99|8
185.220.103.7|8
117.68.2.93|8
209.141.56.75|8
162.247.74.217|8
185.100.86.74|8
199.195.251.49|8
195.133.18.116|8
209.141.33.121|8
45.61.185.168|8
212.193.30.101|8
198.98.52.12|8
185.38.175.132|8
213.202.216.189|8
80.67.172.162|8
64.113.32.29|8
199.195.253.199|8
209.141.55.232|8
209.141.59.9|8
104.244.76.13|8
116.110.124.53|8
185.31.175.207|8
89.163.252.12|8
45.153.160.133|8
45.153.160.132|8
45.153.160.137|8
45.153.160.136|8
45.153.160.135|8
45.153.160.134|8
185.220.100.241|8
185.31.175.243|8
205.185.116.163|8
195.206.105.217|8
141.98.10.81|8
209.141.59.184|8
37.123.163.58|8
107.189.30.134|8
185.100.87.202|8
