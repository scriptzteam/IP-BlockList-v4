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
Wall of shame (2021-12-08)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.77|10
185.31.175.226|9
89.234.157.254|9
185.220.100.254|9
192.42.116.16|9
45.88.137.253|9
185.130.44.108|9
45.153.160.140|9
185.31.175.215|9
171.25.193.25|9
171.25.193.20|9
185.31.175.220|8
162.247.74.200|8
134.209.198.229|8
199.249.230.163|8
23.183.81.249|8
5.183.209.217|8
176.111.173.237|8
205.185.115.39|8
185.107.47.215|8
185.220.102.248|8
162.247.74.74|8
141.98.10.63|8
104.248.85.104|8
171.25.193.78|8
185.107.47.171|8
185.220.101.1|8
176.10.104.240|8
185.220.101.40|8
134.209.205.40|8
178.20.55.18|8
178.20.55.16|8
212.192.241.124|8
192.160.102.170|8
195.254.135.76|8
23.183.81.136|8
162.247.74.213|8
185.220.102.4|8
199.249.230.119|8
212.192.241.37|8
23.183.82.135|8
141.98.10.246|8
205.185.120.71|8
185.31.175.231|8
38.91.102.77|8
221.131.165.33|8
162.247.74.217|8
45.153.160.2|8
176.10.99.200|8
221.131.165.75|8
80.67.172.162|8
45.13.104.179|8
64.113.32.29|8
221.131.165.50|8
199.195.250.77|8
185.165.171.175|8
62.102.148.68|8
45.153.160.134|8
45.153.160.139|8
209.141.47.245|8
185.31.175.243|8
23.183.82.180|8
221.181.185.111|8
134.209.95.47|8
209.141.53.74|8
