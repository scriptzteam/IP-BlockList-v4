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
Wall of shame (2021-11-10)
----

|IP|Number of (black)lists|
|---|--:|
209.141.44.165|11
171.25.193.20|11
64.113.32.29|11
185.31.175.231|10
171.25.193.25|10
141.98.10.60|10
2.56.59.39|10
205.185.120.180|10
199.19.224.231|10
45.88.137.253|10
107.189.30.134|10
185.31.175.220|9
205.185.115.39|9
162.247.74.27|9
162.247.74.74|9
141.98.10.72|9
5.2.69.50|9
171.25.193.78|9
185.100.87.72|9
45.153.160.139|9
195.133.18.210|9
185.220.102.244|9
185.220.102.243|9
45.153.160.131|9
45.153.160.137|9
209.141.49.147|9
185.31.175.240|9
185.31.175.247|9
166.70.207.2|9
89.234.157.254|9
141.98.10.81|9
141.98.10.82|9
185.31.175.207|9
60.170.247.162|8
185.31.175.228|8
193.142.146.242|8
128.31.0.13|8
80.82.77.33|8
159.223.2.20|8
94.232.46.202|8
199.19.225.198|8
206.189.144.184|8
176.10.99.200|8
141.98.10.109|8
176.111.173.237|8
185.107.47.215|8
209.141.33.121|8
185.220.102.247|8
185.220.102.241|8
211.22.65.18|8
185.220.102.253|8
221.131.165.50|8
141.98.10.63|8
209.141.33.193|8
221.131.165.62|8
38.91.102.38|8
185.83.214.69|8
185.220.101.33|8
198.96.155.3|8
171.25.193.77|8
185.220.101.4|8
45.124.84.250|8
205.185.120.183|8
45.153.160.2|8
176.10.104.240|8
80.82.77.139|8
222.187.254.41|8
178.20.55.18|8
199.195.254.81|8
209.127.17.234|8
81.17.18.62|8
117.7.122.163|8
45.153.160.135|8
45.88.137.100|8
45.153.160.129|8
185.220.100.253|8
185.220.100.255|8
185.31.175.252|8
185.220.102.4|8
185.130.44.108|8
209.141.59.184|8
163.172.213.212|8
80.67.172.162|8
185.100.87.202|8
