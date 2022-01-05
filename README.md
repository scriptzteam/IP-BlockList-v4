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
Wall of shame (2022-01-05)
----

|IP|Number of (black)lists|
|---|--:|
185.220.102.254|10
45.13.104.179|10
171.25.193.77|9
104.244.72.132|9
81.17.18.62|9
107.189.5.68|9
185.220.102.250|9
64.113.32.29|9
171.252.186.42|9
45.153.160.133|9
81.17.18.58|9
107.189.7.175|9
107.189.6.166|9
5.183.209.217|8
185.220.102.243|8
171.25.193.20|8
5.2.69.50|8
185.220.101.4|8
185.191.127.212|8
45.154.255.147|8
97.74.80.115|8
171.25.193.78|8
221.181.185.94|8
104.244.78.183|8
89.163.249.244|8
107.189.5.5|8
185.130.44.108|8
5.2.72.168|8
137.184.58.227|8
46.19.139.18|8
222.187.238.58|8
185.100.86.74|8
222.187.254.41|8
185.38.175.132|8
185.220.102.253|8
221.131.165.50|8
107.189.12.227|8
185.56.80.65|8
104.244.72.120|8
62.102.148.69|8
185.129.61.2|8
185.129.61.6|8
104.244.79.196|8
221.181.185.111|8
185.165.171.175|8
37.123.163.58|8
