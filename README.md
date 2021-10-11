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
Wall of shame (2021-10-11)
----

|IP|Number of (black)lists|
|---|--:|
165.22.100.49|10
89.234.157.254|10
141.98.10.60|10
60.8.87.190|10
205.185.121.149|10
198.98.48.67|10
209.141.53.99|10
185.73.124.253|10
199.195.251.49|10
141.98.10.81|10
141.98.10.82|10
185.31.175.226|9
185.73.124.100|9
185.220.102.246|9
185.220.102.243|9
198.98.54.17|9
221.131.165.65|9
209.141.51.168|9
221.181.185.94|9
185.247.225.73|9
209.141.40.193|9
141.98.10.121|9
198.96.155.3|9
199.19.224.76|9
107.189.31.248|9
179.43.141.99|9
185.220.102.4|9
179.43.175.26|9
221.131.165.33|9
45.153.160.2|9
222.187.238.58|9
212.193.30.101|9
221.131.165.75|9
185.220.102.252|9
199.195.253.199|9
209.141.55.232|9
221.131.165.50|9
106.12.155.22|9
212.193.30.64|9
185.31.175.228|8
185.31.175.220|8
5.183.209.217|8
89.163.249.244|8
176.111.173.237|8
199.195.252.242|8
185.220.102.244|8
185.220.102.240|8
185.220.102.248|8
5.2.69.50|8
185.107.47.171|8
222.187.232.39|8
80.82.77.139|8
162.247.72.199|8
209.127.17.242|8
185.220.100.255|8
72.167.47.69|8
185.90.136.69|8
185.100.87.72|8
166.70.207.2|8
45.153.160.140|8
77.247.181.165|8
45.135.232.159|8
93.174.95.106|8
185.31.175.235|8
185.31.175.231|8
178.73.215.171|8
185.100.86.74|8
171.25.193.25|8
212.193.30.84|8
198.98.52.12|8
185.220.102.253|8
185.220.102.250|8
80.67.172.162|8
8.209.91.186|8
64.113.32.29|8
199.19.226.4|8
185.56.80.65|8
185.31.175.207|8
89.248.167.131|8
185.31.175.215|8
176.10.99.200|8
209.127.17.234|8
185.129.62.62|8
45.153.160.133|8
45.153.160.132|8
45.153.160.136|8
185.247.225.67|8
185.247.225.61|8
205.185.116.226|8
185.31.175.243|8
185.31.175.240|8
69.49.228.198|8
117.248.249.70|8
107.189.30.134|8
171.25.193.20|8
