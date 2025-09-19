```sh
# Detect ICMP Echo Requests (ping)
alert icmp any any -> 192.168.129.4 any \
(msg:"[ALERT] Ping detected to pfSense"; sid:100001; rev:3;
classtype:icmp-event; itype:8;
threshold:type limit, track by_src, count 1, seconds 10; priority:2;)

# Detect HTTP access on port 8080
alert tcp any any -> 192.168.129.4 8080 \
(msg:"[ALERT] WAN - HTTP access on port 8080 detected"; sid:100002; rev:1;
classtype:web-application-attack; flow:to_server,established;
content:"GET"; http_method;
threshold:type limit, track by_src, count 3, seconds 10; priority:3;)

# Detect SSH access on port 2222
alert tcp any any -> 192.168.129.4 2222 \
(msg:"[ALERT] WAN - SSH access on port 2222"; sid:100003; rev:2;
classtype:attempted-admin; flow:to_server,established;
content:"SSH-"; depth:4;
threshold:type limit, track by_src, count 1, seconds 10; priority:2;)

# Detect MySQL access on port 3306
alert tcp any any -> 192.168.129.4 3306 \
(msg:"[ALERT] WAN - MySQL access on port 3306"; sid:100004; rev:1;
classtype:attempted-admin; priority:2;)

# Detect Nmap scan (SYN packets)
alert tcp any any -> 192.168.129.4 any \
(msg:"[ALERT] WAN - Nmap network scan detected"; sid:100005; rev:5;
classtype:network-scan; flags:S;
threshold:type both, track by_src, count 5, seconds 10; priority:2;)
```

```sh
# Suppression syntax
[ALERT] WAN - Ping detected a pfSense
suppress gen_id 1, sig_id 100001, track by_src, ip 192.168.129.4
```

```sh
# Official rules download
https://snort.org/downloads#rules
```
