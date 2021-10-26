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
Wall of shame (2021-10-26)
----

|IP|Number of (black)lists|
|---|--:|
165.22.100.49|10
209.141.40.193|10
209.141.53.99|10
185.73.124.253|10
199.195.253.199|10
185.56.80.65|10
141.98.10.82|10
141.98.10.60|10
185.31.175.228|9
5.183.209.217|9
185.73.124.100|9
185.220.102.244|9
162.247.74.74|9
198.98.54.17|9
221.131.165.65|9
5.2.69.50|9
171.25.193.78|9
18.27.197.252|9
212.193.30.32|9
167.88.161.219|9
45.153.160.129|9
141.98.10.121|9
199.19.224.76|9
205.185.116.163|9
198.98.48.67|9
60.170.247.162|9
185.31.175.231|9
221.131.165.33|9
209.141.56.75|9
222.187.238.58|9
95.172.47.98|9
209.141.33.121|9
45.61.185.168|9
212.193.30.101|9
198.98.52.12|9
221.131.165.75|9
185.38.175.132|9
185.220.102.253|9
80.67.172.162|9
209.141.55.232|9
221.131.165.50|9
209.141.59.9|9
185.129.62.62|9
45.153.160.131|9
221.181.185.111|9
139.59.144.149|9
141.98.10.81|9
209.141.59.184|9
68.183.180.46|9
199.195.251.49|9
116.110.223.93|8
185.31.175.220|8
199.195.248.175|8
162.247.74.200|8
162.247.74.206|8
89.234.157.254|8
199.19.226.61|8
104.244.77.37|8
185.220.102.246|8
185.220.102.243|8
221.131.165.62|8
164.52.24.164|8
116.105.30.143|8
171.25.193.77|8
80.82.77.139|8
81.17.18.61|8
202.29.214.13|8
185.220.100.252|8
198.96.155.3|8
185.100.87.72|8
198.144.121.93|8
45.153.160.140|8
107.189.13.219|8
179.43.175.26|8
117.68.2.93|8
162.247.74.213|8
171.25.193.20|8
198.98.49.124|8
185.100.86.74|8
171.25.193.25|8
209.141.47.39|8
209.141.40.64|8
195.133.18.116|8
209.141.59.77|8
221.131.165.72|8
185.220.102.251|8
185.220.102.250|8
64.113.32.29|8
205.185.120.183|8
209.127.17.234|8
89.163.252.12|8
209.141.36.13|8
45.153.160.137|8
45.153.160.135|8
45.153.160.134|8
199.195.253.210|8
192.42.116.27|8
209.141.49.147|8
185.31.175.243|8
45.153.160.136|8
45.153.160.2|8
159.223.24.19|8
37.123.163.58|8
163.172.213.212|8
209.127.17.242|8
159.65.52.117|8
185.100.87.202|8
