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
Wall of shame (2022-01-31)
----

|IP|Number of (black)lists|
|---|--:|
45.153.160.2|10
171.25.193.25|10
185.38.175.132|10
80.67.172.162|10
185.220.100.254|9
185.220.102.244|9
185.220.102.240|9
5.2.69.50|9
81.17.18.60|9
192.42.116.16|9
185.220.103.7|9
171.25.193.20|9
185.220.102.253|9
185.220.102.250|9
185.56.80.65|9
185.129.62.62|9
45.153.160.134|9
81.17.18.58|9
199.195.253.118|9
185.100.87.202|9
107.189.10.237|8
5.183.209.217|8
89.163.249.244|8
89.234.157.254|8
5.2.77.22|8
162.247.74.27|8
185.220.102.247|8
185.220.102.241|8
185.220.102.242|8
185.220.102.243|8
185.220.102.248|8
185.220.102.249|8
104.244.74.253|8
171.25.193.77|8
171.25.193.78|8
185.220.101.4|8
185.220.101.1|8
23.154.177.3|8
185.100.87.133|8
205.185.113.12|8
81.17.18.61|8
23.154.177.20|8
185.220.100.253|8
185.220.100.252|8
185.220.100.255|8
185.100.87.72|8
185.220.101.24|8
213.164.206.127|8
185.220.102.4|8
185.220.102.8|8
116.105.212.31|8
5.2.72.168|8
45.155.204.161|8
45.153.160.140|8
104.244.74.28|8
46.19.139.18|8
27.122.59.100|8
162.247.74.213|8
209.141.40.109|8
222.187.238.58|8
185.100.86.74|8
5.2.72.73|8
5.2.73.169|8
179.43.187.70|8
89.58.19.2|8
185.220.102.254|8
185.220.102.251|8
64.113.32.29|8
23.154.177.2|8
45.129.56.200|8
45.154.168.39|8
45.153.160.133|8
45.153.160.131|8
45.153.160.130|8
45.153.160.137|8
185.220.101.32|8
31.7.57.130|8
205.185.120.164|8
