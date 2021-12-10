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
185.31.175.226|10
185.220.102.243|10
171.25.193.78|10
45.88.137.253|10
205.185.120.71|10
185.31.175.215|10
185.31.175.220|9
116.110.92.217|9
136.144.41.139|9
162.247.74.206|9
134.209.198.229|9
205.185.115.39|9
116.105.77.214|9
185.220.102.248|9
141.98.10.63|9
205.185.114.149|9
171.25.193.77|9
134.209.195.231|9
134.209.205.40|9
185.220.100.254|9
212.192.241.37|9
222.187.238.58|9
141.98.10.246|9
185.243.218.50|9
185.31.175.231|9
116.110.19.131|9
162.247.74.217|9
171.25.193.25|9
171.25.193.20|9
195.133.18.24|9
221.131.165.75|9
185.220.102.250|9
80.67.172.162|9
64.113.32.29|9
221.131.165.50|9
199.195.250.77|9
185.165.171.175|9
179.43.187.37|9
209.141.34.220|9
185.100.87.129|9
45.153.160.131|9
185.31.175.196|9
209.141.47.245|9
185.31.175.247|9
167.172.43.16|9
209.141.53.74|9
89.163.252.230|8
185.31.175.228|8
80.82.77.33|8
107.189.11.153|8
199.249.230.163|8
23.183.81.249|8
89.234.157.254|8
38.91.102.46|8
185.220.102.244|8
185.220.102.246|8
185.220.102.247|8
185.220.102.241|8
185.220.102.249|8
162.247.74.74|8
211.22.65.18|8
104.248.85.104|8
185.83.214.69|8
5.2.69.50|8
185.107.47.171|8
116.235.94.247|8
23.183.81.136|8
212.192.241.95|8
45.154.255.147|8
185.220.101.46|8
23.183.81.116|8
165.22.195.82|8
178.20.55.18|8
178.20.55.16|8
185.220.101.4|8
81.17.18.61|8
212.192.241.124|8
185.42.170.203|8
45.153.160.129|8
185.220.100.253|8
185.220.100.252|8
137.184.49.249|8
195.254.135.76|8
198.96.155.3|8
185.31.175.252|8
185.100.87.72|8
185.220.102.4|8
185.130.44.108|8
23.183.81.227|8
45.153.160.140|8
185.31.175.213|8
89.163.243.88|8
23.183.82.135|8
93.174.95.106|8
94.232.46.202|8
38.91.102.77|8
45.153.160.2|8
45.88.188.13|8
185.100.86.74|8
95.128.43.164|8
167.71.10.210|8
141.98.10.202|8
185.38.175.132|8
185.220.102.254|8
185.220.102.253|8
185.67.82.114|8
45.13.104.179|8
163.172.213.212|8
185.56.80.65|8
72.167.48.55|8
89.163.252.30|8
104.244.76.13|8
185.31.175.207|8
185.31.175.188|8
185.129.61.1|8
176.10.99.200|8
23.183.81.54|8
185.220.102.245|8
45.153.160.134|8
107.189.1.90|8
185.220.100.241|8
45.88.137.100|8
162.247.72.199|8
185.31.175.243|8
23.183.82.180|8
221.181.185.111|8
134.209.95.47|8
37.123.163.58|8
94.153.161.234|8
185.100.87.202|8
