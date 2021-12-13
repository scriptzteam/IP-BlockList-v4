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
Wall of shame (2021-12-13)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.78|10
45.88.188.13|10
205.185.115.39|9
38.91.102.46|9
107.189.1.167|9
104.248.85.104|9
45.153.160.129|9
45.88.137.253|9
185.130.44.108|9
45.153.160.140|9
205.185.120.71|9
38.91.102.77|9
171.25.193.25|9
205.185.114.158|9
64.113.32.29|9
221.131.165.50|9
161.35.201.142|9
45.153.160.133|9
209.141.47.245|9
134.209.95.47|9
80.82.77.33|8
134.209.198.229|8
164.90.203.55|8
58.222.83.94|8
5.183.209.217|8
89.234.157.254|8
85.202.169.128|8
23.129.64.130|8
116.105.77.214|8
185.107.47.215|8
89.163.249.192|8
185.220.102.244|8
185.220.102.242|8
185.220.102.243|8
185.220.102.249|8
162.247.74.74|8
188.166.24.204|8
141.98.10.63|8
167.99.223.124|8
205.185.114.149|8
171.25.193.77|8
185.107.47.171|8
185.220.101.4|8
185.220.101.189|8
185.220.101.185|8
134.209.195.231|8
185.14.97.147|8
212.192.241.95|8
45.154.255.147|8
134.209.205.40|8
107.189.14.215|8
45.61.187.203|8
178.20.55.18|8
178.20.55.16|8
162.247.72.199|8
212.192.241.124|8
185.220.100.253|8
185.220.100.254|8
209.141.44.102|8
185.100.87.72|8
166.70.207.2|8
89.163.249.244|8
185.220.102.4|8
199.249.230.119|8
212.192.241.37|8
209.141.34.220|8
89.163.243.88|8
222.187.238.58|8
185.243.218.50|8
205.185.120.235|8
94.232.46.202|8
116.110.19.131|8
5.2.72.124|8
45.153.160.2|8
185.100.86.74|8
195.133.18.24|8
176.10.104.240|8
167.71.10.210|8
45.61.184.103|8
185.38.175.132|8
213.202.216.189|8
80.67.172.162|8
23.154.177.2|8
107.189.30.23|8
51.255.106.85|8
179.43.187.37|8
89.163.154.91|8
185.56.80.65|8
62.102.148.69|8
161.35.205.46|8
185.129.61.2|8
45.153.160.136|8
81.17.18.59|8
45.88.137.100|8
45.144.225.188|8
221.181.185.111|8
107.189.12.169|8
185.220.101.149|8
185.220.101.143|8
167.172.43.16|8
107.189.30.134|8
209.141.53.74|8
104.244.72.168|8
185.100.87.202|8
107.189.8.65|8
