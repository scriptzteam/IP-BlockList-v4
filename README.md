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
Wall of shame (2021-10-14)
----

|IP|Number of (black)lists|
|---|--:|
165.22.100.49|9
185.73.124.100|9
185.31.175.228|8
128.31.0.13|8
188.166.74.91|8
205.185.121.149|8
89.234.157.254|8
176.111.173.237|8
178.73.215.171|8
95.172.47.98|8
171.245.46.121|8
188.166.111.236|8
199.195.251.49|8
107.189.30.134|8
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
Wall of shame (2021-10-14)
----

|IP|Number of (black)lists|
|---|--:|
165.22.100.49|9
185.73.124.100|9
185.31.175.228|8
128.31.0.13|8
188.166.74.91|8
205.185.121.149|8
89.234.157.254|8
176.111.173.237|8
178.73.215.171|8
95.172.47.98|8
171.245.46.121|8
188.166.111.236|8
199.195.251.49|8
107.189.30.134|8
165.22.100.49|9
185.73.124.100|9
141.98.10.60|9
179.43.141.99|9
209.141.53.99|9
185.73.124.253|9
171.25.193.20|9
199.195.253.199|9
141.98.10.82|9
185.31.175.228|8
128.31.0.13|8
188.166.74.91|8
205.185.121.149|8
89.234.157.254|8
176.111.173.237|8
178.73.215.171|8
95.172.47.98|8
171.245.46.121|8
188.166.111.236|8
185.220.102.243|8
198.98.54.17|8
221.131.165.65|8
206.189.6.143|8
209.141.40.193|8
185.220.101.42|8
80.82.77.139|8
212.193.30.32|8
221.181.185.94|8
167.172.41.24|8
205.185.124.141|8
185.220.100.253|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
141.98.10.121|8
199.19.224.76|8
107.189.31.248|8
209.141.54.35|8
198.98.48.67|8
77.247.181.163|8
60.170.247.162|8
93.174.95.106|8
179.43.175.26|8
221.131.165.33|8
209.141.55.247|8
222.187.238.58|8
171.25.193.25|8
209.141.47.39|8
199.195.251.49|8
212.193.30.101|8
178.62.212.82|8
198.98.52.12|8
221.131.165.75|8
80.67.172.162|8
209.141.55.232|8
221.131.165.50|8
199.19.226.4|8
178.62.232.188|8
116.110.124.53|8
89.248.167.131|8
222.187.232.39|8
212.193.30.64|8
205.185.116.226|8
117.248.249.70|8
199.195.248.44|8
141.98.10.81|8
107.189.30.134|8
