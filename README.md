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
Wall of shame (2021-10-05)
----

|IP|Number of (black)lists|
|---|--:|
141.98.10.60|10
198.98.52.69|10
60.8.87.190|10
171.225.185.69|10
104.244.79.215|10
179.43.141.99|10
198.98.50.192|10
185.73.124.253|10
205.185.118.82|10
117.248.249.70|10
141.98.10.81|10
141.98.10.82|10
45.155.204.39|9
205.185.121.149|9
185.73.124.100|9
221.131.165.65|9
198.98.58.250|9
45.133.1.35|9
107.189.3.160|9
209.141.51.168|9
171.25.193.77|9
209.141.53.166|9
107.189.1.85|9
221.181.185.94|9
185.100.87.72|9
107.189.31.248|9
198.98.53.184|9
60.170.247.162|9
179.43.175.26|9
221.131.165.33|9
209.141.55.247|9
222.187.238.58|9
171.25.193.25|9
212.193.30.101|9
221.131.165.75|9
222.187.232.39|9
209.141.55.232|9
221.131.165.50|9
199.195.254.38|9
176.10.99.200|9
107.189.30.211|9
45.93.201.148|9
45.95.169.176|9
185.31.175.228|8
185.31.175.226|8
185.31.175.220|8
148.72.245.63|8
107.189.12.107|8
212.192.246.96|8
5.183.209.217|8
89.163.249.244|8
89.234.157.254|8
176.111.173.238|8
176.111.173.237|8
199.195.252.247|8
162.247.74.27|8
162.247.74.74|8
5.2.69.50|8
45.133.1.31|8
107.189.8.8|8
45.148.123.3|8
171.25.193.78|8
45.133.1.14|8
45.153.160.2|8
209.141.32.151|8
80.82.77.139|8
35.240.229.94|8
5.199.143.202|8
192.160.102.170|8
192.42.116.16|8
141.98.10.121|8
185.31.175.252|8
5.104.110.89|8
107.189.13.161|8
199.195.248.37|8
45.153.160.140|8
77.247.181.165|8
77.247.181.163|8
167.172.43.25|8
45.133.1.3|8
198.98.51.254|8
209.141.53.99|8
185.220.103.5|8
185.220.102.4|8
185.31.175.235|8
185.31.175.231|8
162.247.74.217|8
178.73.215.171|8
171.25.193.20|8
222.187.254.41|8
213.202.216.189|8
185.220.102.254|8
80.67.172.162|8
45.61.187.251|8
45.61.186.176|8
64.113.32.29|8
107.189.13.122|8
185.31.175.207|8
185.31.175.215|8
45.153.160.133|8
45.153.160.136|8
45.153.160.135|8
45.153.160.139|8
75.119.155.12|8
185.31.175.243|8
185.31.175.240|8
185.31.175.247|8
64.227.65.76|8
185.100.87.202|8
