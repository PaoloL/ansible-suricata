# Suricata on Amazon EC2
Suricata is an open source threat detection engine that combines intrusion detection (IDS), intrusion prevention (IPS), network security monitoring (NSM) and PCAP processing.
We can use Suricata for threat detection by leveraging the VPC Traffic Mirroring Feature. 
By Traffic Mirroring a copy of Amazon VPC traffic flows is sent to a set of EC2 instances (behind an NLB) with Suricata engine aboard.

## Install Suricata on Amazon Linux 2

### Suricata Common Vars
```home_net``` ip-address(es) of your local network

```default_conf_dir``` where configuration files are (ex /etc/suricata)

```default_log_dir``` where log files are (ex /var/log/suricata)

### Suricata Logging
In the /var/log/suricata directory, all of Suricata’s output (alerts and events) will be stored.
- Line based alerts logs (**fast.log**): this log contains alerts consisting of a single line
- Extensible Event Format logs (**eve.json**): this is an JSON output for alerts and events.
- Engine statistics logs (**stats.log**): this log contain engine statistics such as packet counters or memory use counters

### Execute Playbook
The Playbook has 3 tasks:
1. Prepare: prepare hosts to installation
2. Install: install Suricata and Apache Web Server
3. Configure: configure Suricata and Apache

To launch playbook

```ansible-playbook -i hosts --private-key <key> main.yaml```



