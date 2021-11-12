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
Wall of shame (2021-11-12)
----

|IP|Number of (black)lists|
|---|--:|
176.111.173.237|10
171.25.193.20|10
209.141.33.193|10
60.170.247.162|9
185.31.175.226|9
199.249.230.163|9
5.183.209.217|9
185.107.47.215|9
209.141.33.121|9
162.247.74.74|9
185.220.102.250|9
141.98.10.63|9
141.98.10.60|9
64.113.32.29|9
221.131.165.50|9
185.220.101.1|9
2.56.59.39|9
209.141.49.147|9
205.185.120.180|9
222.187.254.41|9
117.7.122.163|9
185.220.102.243|9
45.153.160.133|9
45.153.160.131|9
45.153.160.135|9
185.31.175.247|9
221.181.185.111|9
209.141.62.185|9
185.31.175.252|9
45.88.137.253|9
209.141.59.184|9
107.189.30.134|9
185.31.175.215|9
209.141.44.165|8
185.31.175.220|8
185.243.218.50|8
159.223.2.20|8
93.174.95.106|8
162.247.74.206|8
185.31.175.235|8
185.31.175.231|8
162.247.74.217|8
199.19.225.198|8
206.189.144.184|8
89.234.157.254|8
141.98.10.109|8
171.25.193.25|8
205.185.115.39|8
185.191.124.143|8
209.141.59.77|8
185.220.102.244|8
185.38.175.132|8
185.220.102.253|8
80.67.172.162|8
221.131.165.62|8
185.83.214.69|8
5.2.69.50|8
199.195.250.77|8
37.0.10.28|8
171.25.193.77|8
171.25.193.78|8
205.185.120.183|8
176.10.104.240|8
199.19.224.231|8
80.82.77.139|8
136.144.41.253|8
185.100.87.72|8
178.20.55.16|8
104.244.76.13|8
89.248.167.131|8
176.10.99.200|8
209.127.17.234|8
195.133.18.210|8
209.141.58.55|8
205.185.119.40|8
185.220.100.241|8
209.127.17.242|8
45.88.137.100|8
192.160.102.170|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
185.220.101.33|8
185.31.175.243|8
185.31.175.240|8
94.230.208.147|8
185.165.168.229|8
192.42.116.16|8
192.42.116.13|8
162.247.74.27|8
185.220.102.4|8
198.98.51.189|8
141.98.10.82|8
185.31.175.207|8
93.123.93.104|8
185.31.175.213|8
