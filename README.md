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
Wall of shame (2021-12-22)
----

|IP|Number of (black)lists|
|---|--:|
221.181.185.111|10
185.220.102.253|10
185.220.102.250|10
64.113.32.29|10
5.183.209.217|9
185.215.167.218|9
205.185.115.39|9
185.220.102.244|9
185.220.102.246|9
185.220.102.248|9
221.131.165.65|9
5.2.69.50|9
171.25.193.78|9
221.181.185.94|9
81.17.18.62|9
89.163.249.244|9
166.70.207.2|9
185.130.44.108|9
185.56.80.65|9
185.243.218.50|9
205.185.120.235|9
45.153.160.2|9
171.25.193.25|9
45.88.188.13|9
222.187.238.58|9
171.25.193.20|9
195.133.18.24|9
185.38.175.132|9
209.141.53.74|9
45.13.104.179|9
221.131.165.50|9
209.141.34.220|9
176.10.99.200|9
45.153.160.130|9
45.153.160.135|9
107.189.1.167|9
198.98.51.189|9
37.123.163.58|9
167.172.43.16|9
134.209.20.123|8
107.189.30.111|8
164.90.203.55|8
167.99.41.232|8
185.220.100.254|8
89.234.157.254|8
185.107.47.215|8
185.220.102.247|8
185.220.102.243|8
162.247.74.74|8
195.133.18.104|8
23.236.146.162|8
38.91.102.84|8
185.220.101.188|8
185.14.97.147|8
80.82.77.139|8
165.22.195.82|8
185.220.101.4|8
45.153.160.129|8
185.220.100.253|8
185.220.100.252|8
185.220.100.255|8
178.128.249.136|8
195.254.135.76|8
104.244.78.168|8
185.100.87.72|8
192.42.116.16|8
185.220.102.4|8
185.220.102.8|8
176.10.104.240|8
185.220.101.134|8
162.247.74.27|8
205.185.120.71|8
38.91.102.77|8
107.189.28.100|8
185.100.86.74|8
209.141.47.245|8
221.131.165.75|8
213.202.216.189|8
185.220.102.254|8
198.144.121.43|8
80.67.172.162|8
23.154.177.6|8
23.154.177.5|8
45.129.56.200|8
163.172.213.212|8
209.141.47.131|8
161.35.201.142|8
89.163.252.30|8
161.35.205.46|8
185.129.61.1|8
45.153.160.133|8
45.153.160.136|8
45.153.160.134|8
45.153.160.138|8
185.220.100.242|8
185.220.100.241|8
192.42.116.23|8
209.141.62.185|8
185.100.87.202|8
