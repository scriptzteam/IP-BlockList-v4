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
Wall of shame (2021-09-20)
----

|IP|Number of (black)lists|
|---|--:|
141.98.10.125|10
199.195.252.247|10
107.189.3.160|10
107.189.8.8|10
179.43.141.99|10
199.195.248.37|10
222.187.232.39|10
222.187.232.60|10
117.248.249.70|10
209.141.59.252|9
209.141.46.14|9
141.98.10.179|9
205.185.121.160|9
209.141.54.115|9
209.141.32.215|9
209.141.54.139|9
198.98.58.250|9
199.195.254.38|9
205.185.116.145|9
198.98.52.69|9
60.8.87.190|9
209.141.45.121|9
45.61.184.15|9
209.141.33.34|9
202.29.214.13|9
221.181.185.94|9
198.98.50.192|9
209.141.51.68|9
107.189.13.122|9
104.248.193.49|9
141.98.10.121|9
107.189.31.248|9
199.19.226.34|9
209.141.58.77|9
116.98.160.162|9
60.170.247.162|9
209.141.32.151|9
222.187.227.122|9
198.98.51.254|9
221.131.165.33|9
209.141.55.247|9
222.187.254.41|9
222.168.30.19|9
205.185.114.54|9
81.161.63.100|9
209.141.34.36|9
185.31.175.220|8
5.183.209.217|8
89.234.157.254|8
209.141.57.50|8
185.107.47.215|8
205.185.127.100|8
185.220.102.244|8
185.238.72.164|8
209.141.51.168|8
171.25.193.77|8
185.107.47.171|8
221.131.165.40|8
45.133.1.14|8
45.133.1.12|8
205.185.119.103|8
209.127.17.242|8
45.153.160.129|8
81.161.63.253|8
105.203.195.68|8
176.111.173.156|8
209.141.58.53|8
205.185.121.232|8
185.100.87.129|8
209.141.37.35|8
185.220.102.4|8
107.173.209.244|8
205.185.113.185|8
209.141.47.30|8
205.185.125.45|8
206.189.104.122|8
209.141.51.176|8
8.209.91.186|8
205.185.123.106|8
64.113.32.29|8
199.195.250.77|8
199.19.225.102|8
205.185.123.199|8
209.141.62.151|8
209.141.42.151|8
149.202.238.204|8
205.185.113.236|8
205.185.117.33|8
209.141.52.46|8
205.185.119.155|8
