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
Wall of shame (2022-02-14)
----

|IP|Number of (black)lists|
|---|--:|
185.100.87.174|11
45.153.160.130|11
5.183.209.217|10
89.163.249.244|10
45.153.160.2|10
80.67.167.81|10
45.153.160.136|10
162.247.74.204|9
89.185.85.100|9
116.105.212.31|9
5.2.69.50|9
107.189.10.237|9
81.17.18.60|9
23.154.177.21|9
171.25.193.25|9
185.220.102.254|9
199.195.253.156|9
179.43.187.173|8
128.31.0.13|8
45.61.187.112|8
185.117.215.9|8
185.107.47.215|8
162.247.74.27|8
179.43.175.170|8
185.220.102.244|8
185.220.102.247|8
185.220.102.241|8
185.220.102.242|8
185.220.102.243|8
185.220.102.248|8
185.220.102.249|8
162.247.74.74|8
171.25.193.77|8
171.25.193.78|8
185.220.101.4|8
185.220.101.1|8
195.144.21.219|8
45.154.255.147|8
23.154.177.4|8
81.17.18.62|8
162.247.72.199|8
45.153.160.129|8
185.220.100.253|8
185.220.100.252|8
185.220.100.255|8
185.100.87.72|8
213.164.206.127|8
166.70.207.2|8
185.220.102.8|8
45.155.204.161|8
46.19.139.18|8
185.220.103.5|8
162.247.74.216|8
171.25.193.20|8
118.186.201.132|8
213.202.216.189|8
185.220.102.253|8
185.220.102.251|8
185.220.102.250|8
64.113.32.29|8
209.141.55.96|8
45.9.20.25|8
23.154.177.2|8
5.2.70.140|8
62.102.148.69|8
89.185.85.253|8
185.129.61.6|8
45.153.160.133|8
45.153.160.134|8
46.182.21.248|8
192.42.116.27|8
198.98.51.189|8
179.43.187.95|8
185.220.103.115|8
185.100.87.202|8
