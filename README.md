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
Wall of shame (2021-12-18)
----

|IP|Number of (black)lists|
|---|--:|
185.107.47.215|9
213.202.216.189|9
205.185.114.158|9
45.153.160.133|9
198.98.51.189|9
164.90.203.55|8
5.183.209.217|8
205.185.115.39|8
185.220.102.244|8
185.220.102.247|8
185.220.102.243|8
162.247.74.74|8
107.189.1.167|8
141.98.10.63|8
5.2.69.50|8
209.141.44.102|8
185.107.47.171|8
212.192.241.163|8
185.14.97.147|8
81.17.18.62|8
45.153.160.129|8
185.220.100.254|8
185.100.87.72|8
104.244.79.234|8
166.70.207.2|8
107.189.14.165|8
222.187.238.58|8
205.185.120.235|8
205.185.120.71|8
38.91.102.77|8
45.153.160.2|8
195.133.18.24|8
209.141.47.245|8
185.220.102.253|8
185.220.102.250|8
209.141.53.74|8
80.67.172.162|8
45.13.104.179|8
64.113.32.29|8
23.154.177.5|8
185.165.171.175|8
163.172.213.212|8
185.56.80.65|8
209.141.34.220|8
89.163.252.30|8
161.35.205.46|8
45.153.160.131|8
45.153.160.134|8
45.153.160.139|8
81.17.18.59|8
221.181.185.111|8
37.123.163.58|8
107.189.8.65|8
