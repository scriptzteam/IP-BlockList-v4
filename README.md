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
Wall of shame (2021-11-24)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.77|10
89.163.249.244|10
185.31.175.226|9
185.31.175.220|9
141.98.10.246|9
185.31.175.235|9
185.31.175.231|9
221.131.165.33|9
5.183.209.217|9
171.25.193.20|9
209.141.47.245|9
162.247.74.74|9
221.131.165.75|9
185.220.102.250|9
221.131.165.50|9
80.67.172.162|9
136.144.41.3|9
185.31.175.240|9
185.56.80.65|9
45.153.160.2|9
45.153.160.133|9
45.153.160.131|9
45.153.160.135|9
221.181.185.111|9
209.127.17.242|9
45.153.160.129|9
185.220.100.253|9
185.31.175.243|9
45.88.137.253|9
198.144.121.93|9
212.192.241.37|9
185.31.175.215|9
23.183.82.135|9
209.141.44.165|8
185.31.175.228|8
136.144.41.139|8
221.131.165.62|8
162.247.74.206|8
185.220.102.4|8
192.160.102.170|8
162.247.74.217|8
171.25.193.25|8
185.107.47.215|8
185.191.124.143|8
185.220.102.247|8
185.220.102.240|8
185.220.102.243|8
185.220.102.248|8
185.220.102.253|8
185.220.102.252|8
141.98.10.60|8
45.13.104.179|8
64.113.32.29|8
5.2.69.50|8
171.25.193.78|8
185.220.101.1|8
195.133.18.210|8
179.43.187.36|8
179.43.187.37|8
89.163.154.91|8
209.141.32.141|8
199.195.250.77|8
176.10.104.240|8
199.19.224.231|8
62.102.148.69|8
185.100.87.72|8
45.61.186.123|8
178.20.55.16|8
104.244.76.13|8
176.10.99.200|8
23.183.81.54|8
205.185.119.40|8
185.165.168.229|8
205.185.119.112|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
212.192.241.124|8
23.183.82.180|8
45.153.160.139|8
94.230.208.147|8
209.141.62.185|8
162.247.74.27|8
185.31.175.252|8
185.220.102.244|8
89.163.243.88|8
162.247.73.192|8
192.42.116.16|8
89.234.157.254|8
107.189.28.84|8
167.71.2.26|8
185.130.44.108|8
205.185.123.252|8
45.153.160.140|8
185.31.175.213|8
212.192.246.95|8
