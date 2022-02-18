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
Wall of shame (2022-02-18)
----

|IP|Number of (black)lists|
|---|--:|
185.56.80.65|11
45.153.160.2|11
45.153.160.135|11
5.183.209.217|10
80.67.167.81|10
185.100.87.174|10
116.105.212.31|9
185.220.102.240|9
5.2.69.50|9
23.154.177.21|9
179.43.159.4|9
89.185.85.253|9
45.153.160.136|9
45.153.160.139|9
162.247.74.204|8
107.189.10.237|8
89.185.85.100|8
45.61.187.112|8
5.2.77.22|8
91.250.242.12|8
89.163.249.192|8
185.220.102.244|8
185.220.102.247|8
185.220.102.248|8
185.220.102.249|8
81.17.24.154|8
171.25.193.78|8
185.220.101.4|8
112.85.42.89|8
185.100.87.133|8
81.17.18.61|8
81.17.18.60|8
193.218.118.158|8
45.153.160.129|8
185.220.100.252|8
5.2.72.168|8
116.105.216.128|8
45.153.160.140|8
46.19.139.18|8
171.25.193.25|8
5.2.73.169|8
185.220.102.251|8
185.220.102.250|8
45.9.20.25|8
23.154.177.6|8
23.154.177.5|8
23.154.177.18|8
23.154.177.19|8
179.43.175.170|8
45.154.168.39|8
185.129.62.62|8
45.153.160.130|8
45.153.160.134|8
23.154.177.7|8
199.195.253.156|8
185.220.103.115|8
