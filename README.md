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
Wall of shame (2022-01-12)
----

|IP|Number of (black)lists|
|---|--:|
81.17.18.62|10
45.13.104.179|10
107.189.4.203|9
171.25.193.20|9
185.38.175.132|9
185.220.102.254|9
185.129.61.6|9
45.153.160.133|9
81.17.18.58|9
37.123.163.58|9
185.220.100.254|8
5.183.209.217|8
89.234.157.254|8
5.2.77.22|8
185.220.102.243|8
209.141.58.169|8
185.191.124.151|8
221.131.165.65|8
5.2.69.50|8
185.191.127.231|8
171.25.193.77|8
171.25.193.78|8
212.192.241.163|8
185.191.127.212|8
45.154.255.147|8
222.187.254.41|8
221.181.185.94|8
185.100.87.133|8
81.17.18.60|8
221.181.185.111|8
185.220.100.252|8
89.163.249.244|8
107.189.5.5|8
185.100.87.72|8
185.220.102.4|8
5.2.72.124|8
222.187.238.58|8
89.58.19.2|8
64.113.32.29|8
221.131.165.50|8
23.154.177.6|8
45.153.160.130|8
107.189.1.90|8
107.189.6.166|8
199.195.248.29|8
81.17.18.59|8
185.100.87.202|8
