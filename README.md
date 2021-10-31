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
Wall of shame (2021-10-31)
----

|IP|Number of (black)lists|
|---|--:|
162.247.74.74|10
128.31.0.13|9
185.107.47.215|9
171.25.193.25|9
185.220.102.254|9
64.113.32.29|9
162.247.74.206|8
162.247.74.204|8
5.183.209.217|8
89.234.157.254|8
185.220.102.244|8
185.220.102.247|8
185.220.102.243|8
5.2.69.50|8
171.25.193.77|8
185.107.47.171|8
18.27.197.252|8
45.153.160.2|8
209.127.17.242|8
185.220.100.253|8
185.220.100.255|8
185.220.100.254|8
94.230.208.147|8
45.153.160.140|8
162.247.74.27|8
185.220.103.7|8
162.247.74.217|8
171.25.193.20|8
80.67.172.162|8
104.244.76.13|8
185.56.80.65|8
45.153.160.133|8
185.220.100.242|8
185.220.100.240|8
185.220.100.241|8
185.220.101.32|8
185.100.87.202|8
