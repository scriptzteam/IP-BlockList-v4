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
Wall of shame (2022-03-24)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.78|9
45.67.34.253|9
112.85.42.124|9
185.129.62.62|9
45.67.34.100|9
114.92.198.79|8
89.234.157.254|8
116.105.212.31|8
97.74.82.17|8
171.25.193.77|8
185.220.101.1|8
61.177.172.89|8
185.220.100.253|8
185.220.100.255|8
185.220.100.254|8
185.220.101.24|8
192.42.116.16|8
185.220.102.4|8
185.220.102.8|8
179.43.168.126|8
46.19.139.18|8
171.25.193.25|8
61.177.172.108|8
194.165.16.5|8
185.56.80.65|8
134.209.199.124|8
122.194.229.54|8
185.220.100.247|8
112.85.42.73|8
37.123.163.58|8
