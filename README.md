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
Wall of shame (2021-11-08)
----

|IP|Number of (black)lists|
|---|--:|
205.185.115.39|10
171.25.193.20|10
205.185.120.180|10
45.153.160.135|10
185.31.175.240|10
141.98.10.82|10
199.19.225.198|9
199.19.224.231|9
185.220.102.240|9
141.98.10.60|9
171.25.193.77|9
185.220.101.4|9
45.88.137.253|9
38.91.102.38|9
185.31.175.231|9
171.25.193.25|9
209.141.33.121|9
141.98.10.72|9
80.67.172.162|9
136.144.41.253|9
2.56.59.39|9
45.153.160.133|9
185.31.175.247|9
185.31.175.215|9
107.189.30.134|9
116.110.223.93|8
185.31.175.228|8
185.31.175.226|8
185.31.175.220|8
80.82.77.33|8
162.247.74.200|8
89.234.157.254|8
193.142.146.242|8
176.111.173.237|8
185.220.102.244|8
185.220.102.243|8
162.247.74.74|8
211.22.65.18|8
141.98.10.63|8
221.131.165.62|8
5.2.69.50|8
45.124.84.250|8
221.131.165.72|8
45.153.160.2|8
80.82.77.139|8
5.199.143.202|8
195.133.18.210|8
162.247.72.199|8
45.153.160.129|8
185.220.100.255|8
141.98.10.121|8
185.31.175.252|8
185.100.87.72|8
209.141.41.103|8
166.70.207.2|8
185.220.102.4|8
198.144.121.93|8
45.153.160.140|8
94.232.46.202|8
206.189.144.184|8
198.98.49.124|8
148.72.247.147|8
221.131.165.75|8
8.209.91.186|8
64.113.32.29|8
221.131.165.50|8
104.244.76.13|8
185.56.80.65|8
62.102.148.69|8
185.31.175.207|8
117.7.122.163|8
45.88.137.100|8
185.31.175.243|8
221.181.185.111|8
162.247.74.27|8
209.141.59.184|8
163.172.213.212|8
