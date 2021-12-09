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
Wall of shame (2021-12-09)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.77|10
45.88.137.253|10
141.98.10.246|10
205.185.120.71|10
171.25.193.25|10
185.31.175.215|10
136.144.41.139|9
23.183.81.249|9
176.111.173.237|9
116.105.77.214|9
162.247.74.74|9
141.98.10.63|9
104.248.85.104|9
116.235.94.247|9
23.183.81.136|9
212.192.241.124|9
185.220.100.254|9
185.130.44.108|9
212.192.241.37|9
222.187.238.58|9
23.183.82.135|9
38.91.102.77|9
205.185.115.39|9
195.133.18.24|9
221.131.165.75|9
185.220.102.253|9
185.220.102.250|9
64.113.32.29|9
221.131.165.50|9
209.141.34.220|9
185.100.87.129|9
104.244.76.13|9
209.141.47.245|9
23.183.82.180|9
134.209.95.47|9
37.123.163.58|9
167.172.43.16|9
209.141.53.74|9
89.163.252.230|8
185.31.175.228|8
185.31.175.226|8
185.31.175.220|8
20.206.86.43|8
80.82.77.33|8
162.247.74.206|8
134.209.198.229|8
199.249.230.163|8
58.222.83.94|8
89.234.157.254|8
23.129.64.138|8
23.129.64.136|8
185.107.47.215|8
38.91.102.46|8
45.144.225.119|8
185.220.102.244|8
185.220.102.246|8
185.220.102.243|8
195.133.18.104|8
185.83.214.69|8
205.185.114.149|8
171.25.193.78|8
185.107.47.171|8
18.27.197.252|8
212.192.241.95|8
45.154.255.147|8
134.209.205.40|8
23.183.81.116|8
165.22.195.82|8
178.20.55.18|8
192.160.102.170|8
185.220.100.252|8
195.254.135.76|8
185.100.87.72|8
185.165.168.229|8
192.42.116.16|8
166.70.207.2|8
134.209.195.231|8
185.220.102.4|8
23.183.81.227|8
199.249.230.119|8
23.129.64.146|8
137.184.51.62|8
185.243.218.50|8
185.31.175.231|8
143.198.136.88|8
221.131.165.33|8
162.247.74.216|8
162.247.74.217|8
162.247.74.213|8
45.153.160.2|8
185.100.86.74|8
171.25.193.20|8
176.10.104.240|8
167.71.10.210|8
185.38.175.132|8
185.67.82.114|8
80.67.172.162|8
209.141.42.136|8
116.110.252.176|8
185.165.171.175|8
179.43.187.37|8
163.172.213.212|8
185.56.80.65|8
72.167.48.55|8
23.129.64.140|8
185.31.175.207|8
176.10.99.200|8
23.183.81.54|8
45.153.160.130|8
69.49.244.54|8
185.220.100.240|8
45.88.137.100|8
162.247.72.199|8
185.31.175.243|8
185.31.175.240|8
185.31.175.247|8
221.181.185.111|8
137.184.49.88|8
117.248.249.70|8
94.153.161.234|8
107.189.8.65|8
