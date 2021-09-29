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
Wall of shame (2021-09-29)
----

|IP|Number of (black)lists|
|---|--:|
198.98.58.250|10
45.133.1.35|10
107.189.3.160|10
107.189.8.8|10
198.98.52.69|10
209.141.53.166|10
107.189.1.85|10
198.98.50.192|10
104.244.79.215|10
198.98.53.184|10
107.189.30.211|10
117.248.249.70|10
107.189.4.119|9
176.111.173.237|9
199.195.252.247|9
221.131.165.65|9
199.195.254.38|9
209.141.51.168|9
171.25.193.78|9
209.141.32.151|9
221.181.185.94|9
162.247.72.199|9
205.185.118.82|9
141.98.10.121|9
107.189.13.161|9
107.189.31.248|9
199.195.248.37|9
60.170.247.162|9
45.133.1.3|9
222.187.227.122|9
198.98.51.254|9
179.43.175.26|9
209.141.55.247|9
222.187.238.58|9
171.25.193.20|9
171.25.193.25|9
222.187.254.41|9
222.187.232.39|9
209.141.55.232|9
221.131.165.50|9
72.167.46.67|9
89.248.167.131|9
205.185.116.145|9
221.131.165.33|9
45.155.204.39|8
165.22.100.49|8
107.189.12.107|8
212.192.246.96|8
89.234.157.254|8
176.111.173.238|8
185.107.47.215|8
185.220.102.244|8
141.98.10.60|8
45.133.1.31|8
205.185.114.141|8
171.25.193.77|8
60.8.87.190|8
45.61.184.15|8
80.82.77.139|8
171.225.185.69|8
107.189.13.122|8
222.187.232.60|8
192.160.102.170|8
185.107.70.202|8
198.96.155.3|8
31.44.185.115|8
45.148.120.25|8
159.203.102.122|8
141.98.10.179|8
178.73.215.171|8
209.141.33.39|8
176.10.99.200|8
80.67.172.162|8
104.244.76.13|8
104.244.75.62|8
45.144.225.143|8
105.203.195.68|8
162.247.74.27|8
198.98.51.189|8
141.98.10.81|8
141.98.10.82|8
209.141.52.9|8
45.93.201.148|8
107.189.30.134|8
