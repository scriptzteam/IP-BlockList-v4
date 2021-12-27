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
Wall of shame (2021-12-27)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.250|10
80.67.172.162|10
23.154.177.6|10
45.153.160.133|10
81.17.18.58|10
185.220.100.254|9
185.215.167.218|9
205.185.120.235|9
185.220.102.244|9
185.220.102.246|9
185.220.102.243|9
185.220.102.249|9
23.236.146.162|9
221.131.165.65|9
5.2.69.50|9
171.25.193.77|9
171.25.193.78|9
185.14.97.147|9
185.191.127.212|9
185.42.170.203|9
107.189.6.166|9
185.220.100.252|9
89.163.249.244|9
167.99.36.169|9
185.100.87.72|9
198.98.56.60|9
185.56.80.65|9
38.91.102.77|9
222.187.238.58|9
195.133.18.24|9
213.202.216.189|9
185.220.102.254|9
185.220.102.253|9
45.13.104.179|9
64.113.32.29|9
164.90.230.201|9
185.129.61.6|9
185.220.102.245|9
45.153.160.131|9
45.153.160.130|9
45.153.160.136|9
107.189.1.167|9
221.181.185.111|9
185.165.171.175|9
89.163.252.230|8
165.232.94.245|8
107.189.11.153|8
167.99.41.232|8
58.222.83.94|8
5.183.209.217|8
165.232.84.254|8
165.232.84.252|8
89.163.249.192|8
162.247.74.27|8
5.183.209.136|8
107.189.6.61|8
185.220.102.247|8
185.220.102.240|8
185.220.102.248|8
195.133.18.104|8
171.25.193.20|8
23.183.82.153|8
185.191.127.231|8
45.153.160.2|8
107.189.14.27|8
104.244.77.122|8
221.181.185.94|8
185.170.114.25|8
104.244.72.132|8
81.17.18.61|8
81.17.18.62|8
212.192.241.124|8
198.98.56.248|8
104.244.78.183|8
116.110.92.217|8
185.220.100.253|8
185.220.100.255|8
137.184.49.249|8
176.10.99.200|8
107.189.5.5|8
185.165.168.229|8
104.244.79.234|8
192.42.116.16|8
68.183.9.117|8
185.220.102.4|8
89.234.157.254|8
185.130.44.108|8
107.189.5.68|8
165.232.94.237|8
45.153.160.140|8
60.170.247.162|8
104.244.77.101|8
162.247.74.217|8
107.189.28.100|8
107.189.28.102|8
107.189.31.156|8
5.2.72.73|8
134.209.83.158|8
165.232.92.17|8
199.195.252.18|8
185.38.175.131|8
185.38.175.132|8
185.220.102.251|8
221.131.165.50|8
23.154.177.2|8
179.43.187.36|8
179.43.187.37|8
121.134.173.39|8
89.163.154.91|8
163.172.213.212|8
89.163.252.30|8
62.102.148.69|8
171.252.186.42|8
104.244.76.13|8
209.141.58.146|8
45.153.160.135|8
45.153.160.134|8
45.153.160.138|8
107.189.1.90|8
185.220.100.241|8
185.220.101.12|8
81.17.18.59|8
192.42.116.20|8
192.42.116.27|8
192.42.116.24|8
141.98.11.16|8
37.123.163.58|8
185.220.101.148|8
167.172.43.16|8
104.244.72.7|8
212.192.246.95|8
