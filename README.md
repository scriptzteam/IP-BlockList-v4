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
Wall of shame (2021-09-21)
----

|IP|Number of (black)lists|
|---|--:|
141.98.10.179|10
222.187.254.41|10
222.187.232.39|10
60.170.247.162|9
222.187.227.122|9
107.189.3.160|9
199.195.254.38|9
199.195.252.247|9
64.113.32.29|9
107.189.8.8|9
171.25.193.77|9
221.131.165.40|9
45.133.1.14|9
209.141.32.151|9
221.181.185.94|9
206.189.104.122|9
45.153.160.133|9
222.187.232.60|9
141.98.10.125|9
199.195.248.37|9
209.141.55.232|9
221.131.165.33|9
185.31.175.226|8
185.31.175.220|8
209.141.59.252|8
198.98.51.254|8
209.141.46.14|8
176.111.173.156|8
209.141.55.247|8
107.189.4.119|8
209.141.57.50|8
171.25.193.25|8
185.107.47.215|8
205.185.127.100|8
209.141.32.215|8
185.220.102.248|8
205.185.125.45|8
81.161.63.100|8
213.202.216.189|8
185.220.102.254|8
80.67.172.162|8
8.209.91.186|8
105.203.195.68|8
198.98.58.250|8
205.185.114.141|8
162.247.74.206|8
222.168.30.19|8
198.96.155.3|8
198.98.52.69|8
185.220.101.4|8
60.8.87.190|8
45.133.1.12|8
209.141.54.139|8
209.141.45.121|8
45.61.184.15|8
209.141.33.34|8
202.29.214.13|8
209.141.51.68|8
205.185.114.54|8
107.189.13.122|8
199.195.250.77|8
209.141.42.151|8
185.220.100.253|8
209.141.53.166|8
104.248.193.49|8
185.107.70.202|8
77.247.181.165|8
141.98.10.121|8
117.248.249.70|8
107.189.31.248|8
179.43.141.99|8
199.19.226.34|8
209.141.58.77|8
185.130.44.108|8
205.185.116.145|8
209.141.62.151|8
209.141.34.36|8
185.31.175.215|8
