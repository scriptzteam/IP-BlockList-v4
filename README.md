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
Wall of shame (2021-12-05)
----

|IP|Number of (black)lists|
|---|--:|
45.153.160.2|10
45.153.160.140|10
141.98.10.246|10
171.25.193.25|10
80.67.172.162|10
163.172.213.212|10
185.31.175.226|9
185.31.175.220|9
23.183.81.249|9
5.183.209.217|9
89.234.157.254|9
185.31.175.252|9
176.111.173.237|9
185.220.102.244|9
185.220.102.246|9
185.220.102.248|9
205.185.122.230|9
141.98.10.63|9
171.25.193.77|9
23.183.81.136|9
212.192.241.95|9
212.192.241.124|9
185.220.100.254|9
185.100.87.72|9
192.42.116.16|9
45.88.137.253|9
185.220.102.4|9
212.192.241.37|9
222.187.238.58|9
205.185.120.71|9
116.105.217.54|9
221.131.165.33|9
185.100.86.74|9
171.25.193.20|9
221.131.165.75|9
2.56.59.114|9
185.220.102.253|9
185.220.102.251|9
185.220.102.250|9
64.113.32.29|9
116.110.252.176|9
209.141.32.141|9
185.56.80.65|9
209.141.34.220|9
185.100.87.129|9
209.127.17.234|9
23.183.81.54|9
209.141.47.245|9
23.183.82.180|9
221.181.185.111|9
209.141.62.185|9
134.209.95.47|9
185.31.175.215|9
167.172.43.16|9
185.100.87.202|9
80.82.77.33|8
162.247.74.200|8
162.247.74.206|8
134.209.198.229|8
205.185.115.39|8
209.141.41.46|8
185.107.47.215|8
89.163.249.192|8
185.220.102.241|8
185.220.102.243|8
69.49.244.54|8
162.247.74.74|8
104.248.85.104|8
5.2.69.50|8
167.99.223.124|8
205.185.114.149|8
171.25.193.78|8
185.107.47.171|8
185.220.101.1|8
185.31.175.247|8
18.27.197.252|8
45.154.255.147|8
134.209.205.40|8
23.183.81.116|8
165.22.195.82|8
178.20.55.18|8
81.17.18.62|8
209.141.54.195|8
162.247.72.199|8
209.141.48.248|8
209.141.33.193|8
116.110.96.81|8
45.153.160.129|8
185.220.100.253|8
185.220.100.255|8
137.184.49.249|8
89.163.249.244|8
166.70.207.2|8
185.220.102.8|8
185.130.44.108|8
199.249.230.119|8
185.31.175.213|8
89.163.243.88|8
23.183.82.135|8
107.189.5.248|8
185.220.103.8|8
185.220.102.6|8
185.31.175.235|8
185.31.175.231|8
162.247.74.217|8
207.244.70.35|8
195.133.18.24|8
188.166.60.8|8
209.141.33.121|8
185.38.175.132|8
213.202.216.189|8
185.220.102.254|8
104.244.73.205|8
45.13.104.179|8
221.131.165.50|8
199.195.250.77|8
72.167.48.55|8
185.220.102.252|8
89.163.252.30|8
62.102.148.68|8
104.244.76.13|8
185.31.175.207|8
185.31.175.188|8
185.129.61.6|8
176.10.99.200|8
45.153.160.133|8
45.153.160.132|8
45.153.160.131|8
45.153.160.130|8
45.153.160.137|8
45.153.160.135|8
45.153.160.134|8
45.153.160.139|8
185.31.175.243|8
185.31.175.240|8
23.183.81.227|8
117.248.249.70|8
162.247.73.192|8
37.123.163.58|8
209.141.53.74|8
107.189.8.65|8
