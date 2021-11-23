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
Wall of shame (2021-11-23)
----

|IP|Number of (black)lists|
|---|--:|
89.163.249.244|10
185.31.175.220|9
141.98.10.246|9
221.131.165.33|9
162.247.74.74|9
221.131.165.75|9
205.185.123.252|9
80.67.172.162|9
136.144.41.3|9
171.25.193.77|9
179.43.187.37|9
185.56.80.65|9
45.153.160.2|9
45.153.160.133|9
45.153.160.135|9
221.181.185.111|9
185.220.100.253|9
45.88.137.253|9
198.144.121.93|9
45.153.160.129|9
185.31.175.226|8
80.82.77.33|8
221.131.165.62|8
162.247.74.206|8
185.220.102.4|8
185.31.175.231|8
192.160.102.170|8
162.247.74.217|8
89.234.157.254|8
171.25.193.20|8
171.25.193.25|8
209.141.47.245|8
185.107.47.215|8
185.191.124.143|8
185.220.102.244|8
185.220.102.240|8
185.220.102.248|8
185.220.102.253|8
185.220.102.252|8
185.220.102.250|8
221.131.165.50|8
64.113.32.29|8
5.2.69.50|8
171.25.193.78|8
195.133.18.210|8
89.163.154.91|8
185.31.175.243|8
199.195.250.77|8
199.19.224.231|8
62.102.148.69|8
185.170.114.25|8
45.61.186.123|8
178.20.55.16|8
104.244.76.13|8
176.10.99.200|8
31.210.20.110|8
45.153.160.139|8
205.185.119.40|8
185.220.100.242|8
205.185.119.112|8
209.127.17.242|8
185.165.168.229|8
104.244.77.80|8
185.220.100.255|8
185.220.100.254|8
23.183.82.180|8
94.230.208.147|8
192.42.116.16|8
209.141.62.185|8
162.247.74.27|8
5.183.209.217|8
185.130.44.108|8
212.192.241.37|8
185.31.175.215|8
23.183.82.135|8
