# Suricata (IDS/IPS) + Snort (with Oinkcode rules) + Watchdog / monitoring + SIEM

![pfsense](/Task06-SURICATA-IDS/assets/01.png)

![pfsense](/Task06-SURICATA-IDS/assets/02.png)

![pfsense](/Task06-SURICATA-IDS/assets/02-1.png)

![pfsense](/Task06-SURICATA-IDS/assets/03.png)

![pfsense](/Task06-SURICATA-IDS/assets/04.png)

![pfsense](/Task06-SURICATA-IDS/assets/05.png)

![pfsense](/Task06-SURICATA-IDS/assets/06.png)

![pfsense](/Task06-SURICATA-IDS/assets/07.png)

![pfsense](/Task06-SURICATA-IDS/assets/08.png)

![pfsense](/Task06-SURICATA-IDS/assets/08-1.png)

![pfsense](/Task06-SURICATA-IDS/assets/09.png)

![pfsense](/Task06-SURICATA-IDS/assets/10.png)

![pfsense](/Task06-SURICATA-IDS/assets/11.png)

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

![pfsense](/Task06-SURICATA-IDS/assets/12.png)

![pfsense](/Task06-SURICATA-IDS/assets/13.png)

![pfsense](/Task06-SURICATA-IDS/assets/14.png)

```sh
# Suppression syntax
[ALERT] WAN - Ping detected a pfSense
suppress gen_id 1, sig_id 100001, track by_src, ip 192.168.129.4
```

![pfsense](/Task06-SURICATA-IDS/assets/15.png)

![pfsense](/Task06-SURICATA-IDS/assets/16.png)

![pfsense](/Task06-SURICATA-IDS/assets/17.png)

```sh
# Official rules download
https://snort.org/downloads#rules
```

![pfsense](/Task06-SURICATA-IDS/assets/18.png)

![pfsense](/Task06-SURICATA-IDS/assets/19.png)

![pfsense](/Task06-SURICATA-IDS/assets/20.png)

![pfsense](/Task06-SURICATA-IDS/assets/21.png)

![pfsense](/Task06-SURICATA-IDS/assets/22.png)

![pfsense](/Task06-SURICATA-IDS/assets/23.png)

![pfsense](/Task06-SURICATA-IDS/assets/24.png)

![pfsense](/Task06-SURICATA-IDS/assets/25.png)

![pfsense](/Task06-SURICATA-IDS/assets/26.png)

![pfsense](/Task06-SURICATA-IDS/assets/27.png)

![pfsense](/Task06-SURICATA-IDS/assets/28.png)

![pfsense](/Task06-SURICATA-IDS/assets/29.png)

![pfsense](/Task06-SURICATA-IDS/assets/30.png)

![pfsense](/Task06-SURICATA-IDS/assets/31.png)

![pfsense](/Task06-SURICATA-IDS/assets/32.png)
