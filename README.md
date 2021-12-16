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
Wall of shame (2021-12-16)
----

|IP|Number of (black)lists|
|---|--:|
178.128.249.136|10
171.25.193.78|10
45.154.255.147|10
205.185.114.158|10
85.202.169.128|9
116.105.77.214|9
185.220.102.243|9
162.247.74.74|9
209.141.44.102|9
212.192.241.124|9
116.110.92.217|9
185.130.44.108|9
222.187.238.58|9
185.243.218.50|9
205.185.120.235|9
107.189.5.248|9
205.185.120.71|9
38.91.102.77|9
171.25.193.25|9
64.113.32.29|9
199.195.250.77|9
179.43.187.37|9
161.35.201.142|9
62.102.148.69|9
209.141.47.245|9
221.181.185.111|9
209.141.53.74|9
164.90.203.55|8
205.185.124.219|8
89.234.157.254|8
205.185.115.39|8
38.91.102.46|8
211.22.65.18|8
188.166.24.204|8
141.98.10.63|8
104.248.85.104|8
5.2.69.50|8
205.185.114.149|8
171.25.193.77|8
185.220.101.187|8
185.14.97.147|8
51.15.43.205|8
165.22.195.82|8
178.20.55.18|8
178.20.55.16|8
107.189.30.23|8
185.42.170.203|8
165.22.205.114|8
185.220.100.253|8
185.220.100.255|8
185.220.100.254|8
176.10.99.200|8
192.42.116.13|8
166.70.207.2|8
116.105.26.187|8
89.163.249.244|8
185.220.102.4|8
199.249.230.119|8
60.170.247.162|8
116.110.19.131|8
5.2.72.124|8
162.247.74.217|8
107.189.28.100|8
45.88.188.13|8
195.133.18.24|8
134.209.83.158|8
167.71.10.210|8
213.202.216.189|8
2.56.59.114|8
185.220.102.253|8
80.67.172.162|8
185.165.171.175|8
185.56.80.65|8
72.167.48.55|8
209.141.34.220|8
162.240.28.64|8
161.35.205.46|8
185.129.61.1|8
45.153.160.133|8
185.220.100.247|8
45.144.225.188|8
162.247.72.199|8
117.248.249.70|8
167.172.43.16|8
107.189.30.134|8
