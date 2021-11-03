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
Wall of shame (2021-11-03)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.20|10
171.25.193.25|10
80.67.172.162|10
162.247.74.27|9
5.183.209.217|9
5.2.69.50|9
162.247.74.74|9
185.220.102.253|9
185.220.102.250|9
141.98.10.63|9
141.98.10.60|9
64.113.32.29|9
171.25.193.77|9
171.25.193.78|9
2.56.59.39|9
104.244.76.13|9
192.42.116.16|9
141.98.10.81|9
198.144.121.93|9
5.189.168.79|9
185.100.87.202|9
116.110.223.93|8
128.31.0.13|8
80.82.77.33|8
221.131.165.62|8
199.195.248.175|8
199.249.230.163|8
71.6.199.23|8
209.141.54.35|8
185.107.47.215|8
185.220.102.244|8
185.220.102.242|8
221.131.165.75|8
198.98.54.17|8
221.131.165.50|8
209.141.55.232|8
185.107.47.171|8
185.220.101.1|8
185.56.80.65|8
80.82.77.139|8
136.144.41.253|8
185.100.87.72|8
5.199.143.202|8
176.10.99.200|8
117.7.122.163|8
185.220.102.241|8
185.220.102.243|8
45.153.160.133|8
45.153.160.135|8
221.181.185.111|8
209.127.17.242|8
45.153.160.129|8
54.36.108.162|8
185.220.100.253|8
185.220.100.255|8
205.185.126.71|8
94.230.208.147|8
221.131.165.72|8
141.98.10.121|8
166.70.207.2|8
141.98.10.82|8
209.141.59.184|8
68.183.180.46|8
45.153.160.140|8
