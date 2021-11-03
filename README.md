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
Wall of shame (2021-11-03)
----

|IP|Number of (black)lists|
|---|--:|
141.98.10.63|10
141.98.10.60|10
5.189.168.79|10
171.25.193.20|10
171.25.193.25|10
80.67.172.162|10
141.98.10.82|10
199.195.248.175|9
199.249.230.163|9
5.183.209.217|9
162.247.74.74|9
198.98.54.17|9
5.2.69.50|9
171.25.193.77|9
171.25.193.78|9
141.98.10.121|9
136.144.41.253|9
192.42.116.16|9
198.144.121.93|9
45.153.160.140|9
64.113.32.29|9
209.141.55.232|9
2.56.59.39|9
185.56.80.65|9
104.244.76.13|9
209.127.17.234|9
117.7.122.163|9
141.98.10.81|9
209.141.59.184|9
68.183.180.46|9
116.110.223.93|8
128.31.0.13|8
80.82.77.33|8
205.185.115.19|8
71.6.199.23|8
185.107.47.215|8
89.163.249.192|8
104.244.77.37|8
185.220.102.240|8
185.220.102.248|8
64.227.126.252|8
221.131.165.62|8
185.107.47.171|8
185.220.101.4|8
185.220.101.1|8
195.144.21.219|8
221.131.165.72|8
80.82.77.139|8
221.181.185.111|8
209.127.17.242|8
45.153.160.129|8
54.36.108.162|8
185.220.100.253|8
185.220.100.255|8
205.185.126.71|8
185.100.87.72|8
94.230.208.147|8
166.70.207.2|8
209.141.54.35|8
162.247.74.27|8
104.244.72.120|8
198.98.49.124|8
185.73.124.253|8
209.141.33.121|8
45.61.185.168|8
221.131.165.75|8
167.88.161.219|8
185.220.102.253|8
185.220.102.250|8
8.209.91.186|8
221.131.165.50|8
209.141.41.31|8
209.141.42.29|8
205.185.120.183|8
45.153.160.138|8
176.10.99.200|8
185.220.102.245|8
185.220.102.241|8
45.153.160.135|8
106.244.10.2|8
141.98.10.109|8
161.35.49.227|8
45.153.160.139|8
139.59.144.149|8
159.223.24.19|8
37.123.163.58|8
185.100.87.202|8
