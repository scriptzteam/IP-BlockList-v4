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
Wall of shame (2021-10-26)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.244|9
162.247.74.74|9
45.153.160.2|9
198.144.121.93|9
185.220.102.253|9
185.56.80.65|9
185.31.175.228|8
162.247.74.206|8
165.22.100.49|8
5.183.209.217|8
185.107.47.215|8
185.220.102.243|8
5.2.69.50|8
171.25.193.78|8
185.107.47.171|8
185.220.101.4|8
18.27.197.252|8
209.141.40.193|8
221.181.185.111|8
45.153.160.129|8
185.220.100.253|8
185.220.100.255|8
185.100.87.72|8
94.230.208.147|8
198.98.48.67|8
60.170.247.162|8
209.141.53.99|8
141.98.10.60|8
185.31.175.231|8
185.73.124.253|8
198.98.52.12|8
185.38.175.132|8
185.220.102.250|8
80.67.172.162|8
64.113.32.29|8
199.195.253.199|8
185.220.101.57|8
205.185.120.183|8
185.129.62.62|8
45.153.160.133|8
45.153.160.131|8
106.12.155.22|8
185.220.100.243|8
185.220.100.240|8
185.220.100.241|8
199.195.251.49|8
141.98.10.81|8
141.98.10.82|8
