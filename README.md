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
Wall of shame (2021-12-25)
----

|IP|Number of (black)lists|
|---|--:|
38.91.102.77|9
222.187.238.58|9
185.220.102.248|9
162.247.74.74|9
45.13.104.179|9
221.131.165.50|9
221.181.185.94|9
185.220.102.246|9
45.153.160.133|9
45.153.160.130|9
81.17.18.58|9
116.110.92.217|9
205.185.120.235|8
107.189.5.248|8
185.220.102.4|8
5.183.209.217|8
45.88.188.13|8
185.100.86.74|8
171.25.193.25|8
38.91.102.46|8
165.232.92.17|8
185.220.102.249|8
185.220.102.253|8
221.131.165.65|8
5.2.69.50|8
171.25.193.77|8
185.165.171.175|8
209.141.47.131|8
116.110.19.131|8
80.82.77.139|8
185.100.87.72|8
209.141.58.146|8
45.153.160.136|8
221.181.185.111|8
45.153.160.129|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
107.189.1.167|8
192.42.116.16|8
192.42.116.14|8
162.247.74.27|8
185.220.102.8|8
185.130.44.108|8
185.56.80.65|8
45.153.160.140|8
