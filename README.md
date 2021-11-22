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
Wall of shame (2021-11-22)
----

|IP|Number of (black)lists|
|---|--:|
162.247.74.74|10
45.61.186.123|10
212.192.241.37|10
185.31.175.220|9
185.220.102.244|9
185.220.102.246|9
185.220.102.243|9
171.25.193.20|9
141.98.10.63|9
5.2.69.50|9
171.25.193.77|9
171.25.193.78|9
178.20.55.16|9
209.127.17.242|9
45.153.160.129|9
45.88.137.253|9
185.31.175.213|9
185.31.175.235|9
185.31.175.231|9
209.141.47.245|9
185.220.102.250|9
179.43.187.37|9
185.31.175.207|9
45.153.160.135|9
205.185.119.40|9
221.181.185.111|9
185.31.175.226|8
128.31.0.13|8
159.223.2.20|8
209.14.131.233|8
89.234.157.254|8
185.220.102.242|8
185.220.102.248|8
205.185.122.230|8
211.22.65.18|8
205.185.123.252|8
141.98.10.60|8
221.131.165.62|8
45.153.160.2|8
185.220.101.42|8
199.19.224.157|8
185.220.101.4|8
209.141.33.193|8
185.220.100.255|8
185.220.100.254|8
166.70.207.2|8
185.130.44.108|8
81.6.43.167|8
45.153.160.140|8
137.184.51.62|8
209.141.44.165|8
185.243.218.50|8
38.91.102.77|8
36.110.228.254|8
185.100.86.74|8
171.25.193.25|8
176.10.99.200|8
195.133.18.24|8
222.187.254.41|8
209.141.33.121|8
221.131.165.75|8
64.113.32.29|8
221.131.165.50|8
199.195.250.77|8
195.133.18.210|8
179.43.187.36|8
209.141.32.141|8
104.244.76.13|8
45.153.160.130|8
45.153.160.137|8
45.153.160.134|8
205.185.119.112|8
205.185.113.226|8
185.31.175.243|8
185.31.175.240|8
209.141.62.185|8
198.98.51.189|8
185.31.175.215|8
