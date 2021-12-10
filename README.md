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
Wall of shame (2021-12-10)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.77|10
134.209.195.231|10
205.185.120.71|10
171.25.193.20|10
136.144.41.139|9
134.209.198.229|9
205.185.115.39|9
141.98.10.63|9
205.185.114.149|9
171.25.193.78|9
116.235.94.247|9
134.209.205.40|9
45.88.137.253|9
185.130.44.108|9
222.187.238.58|9
141.98.10.246|9
171.25.193.25|9
195.133.18.24|9
221.131.165.75|9
80.67.172.162|9
64.113.32.29|9
221.131.165.50|9
179.43.187.37|9
185.100.87.129|9
209.141.47.245|9
185.31.175.215|9
167.172.43.16|9
209.141.53.74|9
185.31.175.226|8
116.110.92.217|8
128.31.0.13|8
80.82.77.33|8
162.247.74.206|8
23.183.81.249|8
89.234.157.254|8
116.105.77.214|8
185.107.47.215|8
185.220.102.243|8
185.220.102.248|8
162.247.74.74|8
211.22.65.18|8
104.248.85.104|8
185.220.101.187|8
23.183.81.136|8
185.31.175.240|8
185.220.101.46|8
212.192.241.124|8
192.160.102.170|8
185.220.100.253|8
185.220.100.254|8
176.10.99.200|8
192.42.116.16|8
166.70.207.2|8
23.183.81.227|8
45.153.160.140|8
212.192.241.37|8
89.163.243.88|8
23.183.82.135|8
23.129.64.146|8
93.174.95.106|8
94.232.46.202|8
185.220.102.6|8
116.110.19.131|8
38.91.102.77|8
162.247.74.217|8
45.88.188.13|8
167.71.10.210|8
141.98.10.202|8
45.61.184.103|8
45.13.104.179|8
199.195.250.77|8
163.172.213.212|8
72.167.48.55|8
209.141.34.220|8
23.183.81.54|8
185.220.102.245|8
45.153.160.139|8
185.31.175.247|8
23.183.82.180|8
221.181.185.111|8
134.209.95.47|8
107.189.30.134|8
