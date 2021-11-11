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
Wall of shame (2021-11-11)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.243|10
45.88.137.253|10
209.141.33.121|10
136.144.41.253|10
2.56.59.39|10
205.185.120.180|10
209.141.59.184|10
107.189.30.134|10
141.98.10.60|10
185.31.175.228|9
185.31.175.220|9
5.183.209.217|9
205.185.115.39|9
141.98.10.63|9
185.83.214.69|9
209.141.33.193|9
60.170.247.162|9
209.141.44.165|9
185.31.175.235|9
185.31.175.231|9
206.189.144.184|9
171.25.193.20|9
205.185.120.183|9
45.153.160.135|9
209.141.49.147|9
185.31.175.240|9
141.98.10.81|9
185.31.175.226|8
80.82.77.33|8
221.131.165.62|8
199.249.230.163|8
199.19.225.198|8
89.163.249.244|8
199.19.224.231|8
185.220.102.248|8
211.22.65.18|8
5.2.69.50|8
37.0.10.28|8
185.220.101.1|8
80.82.77.139|8
195.133.18.210|8
45.153.160.129|8
185.31.175.252|8
185.100.87.72|8
89.163.243.88|8
171.25.193.25|8
222.187.254.41|8
185.191.124.143|8
209.141.59.77|8
141.98.10.72|8
178.17.174.14|8
64.113.32.29|8
221.131.165.50|8
185.56.80.65|8
209.127.17.234|8
117.7.122.163|8
45.153.160.131|8
45.88.137.100|8
141.98.10.109|8
185.31.175.247|8
221.181.185.111|8
198.98.51.189|8
141.98.10.82|8
209.141.59.180|8
