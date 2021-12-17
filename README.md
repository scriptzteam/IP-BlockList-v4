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
Wall of shame (2021-12-17)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.78|9
185.220.100.255|9
176.10.99.200|9
192.42.116.13|9
164.90.203.55|8
205.185.124.219|8
89.234.157.254|8
85.202.169.128|8
185.107.47.215|8
185.220.102.248|8
162.247.74.74|8
107.189.1.167|8
141.98.10.63|8
5.2.69.50|8
171.25.193.77|8
209.141.44.102|8
51.15.43.205|8
185.170.114.25|8
178.20.55.16|8
221.181.185.111|8
45.153.160.129|8
185.220.100.253|8
185.220.100.252|8
185.220.100.254|8
185.100.87.72|8
192.42.116.16|8
166.70.207.2|8
185.220.102.8|8
185.130.44.108|8
5.2.70.140|8
185.56.80.65|8
161.35.201.142|8
62.102.148.69|8
161.35.205.46|8
45.153.160.133|8
45.153.160.134|8
209.141.47.245|8
185.220.100.247|8
198.98.51.189|8
167.172.43.16|8
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
Wall of shame (2021-12-17)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.78|9
185.220.100.255|9
176.10.99.200|9
192.42.116.13|9
164.90.203.55|8
205.185.124.219|8
89.234.157.254|8
85.202.169.128|8
185.107.47.215|8
185.220.102.248|8
162.247.74.74|8
107.189.1.167|8
141.98.10.63|8
5.2.69.50|8
171.25.193.77|8
209.141.44.102|8
51.15.43.205|8
185.170.114.25|8
178.20.55.16|8
221.181.185.111|8
45.153.160.129|8
185.220.100.253|8
185.220.100.252|8
185.220.100.254|8
185.100.87.72|8
192.42.116.16|8
166.70.207.2|8
185.220.102.8|8
185.130.44.108|8
5.2.70.140|8
185.56.80.65|8
161.35.201.142|8
62.102.148.69|8
161.35.205.46|8
45.153.160.133|8
45.153.160.134|8
209.141.47.245|8
185.220.100.247|8
198.98.51.189|8
167.172.43.16|8
