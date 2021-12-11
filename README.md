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
Wall of shame (2021-12-11)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.25|10
134.209.198.229|9
134.209.195.231|9
212.192.241.124|9
166.70.207.2|9
45.88.137.253|9
185.220.102.8|9
222.187.238.58|9
205.185.120.71|9
195.133.18.24|9
167.71.10.210|9
221.131.165.75|9
185.220.102.253|9
205.185.114.158|9
221.131.165.50|9
62.102.148.68|9
209.141.47.245|9
221.181.185.111|9
185.31.175.215|9
209.141.53.74|9
107.189.10.137|8
116.110.92.217|8
80.82.77.33|8
136.144.41.139|8
89.234.157.254|8
167.99.38.54|8
23.129.64.130|8
205.185.115.39|8
116.105.77.214|8
161.35.153.169|8
185.220.102.243|8
185.220.102.248|8
185.220.102.249|8
162.247.74.74|8
141.98.10.63|8
104.248.85.104|8
205.185.114.149|8
171.25.193.77|8
185.107.47.171|8
185.220.101.4|8
116.235.94.247|8
185.220.101.187|8
45.154.255.147|8
134.209.205.40|8
171.25.193.78|8
222.187.254.41|8
165.22.195.82|8
178.20.55.18|8
178.20.55.16|8
81.17.18.61|8
185.220.100.253|8
185.220.100.255|8
185.220.100.254|8
209.141.44.102|8
185.100.87.72|8
89.163.249.244|8
185.220.102.4|8
185.130.44.108|8
45.153.160.140|8
212.192.241.37|8
185.220.101.46|8
38.91.102.77|8
171.25.193.20|8
141.98.10.202|8
45.61.184.103|8
213.202.216.189|8
185.220.102.254|8
80.67.172.162|8
64.113.32.29|8
179.43.187.37|8
72.167.48.55|8
209.141.34.220|8
23.129.64.149|8
23.129.64.145|8
185.220.101.190|8
185.220.101.62|8
167.99.39.128|8
45.153.160.133|8
185.220.100.249|8
192.42.116.23|8
137.184.49.88|8
134.209.95.47|8
185.220.101.148|8
167.172.43.16|8
107.189.30.134|8
104.244.72.7|8
46.166.139.111|8
