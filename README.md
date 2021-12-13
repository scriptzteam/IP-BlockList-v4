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
171.25.193.78|11
162.247.74.74|10
45.88.137.253|10
185.130.44.108|10
45.153.160.140|10
171.25.193.25|10
45.153.160.133|10
85.202.169.128|9
205.185.115.39|9
185.107.47.215|9
38.91.102.46|9
185.220.102.244|9
185.220.102.248|9
104.248.85.104|9
5.2.69.50|9
171.25.193.77|9
134.209.195.231|9
45.154.255.147|9
185.220.100.254|9
209.141.44.102|9
222.187.238.58|9
185.243.218.50|9
205.185.120.71|9
38.91.102.77|9
45.153.160.2|9
45.88.188.13|9
171.25.193.20|9
195.133.18.24|9
185.220.102.250|9
205.185.114.158|9
64.113.32.29|9
221.131.165.50|9
107.189.30.23|9
163.172.213.212|9
161.35.201.142|9
161.35.205.46|9
45.153.160.136|9
209.141.47.245|9
162.247.72.199|9
107.189.1.167|9
221.181.185.111|9
134.209.95.47|9
185.220.101.149|9
185.220.101.143|9
167.172.43.16|9
107.189.30.134|9
107.189.8.65|9
107.189.10.137|8
80.82.77.33|8
134.209.198.229|8
164.90.203.55|8
58.222.83.94|8
89.234.157.254|8
23.129.64.130|8
116.105.77.214|8
82.221.131.5|8
89.163.249.192|8
161.35.153.160|8
5.183.209.134|8
185.220.102.247|8
185.220.102.242|8
185.220.102.243|8
185.220.102.249|8
211.22.65.18|8
188.166.24.204|8
141.98.10.63|8
205.185.114.149|8
185.107.47.171|8
185.220.101.4|8
185.220.101.189|8
185.220.101.185|8
185.220.101.187|8
185.14.97.147|8
212.192.241.95|8
134.209.205.40|8
107.189.14.215|8
165.22.195.82|8
45.61.187.203|8
178.20.55.18|8
178.20.55.16|8
81.17.18.61|8
81.17.18.62|8
212.192.241.124|8
45.153.160.129|8
185.220.100.253|8
185.220.100.255|8
176.10.99.200|8
104.244.78.168|8
185.100.87.72|8
192.42.116.16|8
166.70.207.2|8
89.163.249.244|8
185.220.102.4|8
199.249.230.119|8
212.192.241.37|8
89.163.243.88|8
205.185.120.235|8
107.189.5.248|8
116.110.19.131|8
5.2.72.124|8
162.247.74.217|8
185.100.86.74|8
188.166.60.8|8
134.209.83.158|8
167.71.10.210|8
45.61.184.103|8
161.35.153.152|8
221.131.165.75|8
185.38.175.132|8
213.202.216.189|8
185.220.102.254|8
80.67.172.162|8
45.13.104.179|8
23.154.177.5|8
179.43.187.37|8
185.56.80.65|8
209.141.34.220|8
185.100.87.129|8
205.185.124.178|8
62.102.148.69|8
185.129.61.2|8
45.153.160.131|8
45.153.160.137|8
45.153.160.135|8
45.153.160.134|8
45.153.160.139|8
185.220.100.241|8
107.189.7.243|8
81.17.18.59|8
45.88.137.100|8
45.144.225.188|8
137.184.49.88|8
162.247.73.192|8
107.189.12.169|8
37.123.163.58|8
209.141.53.74|8
85.202.169.161|8
104.244.72.168|8
