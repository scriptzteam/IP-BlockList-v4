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
Wall of shame (2021-11-09)
----

|IP|Number of (black)lists|
|---|--:|
45.153.160.135|10
185.31.175.240|10
185.31.175.226|9
185.31.175.220|9
176.111.173.237|9
199.19.224.231|9
5.2.69.50|9
45.88.137.253|9
171.25.193.20|9
171.25.193.25|9
205.185.120.180|9
117.7.122.163|9
185.31.175.215|9
141.98.10.82|9
107.189.30.134|9
116.110.223.93|8
205.185.115.39|8
80.82.77.33|8
162.247.74.200|8
199.19.225.198|8
5.183.209.217|8
185.220.102.240|8
221.131.165.62|8
171.25.193.77|8
185.220.101.4|8
81.17.18.62|8
195.133.18.210|8
162.247.72.199|8
45.153.160.129|8
136.144.41.253|8
209.141.41.103|8
38.91.102.38|8
107.189.14.165|8
185.31.175.231|8
185.216.32.130|8
206.189.144.184|8
185.100.86.74|8
209.141.33.121|8
141.98.10.72|8
221.131.165.75|8
185.38.175.132|8
185.220.102.254|8
80.67.172.162|8
221.131.165.50|8
185.56.80.65|8
185.31.175.207|8
209.127.17.234|8
45.153.160.133|8
45.153.160.131|8
45.153.160.137|8
205.185.119.40|8
192.42.116.23|8
185.31.175.243|8
185.31.175.247|8
221.181.185.111|8
