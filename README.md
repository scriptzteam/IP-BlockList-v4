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
Wall of shame (2021-12-16)
----

|IP|Number of (black)lists|
|---|--:|
222.187.238.58|9
171.25.193.78|9
45.154.255.147|9
178.128.249.136|9
221.181.185.111|9
185.243.218.50|8
205.185.120.235|8
205.185.120.71|8
38.91.102.77|8
171.25.193.25|8
85.202.169.128|8
116.105.77.214|8
209.141.47.245|8
185.220.102.243|8
162.247.74.74|8
2.56.59.114|8
185.220.102.253|8
205.185.114.158|8
64.113.32.29|8
179.43.187.37|8
185.56.80.65|8
199.195.250.77|8
161.35.201.142|8
62.102.148.69|8
212.192.241.124|8
116.110.92.217|8
89.163.249.244|8
209.141.44.102|8
185.130.44.108|8
209.141.53.74|8
