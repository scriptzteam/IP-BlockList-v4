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
Wall of shame (2021-10-03)
----

|IP|Number of (black)lists|
|---|--:|
198.98.53.184|10
222.187.254.41|10
45.155.204.39|9
185.220.102.248|9
141.98.10.60|9
221.131.165.65|9
198.98.58.250|9
107.189.3.160|9
199.195.254.38|9
107.189.8.8|9
171.25.193.77|9
60.8.87.190|9
209.141.53.166|9
107.189.1.85|9
221.181.185.94|9
198.98.50.192|9
171.225.185.69|9
205.185.118.82|9
104.244.79.215|9
179.43.141.99|9
222.187.232.39|9
222.187.238.58|9
198.98.51.254|9
221.131.165.33|9
185.73.124.253|9
221.131.165.75|9
221.131.165.50|9
107.189.30.211|9
185.31.175.243|9
117.248.249.70|9
209.141.52.9|9
45.93.201.148|9
185.31.175.226|8
165.22.100.49|8
185.31.175.228|8
89.234.157.254|8
199.195.252.247|8
162.247.74.74|8
5.2.69.50|8
45.133.1.31|8
45.133.1.35|8
205.185.114.141|8
171.25.193.78|8
185.107.47.171|8
178.20.55.18|8
198.98.52.69|8
107.189.13.122|8
45.153.160.129|8
141.98.10.121|8
185.100.87.72|8
107.189.13.161|8
107.189.31.248|8
185.220.102.4|8
185.130.44.108|8
199.195.248.37|8
77.247.181.165|8
77.247.181.163|8
60.170.247.162|8
93.174.95.106|8
179.43.175.26|8
209.141.55.247|8
171.25.193.20|8
171.25.193.25|8
212.193.30.101|8
213.202.216.189|8
80.67.172.162|8
209.141.55.232|8
89.248.167.131|8
185.31.175.215|8
176.10.99.200|8
141.98.10.81|8
141.98.10.82|8
45.95.169.176|8
