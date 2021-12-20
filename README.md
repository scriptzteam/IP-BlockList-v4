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
Wall of shame (2021-12-20)
----

|IP|Number of (black)lists|
|---|--:|
162.247.74.74|10
171.25.193.25|10
64.113.32.29|10
185.220.102.243|9
185.220.102.249|9
5.2.69.50|9
171.25.193.77|9
185.107.47.171|9
45.153.160.2|9
81.17.18.62|9
45.153.160.129|9
185.220.100.254|9
209.141.44.102|9
185.100.87.72|9
205.185.120.235|9
205.185.120.71|9
45.88.188.13|9
222.187.238.58|9
195.133.18.24|9
185.38.175.132|9
185.220.102.254|9
185.220.102.250|9
45.13.104.179|9
163.172.213.212|9
185.56.80.65|9
161.35.205.46|9
176.10.99.200|9
185.220.102.245|9
45.153.160.138|9
221.181.185.111|9
37.123.163.58|9
164.90.203.55|8
58.222.83.94|8
5.183.209.217|8
198.98.57.207|8
89.234.157.254|8
85.202.169.128|8
185.215.167.218|8
209.141.59.176|8
205.185.115.39|8
185.107.47.215|8
38.91.102.46|8
5.183.209.135|8
185.220.102.244|8
185.220.102.240|8
185.220.102.248|8
107.189.1.167|8
2.58.149.49|8
205.185.114.149|8
171.25.193.78|8
185.220.101.1|8
51.15.43.205|8
45.61.187.203|8
178.20.55.18|8
178.20.55.16|8
5.199.143.202|8
81.17.18.61|8
212.192.241.124|8
165.22.205.114|8
185.220.100.252|8
185.220.100.255|8
178.128.249.136|8
89.163.249.244|8
195.254.135.76|8
104.244.78.168|8
167.99.36.169|8
192.42.116.16|8
192.42.116.13|8
213.164.206.127|8
166.70.207.2|8
185.220.102.4|8
185.220.102.8|8
185.130.44.108|8
89.163.243.88|8
185.243.218.50|8
185.220.103.5|8
38.91.102.77|8
221.131.165.33|8
107.189.31.156|8
185.100.86.74|8
171.25.193.20|8
134.209.83.158|8
209.141.47.245|8
213.202.216.189|8
185.220.102.253|8
165.22.195.82|8
209.141.53.74|8
80.67.172.162|8
205.185.114.158|8
221.131.165.50|8
209.141.59.5|8
179.43.187.37|8
89.163.154.91|8
209.141.34.220|8
162.240.28.64|8
161.35.201.142|8
205.185.124.178|8
62.102.148.69|8
221.181.185.159|8
199.195.254.81|8
185.129.61.1|8
45.153.160.133|8
45.153.160.130|8
45.153.160.137|8
81.17.18.58|8
162.247.72.199|8
104.244.78.62|8
167.172.43.16|8
46.166.139.111|8
185.220.101.129|8
