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
Wall of shame (2022-02-07)
----

|IP|Number of (black)lists|
|---|--:|
23.236.146.166|10
81.17.18.60|10
185.38.175.132|10
185.56.80.65|10
45.153.160.130|10
45.153.160.2|10
5.183.209.217|9
162.247.74.74|9
5.2.69.50|9
185.100.87.72|9
185.100.87.174|9
162.247.74.213|9
171.25.193.25|9
171.25.193.20|9
185.220.102.250|9
45.153.160.133|9
45.153.160.136|9
45.153.160.134|9
122.194.229.38|8
162.247.74.204|8
162.247.74.27|8
179.43.175.170|8
185.220.102.247|8
185.220.102.240|8
185.220.102.241|8
185.220.102.243|8
185.220.102.248|8
171.25.193.77|8
171.25.193.78|8
23.154.177.4|8
185.170.114.25|8
81.17.18.62|8
45.153.160.129|8
185.220.100.254|8
185.220.100.253|8
185.220.100.252|8
185.220.100.255|8
192.42.116.16|8
192.42.116.14|8
185.220.102.8|8
179.43.187.146|8
185.130.44.108|8
116.105.212.31|8
45.155.204.161|8
45.153.160.140|8
185.100.86.74|8
185.220.102.254|8
185.220.102.253|8
64.113.32.29|8
45.9.20.25|8
23.154.177.2|8
104.244.76.13|8
185.129.62.62|8
45.153.160.137|8
45.153.160.139|8
81.17.18.58|8
192.42.116.27|8
31.7.57.130|8
179.43.187.95|8
185.100.87.202|8
