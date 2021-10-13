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
Wall of shame (2021-10-13)
----

|IP|Number of (black)lists|
|---|--:|
185.31.175.207|11
165.22.100.49|10
141.98.10.60|10
205.185.121.149|10
199.19.224.76|10
179.43.141.99|10
198.98.48.67|10
209.141.53.99|10
185.73.124.253|10
171.25.193.20|10
198.98.52.12|10
199.195.253.199|10
141.98.10.81|10
141.98.10.82|10
185.31.175.228|9
185.31.175.226|9
185.73.124.100|9
185.220.102.244|9
185.220.102.243|9
198.98.54.17|9
221.131.165.65|9
209.141.40.193|9
60.8.87.190|9
212.193.30.32|9
221.181.185.94|9
205.185.124.141|9
141.98.10.121|9
209.141.54.35|9
185.31.175.235|9
185.31.175.231|9
179.43.175.26|9
221.131.165.33|9
222.187.238.58|9
209.141.47.39|9
212.193.30.84|9
212.193.30.101|9
221.131.165.75|9
80.67.172.162|9
209.141.55.232|9
221.131.165.50|9
199.19.226.4|9
185.31.175.215|9
106.12.155.22|9
222.187.232.39|9
212.193.30.64|9
199.195.251.49|9
185.31.175.243|9
117.248.249.70|9
107.189.30.134|9
185.31.175.220|8
46.101.149.29|8
107.189.12.107|8
5.183.209.217|8
89.163.249.244|8
89.234.157.254|8
176.111.173.238|8
95.172.47.98|8
199.195.252.242|8
185.220.102.242|8
185.220.102.248|8
205.185.127.160|8
5.2.69.50|8
209.141.51.168|8
206.189.6.143|8
171.25.193.77|8
171.25.193.78|8
185.107.47.171|8
185.220.101.1|8
185.247.225.55|8
185.220.101.42|8
80.82.77.139|8
162.247.72.199|8
185.42.170.203|8
54.36.108.162|8
185.220.100.253|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
185.90.136.69|8
185.100.87.72|8
107.189.31.248|8
185.220.102.4|8
198.98.52.98|8
198.144.121.93|8
77.247.181.165|8
77.247.181.163|8
185.31.175.213|8
45.135.232.159|8
93.174.95.106|8
91.219.236.228|8
178.73.215.171|8
209.141.55.247|8
198.98.49.124|8
171.25.193.25|8
195.133.18.116|8
178.62.212.82|8
185.220.102.253|8
185.220.102.250|8
8.209.91.186|8
136.144.41.253|8
199.195.250.77|8
185.56.80.65|8
116.110.124.53|8
105.203.195.68|8
176.10.99.200|8
185.220.102.245|8
45.153.160.132|8
199.195.248.44|8
205.185.113.224|8
