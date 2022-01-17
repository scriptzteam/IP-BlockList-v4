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
Wall of shame (2022-01-17)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.25|10
37.123.163.58|10
81.17.18.62|9
185.100.87.72|9
46.19.139.18|9
185.38.175.132|9
185.220.102.254|9
45.13.104.179|9
45.153.160.133|9
81.17.18.58|9
91.149.225.120|9
206.189.103.89|8
5.183.209.217|8
89.234.157.254|8
5.2.77.22|8
185.220.102.242|8
185.220.102.248|8
171.25.193.20|8
221.131.165.65|8
185.191.127.231|8
171.25.193.78|8
185.220.101.3|8
51.15.43.205|8
185.191.127.212|8
185.100.87.133|8
195.254.135.76|8
104.244.78.168|8
185.220.102.4|8
185.220.102.8|8
222.187.238.58|8
185.220.102.6|8
107.189.4.203|8
222.187.254.41|8
89.58.19.2|8
185.220.102.250|8
64.113.32.29|8
23.154.177.6|8
62.102.148.69|8
185.129.61.6|8
45.153.160.137|8
45.153.160.134|8
31.7.57.130|8
221.181.185.111|8
107.189.6.166|8
92.255.85.28|8
45.153.160.2|8
185.100.87.202|8
