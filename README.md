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
141.98.10.246|9
221.131.165.33|9
209.141.47.245|9
221.131.165.75|9
221.131.165.50|9
45.153.160.135|9
221.181.185.111|9
212.192.241.37|9
209.141.44.165|8
221.131.165.62|8
185.31.175.231|8
5.183.209.217|8
171.25.193.25|8
185.220.102.243|8
185.220.102.248|8
162.247.74.74|8
171.25.193.77|8
185.220.101.1|8
195.133.18.210|8
179.43.187.36|8
209.141.32.141|8
185.31.175.240|8
199.19.224.231|8
45.61.186.123|8
23.183.81.54|8
45.153.160.131|8
185.220.100.254|8
185.31.175.243|8
23.183.82.180|8
23.183.81.227|8
45.88.137.253|8
198.98.51.189|8
167.71.2.26|8
205.185.123.252|8
185.31.175.215|8
23.183.82.135|8
