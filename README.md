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
Wall of shame (2021-12-21)
----

|IP|Number of (black)lists|
|---|--:|
185.215.167.218|10
89.163.249.244|10
205.185.120.235|10
205.185.120.71|10
64.113.32.29|10
5.183.209.217|9
89.234.157.254|9
85.202.169.128|9
185.220.102.244|9
185.220.102.246|9
2.58.149.49|9
171.25.193.77|9
171.25.193.78|9
221.181.185.94|9
185.170.114.25|9
178.20.55.18|9
178.20.55.16|9
81.17.18.61|9
81.17.18.62|9
209.141.54.195|9
221.181.185.111|9
185.220.100.254|9
185.100.87.72|9
185.220.102.4|9
185.130.44.108|9
45.153.160.140|9
209.141.34.220|9
162.247.74.217|9
45.153.160.2|9
171.25.193.25|9
171.25.193.20|9
209.141.47.245|9
213.202.216.189|9
185.220.102.254|9
185.220.102.250|9
209.141.53.74|9
80.67.172.162|9
45.13.104.179|9
221.131.165.50|9
185.165.171.175|9
185.56.80.65|9
161.35.201.142|9
161.35.205.46|9
176.10.99.200|9
45.153.160.133|9
45.153.160.130|9
45.153.160.139|9
81.17.18.58|9
37.123.163.58|9
222.187.238.58|9
167.172.43.16|9
107.189.10.137|8
107.189.30.111|8
164.90.203.55|8
167.99.41.232|8
58.222.83.94|8
205.185.115.39|8
116.105.77.214|8
185.107.47.215|8
185.220.102.240|8
185.220.102.243|8
162.247.74.74|8
188.166.24.204|8
5.2.69.50|8
205.185.114.149|8
185.191.127.231|8
2.56.59.21|8
212.192.241.163|8
185.191.127.212|8
45.61.187.203|8
5.199.143.202|8
185.220.101.4|8
162.247.72.199|8
212.192.241.124|8
165.22.205.114|8
116.110.92.217|8
185.220.100.253|8
185.220.100.255|8
178.128.249.136|8
192.42.116.13|8
166.70.207.2|8
45.88.137.253|8
185.220.102.8|8
60.170.247.162|8
162.247.74.27|8
107.189.5.248|8
116.110.19.131|8
38.91.102.77|8
221.131.165.33|8
207.244.70.35|8
45.88.188.13|8
107.189.31.156|8
58.37.145.160|8
185.100.86.74|8
5.2.72.73|8
195.133.18.24|8
134.209.83.158|8
185.38.175.132|8
185.220.102.253|8
185.220.102.252|8
185.220.102.251|8
165.22.195.82|8
199.195.250.77|8
23.154.177.6|8
179.43.187.37|8
89.163.154.91|8
209.141.47.131|8
62.102.148.68|8
185.220.102.245|8
45.153.160.132|8
45.153.160.131|8
45.153.160.137|8
45.153.160.136|8
45.153.160.134|8
46.182.21.248|8
185.220.100.242|8
81.17.18.59|8
45.88.137.100|8
209.141.62.185|8
185.220.101.149|8
104.244.78.62|8
163.172.213.212|8
185.220.101.129|8
