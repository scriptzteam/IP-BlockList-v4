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
Wall of shame (2021-12-14)
----

|IP|Number of (black)lists|
|---|--:|
178.128.249.136|10
171.25.193.78|10
45.153.160.140|10
134.209.198.229|9
205.185.115.39|9
116.105.77.214|9
134.209.195.231|9
178.20.55.16|9
212.192.241.124|9
185.220.100.254|9
209.141.44.102|9
209.141.34.220|9
222.187.238.58|9
205.185.120.235|9
205.185.120.71|9
38.91.102.77|9
5.2.72.124|9
171.25.193.25|9
45.88.188.13|9
167.71.10.210|9
80.67.172.162|9
205.185.114.158|9
221.131.165.50|9
199.195.250.77|9
179.43.187.37|9
161.35.201.142|9
221.181.185.111|9
134.209.95.47|9
164.90.203.55|8
199.249.230.163|8
205.185.124.219|8
58.222.83.94|8
89.234.157.254|8
23.129.64.130|8
188.214.104.146|8
209.141.47.245|8
185.107.47.215|8
38.91.102.46|8
185.220.102.244|8
162.247.74.74|8
107.189.1.160|8
211.22.65.18|8
188.166.24.204|8
109.201.133.100|8
141.98.10.63|8
104.248.85.104|8
205.185.114.149|8
171.25.193.77|8
185.220.101.4|8
45.154.255.147|8
185.220.101.46|8
134.209.205.40|8
185.170.114.25|8
178.20.55.18|8
81.17.18.61|8
81.17.18.62|8
209.141.48.248|8
165.22.205.114|8
116.110.92.217|8
185.220.100.252|8
185.220.100.255|8
195.254.135.76|8
192.42.116.14|8
166.70.207.2|8
5.183.209.217|8
45.88.137.253|8
185.220.102.4|8
185.220.102.8|8
185.130.44.108|8
199.249.230.119|8
93.123.93.104|8
23.129.64.146|8
185.243.218.50|8
162.247.74.27|8
107.189.5.248|8
93.174.95.106|8
94.232.46.202|8
162.247.74.216|8
58.37.145.160|8
185.100.86.74|8
171.25.193.20|8
107.189.12.47|8
213.202.216.189|8
185.220.102.254|8
185.220.102.253|8
185.220.102.251|8
185.220.102.250|8
209.141.53.74|8
45.13.104.179|8
64.113.32.29|8
185.165.171.175|8
89.163.154.91|8
185.56.80.65|8
23.129.64.143|8
185.220.101.190|8
62.102.148.69|8
161.35.205.46|8
185.129.61.2|8
176.10.99.200|8
45.153.160.133|8
45.153.160.131|8
81.17.18.59|8
45.88.137.100|8
45.144.225.188|8
107.189.1.167|8
117.248.249.70|8
107.189.12.169|8
167.172.43.16|8
107.189.30.134|8
185.100.87.202|8
