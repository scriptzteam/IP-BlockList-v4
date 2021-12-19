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
Wall of shame (2021-12-19)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.25|9
162.247.74.74|9
185.220.102.250|9
185.100.87.72|9
221.181.185.111|9
205.185.120.235|8
205.185.120.71|8
185.220.103.5|8
45.88.188.13|8
222.187.238.58|8
195.133.18.24|8
185.220.102.240|8
185.220.102.243|8
185.38.175.132|8
213.202.216.189|8
185.220.102.254|8
185.220.102.253|8
37.123.163.58|8
45.13.104.179|8
64.113.32.29|8
5.2.69.50|8
221.131.165.50|8
185.107.47.171|8
45.153.160.2|8
161.35.205.46|8
5.199.143.202|8
81.17.18.62|8
185.220.102.245|8
45.153.160.138|8
222.186.42.137|8
45.153.160.129|8
185.220.100.254|8
209.141.44.102|8
176.10.99.200|8
163.172.213.212|8
