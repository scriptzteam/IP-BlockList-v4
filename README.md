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
Wall of shame (2021-10-23)
----

|IP|Number of (black)lists|
|---|--:|
18.27.197.252|10
185.220.102.248|10
162.247.74.74|10
198.98.52.12|10
198.98.48.67|10
128.31.0.13|9
162.247.74.27|9
165.22.100.49|9
222.187.238.58|9
171.25.193.20|9
185.220.102.244|9
221.131.165.75|9
185.220.102.253|9
5.2.69.50|9
199.195.253.199|9
209.141.40.193|9
221.181.185.94|9
136.144.41.253|9
185.100.87.72|9
89.163.252.12|9
199.19.224.76|9
185.31.175.247|9
141.98.10.81|9
141.98.10.82|9
163.172.213.212|9
199.195.251.49|9
141.98.10.60|9
60.170.247.162|8
185.31.175.226|8
185.31.175.220|8
209.141.53.99|8
162.247.74.206|8
185.220.103.7|8
185.31.175.231|8
179.43.175.26|8
117.68.2.93|8
209.141.56.75|8
162.247.74.217|8
5.183.209.217|8
89.234.157.254|8
198.98.49.124|8
185.100.86.74|8
185.73.124.253|8
149.56.44.47|8
171.25.193.25|8
209.141.47.39|8
89.163.249.192|8
195.133.18.116|8
212.193.30.101|8
185.220.102.241|8
185.220.102.243|8
185.38.175.132|8
185.220.102.250|8
221.131.165.50|8
221.131.165.65|8
185.83.214.69|8
185.73.124.100|8
171.25.193.77|8
209.141.60.103|8
89.163.154.91|8
185.56.80.65|8
45.153.160.2|8
209.141.42.170|8
209.127.17.234|8
45.153.160.133|8
45.153.160.136|8
45.153.160.139|8
45.153.160.138|8
185.247.225.61|8
185.220.100.242|8
185.220.100.240|8
185.220.100.241|8
221.181.185.111|8
209.127.17.242|8
54.36.108.162|8
185.220.100.253|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
185.31.175.243|8
139.59.144.149|8
167.88.161.219|8
107.189.31.248|8
89.163.243.88|8
185.220.102.4|8
68.183.180.46|8
37.123.163.58|8
209.141.55.232|8
198.144.121.93|8
45.153.160.140|8
185.31.175.213|8
185.31.175.215|8
185.100.87.202|8
