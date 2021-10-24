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
Wall of shame (2021-10-24)
----

|IP|Number of (black)lists|
|---|--:|
128.31.0.13|9
185.220.102.244|9
162.247.74.74|9
198.98.52.12|9
198.98.48.67|9
185.220.103.7|8
5.183.209.217|8
222.187.238.58|8
185.73.124.253|8
171.25.193.20|8
171.25.193.25|8
185.220.102.241|8
185.220.102.243|8
185.220.102.248|8
221.131.165.75|8
185.220.102.253|8
80.67.172.162|8
185.83.214.69|8
5.2.69.50|8
199.195.253.199|8
171.25.193.78|8
209.141.40.193|8
18.27.197.252|8
45.153.160.2|8
199.195.250.77|8
221.181.185.94|8
136.144.41.253|8
89.163.252.12|8
185.220.100.242|8
185.220.100.240|8
185.220.100.241|8
185.220.100.253|8
185.220.100.255|8
185.220.100.254|8
199.19.224.76|8
185.31.175.247|8
89.163.243.88|8
185.220.102.4|8
141.98.10.81|8
141.98.10.82|8
185.107.47.215|8
163.172.213.212|8
198.144.121.93|8
45.153.160.140|8
199.195.251.49|8
141.98.10.60|8
