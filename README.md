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
Wall of shame (2021-09-25)
----

|IP|Number of (black)lists|
|---|--:|
107.189.3.160|10
107.189.8.8|10
60.8.87.190|10
209.141.53.166|10
205.185.118.82|10
104.244.79.215|10
141.98.10.125|10
198.98.53.184|10
141.98.10.179|10
209.141.32.151|10
206.189.104.122|10
209.141.52.9|10
89.234.157.254|9
107.189.4.119|9
199.195.252.247|9
198.98.58.250|9
199.195.254.38|9
209.141.51.168|9
205.185.116.145|9
198.98.52.69|9
221.131.165.40|9
221.181.185.94|9
107.189.13.122|9
222.187.232.60|9
107.189.13.161|9
104.248.193.49|9
185.107.70.202|9
141.98.10.121|9
107.189.31.248|9
198.98.50.192|9
199.195.248.37|9
60.170.247.162|9
198.98.51.254|9
221.131.165.33|9
178.73.215.171|9
45.61.184.15|9
209.141.55.247|9
171.25.193.25|9
222.187.254.41|9
64.113.32.29|9
222.187.232.39|9
209.141.55.232|9
104.244.75.62|9
81.161.63.100|9
107.189.30.211|9
45.93.201.148|9
89.163.249.244|8
41.33.61.166|8
185.107.47.215|8
89.163.249.192|8
185.220.102.243|8
162.247.74.74|8
205.185.126.99|8
171.25.193.77|8
185.107.47.171|8
103.158.147.250|8
45.133.1.14|8
185.31.175.247|8
107.189.1.85|8
80.82.77.139|8
178.20.55.16|8
192.160.102.170|8
81.161.63.253|8
179.43.141.99|8
185.220.102.4|8
176.111.173.156|8
185.130.44.108|8
45.153.160.140|8
77.247.181.163|8
104.244.74.29|8
209.141.33.39|8
171.25.193.20|8
213.202.216.189|8
45.144.225.143|8
72.167.46.67|8
185.31.175.207|8
105.203.195.68|8
117.248.249.70|8
