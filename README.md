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
Wall of shame (2021-12-26)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.246|10
185.220.102.248|10
171.25.193.77|10
89.163.249.244|10
185.100.87.72|10
38.91.102.77|10
45.13.104.179|10
45.153.160.133|10
45.153.160.130|10
81.17.18.58|10
89.163.252.230|9
107.189.11.153|9
185.220.100.254|9
185.117.215.9|9
5.183.209.217|9
38.91.102.46|9
162.247.74.27|9
80.67.172.162|9
185.220.102.249|9
162.247.74.74|9
5.2.69.50|9
185.191.127.231|9
167.99.36.169|9
221.181.185.94|9
45.153.160.129|9
185.220.100.252|9
185.220.100.255|9
192.42.116.16|9
185.130.44.108|9
185.56.80.65|9
45.153.160.140|9
185.243.218.50|9
205.185.120.235|9
45.88.188.13|9
222.187.238.58|9
5.2.72.73|9
185.38.175.132|9
185.220.102.250|9
221.131.165.50|9
23.154.177.6|9
163.172.213.212|9
209.141.47.131|9
45.153.160.136|9
167.172.43.16|9
134.209.20.123|8
128.31.0.13|8
107.189.10.237|8
167.99.41.232|8
58.222.83.94|8
89.234.157.254|8
185.215.167.218|8
89.163.249.192|8
107.189.6.61|8
185.220.102.244|8
185.220.102.240|8
195.133.18.104|8
221.131.165.65|8
164.52.24.164|8
38.91.102.84|8
171.25.193.78|8
51.15.43.205|8
185.191.127.212|8
80.82.77.139|8
23.154.177.4|8
165.22.195.82|8
104.244.72.132|8
45.61.187.203|8
81.17.18.62|8
212.192.241.124|8
116.110.92.217|8
107.189.7.88|8
192.42.116.14|8
213.164.206.127|8
198.98.59.49|8
45.88.137.253|8
185.220.102.8|8
91.219.236.197|8
60.170.247.162|8
107.189.5.248|8
185.220.103.7|8
185.220.102.4|8
116.110.19.131|8
36.110.228.254|8
185.220.101.176|8
45.153.160.2|8
58.37.145.160|8
185.100.86.74|8
171.25.193.25|8
195.133.18.24|8
134.209.83.158|8
141.98.10.202|8
165.232.92.17|8
104.244.73.93|8
213.202.216.189|8
185.220.102.254|8
185.220.102.253|8
185.220.102.252|8
185.67.82.114|8
198.144.121.43|8
104.244.73.205|8
64.113.32.29|8
199.195.250.77|8
107.189.30.23|8
185.165.171.175|8
179.43.187.37|8
121.134.173.39|8
89.163.154.91|8
45.129.56.200|8
185.191.127.213|8
62.102.148.69|8
104.244.76.13|8
185.129.61.6|8
176.10.99.200|8
209.141.58.146|8
185.220.102.245|8
45.153.160.135|8
45.153.160.134|8
45.153.160.139|8
45.153.160.138|8
185.220.100.242|8
45.88.137.100|8
162.247.72.199|8
192.42.116.20|8
192.42.116.27|8
192.42.116.25|8
107.189.1.167|8
185.220.103.118|8
221.181.185.111|8
141.98.11.16|8
37.123.163.58|8
185.220.101.149|8
