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
Wall of shame (2021-11-04)
----

|IP|Number of (black)lists|
|---|--:|
141.98.10.63|10
141.98.10.60|10
185.100.87.72|10
185.31.175.231|9
5.2.69.50|9
141.98.10.109|9
171.25.193.20|9
171.25.193.25|9
45.61.185.168|9
162.247.74.74|9
80.67.172.162|9
171.25.193.78|9
209.141.60.103|9
2.56.59.39|9
205.185.120.180|9
45.153.160.135|9
45.153.160.129|9
185.220.100.255|9
141.98.10.121|9
209.141.54.35|9
141.98.10.81|9
141.98.10.82|9
209.141.59.184|9
209.141.55.232|9
198.144.121.93|9
45.135.232.159|8
185.31.175.220|8
128.31.0.13|8
80.82.77.33|8
162.247.74.27|8
199.195.248.175|8
185.220.103.7|8
185.31.175.235|8
199.249.230.163|8
185.220.102.243|8
162.247.74.217|8
5.183.209.217|8
176.10.99.200|8
198.98.49.124|8
185.100.86.74|8
185.107.47.215|8
5.206.227.16|8
185.220.102.244|8
198.98.54.17|8
185.220.102.254|8
221.131.165.50|8
64.227.126.252|8
8.209.91.186|8
64.113.32.29|8
185.107.47.171|8
185.220.101.4|8
209.141.42.29|8
185.31.175.240|8
209.141.33.121|8
205.185.120.183|8
80.82.77.139|8
136.144.41.253|8
185.90.136.171|8
81.17.18.62|8
195.133.18.210|8
162.247.72.199|8
209.141.54.195|8
221.181.185.111|8
209.127.17.242|8
185.220.100.253|8
185.220.100.252|8
185.220.100.254|8
67.205.170.72|8
198.96.155.3|8
117.7.122.163|8
185.31.175.252|8
221.131.165.72|8
167.88.161.219|8
45.88.137.253|8
185.220.102.4|8
89.234.157.254|8
185.31.175.207|8
5.189.168.79|8
23.129.64.188|8
107.189.30.134|8
