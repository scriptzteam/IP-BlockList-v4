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
Wall of shame (2021-11-30)
----

|IP|Number of (black)lists|
|---|--:|
185.220.100.252|10
45.88.137.253|10
212.192.241.37|10
141.98.10.246|10
171.25.193.20|10
209.141.34.220|10
209.141.62.233|10
185.31.175.215|10
185.31.175.226|9
185.31.175.220|9
205.185.115.39|9
185.220.102.244|9
205.185.114.87|9
171.25.193.77|9
185.220.101.1|9
45.153.160.2|9
178.20.55.18|9
212.192.241.124|9
185.220.100.254|9
185.31.175.252|9
185.31.175.213|9
222.187.238.58|9
23.183.82.135|9
205.185.120.71|9
116.105.217.54|9
36.110.228.254|9
171.25.193.25|9
209.141.33.121|9
221.131.165.75|9
213.202.216.189|9
209.141.53.74|9
80.67.172.162|9
64.113.32.29|9
221.131.165.50|9
195.133.18.210|9
209.141.32.141|9
185.220.102.245|9
23.183.82.180|9
45.153.160.139|9
221.181.185.111|9
163.172.213.212|9
167.172.43.16|9
89.163.252.230|8
80.82.77.33|8
162.247.74.206|8
23.183.81.249|8
167.71.12.34|8
5.183.209.217|8
23.129.64.130|8
167.71.77.225|8
136.144.41.139|8
185.220.102.241|8
185.220.102.243|8
185.220.102.248|8
162.247.74.74|8
199.195.249.152|8
205.185.114.149|8
136.144.41.3|8
167.71.2.44|8
171.25.193.78|8
164.92.242.66|8
23.183.81.136|8
185.220.101.4|8
81.17.18.62|8
31.210.20.110|8
209.141.33.193|8
185.220.100.255|8
83.149.87.180|8
176.10.99.200|8
185.100.87.72|8
94.230.208.147|8
185.220.102.4|8
185.130.44.108|8
38.91.102.36|8
38.91.102.38|8
198.144.121.93|8
107.189.8.254|8
45.153.160.140|8
107.189.30.85|8
185.243.218.50|8
185.31.175.231|8
23.183.82.117|8
38.91.102.77|8
221.131.165.33|8
162.247.74.217|8
209.141.44.68|8
195.133.18.24|8
198.98.48.103|8
199.195.252.18|8
185.38.175.132|8
2.56.59.114|8
185.220.102.254|8
185.220.102.253|8
104.244.73.169|8
116.110.252.176|8
23.154.177.2|8
164.92.250.114|8
179.43.187.37|8
185.100.87.129|8
209.141.55.43|8
104.244.76.13|8
185.31.175.207|8
23.183.81.54|8
45.153.160.133|8
45.153.160.132|8
45.88.137.100|8
209.141.47.245|8
185.31.175.243|8
209.141.52.25|8
209.141.62.185|8
116.110.156.69|8
134.209.95.47|8
23.183.81.227|8
117.248.249.70|8
162.247.73.192|8
221.10.33.104|8
37.123.163.58|8
164.92.252.236|8
