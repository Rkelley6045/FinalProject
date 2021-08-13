# Blue Team: Summary of Operations

## Table of Contents
- Network Topology
- Description of Targets
- Monitoring the Targets
- Patterns of Traffic & Behavior
- Suggestions for Going Further

### Network Topology

The following machines were identified on the network:
- Name of VM 1: `Elk machine`
  - **Operating System**: Linux
  - **Purpose**: Elk setup that holds the Kibana dashboards
  - **IP Address**: `192.168.1.100`
- Name of VM 2: `Kali`
  - **Operating System**: Linux 2.6.32
  - **Purpose**: Standared Kali Linux machine used for penetration test on Day 1
  - **IP Address**: `192.168.1.90`
- Name of VM 3: `Capstone`
  - **Operating System**: Linux
  - **Purpose**: Testing alerts via the Filebeat and Metricbeat installed on the machine
  - **IP Address**: `192.168.1.105`
- Name of VM 4: `Target 1`
  - **Operating System**: 3.2 - 4.9
  - **Purpose**: Exposes a vulnerable WordPress server
  - **IP Address**: `192.168.1.110`

### Description of Targets

The target of this attack was: `Target 1` `192.168.1.110`.

Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

#### Name of Alert 1
`Excessive HTTP Errors` Alert is implemented as follows:
  - **Metric**: HTTP response code count
  - **Threshold**: 400 ,and above, response status code for the last 5 minutes
  - **Vulnerability Mitigated**: Unauthorized user access
  - **Reliability**: High reliability 

#### Name of Alert 2
`HTTP Request Size Monitor` Alert is implemented as follows:
  - **Metric**: Sum count
  - **Threshold**: Size of http request bytes for all documents above 3500 for the last minute
  - **Vulnerability Mitigated**: HTTP request smuggling
  - **Reliability**: High reliabiility

#### Name of Alert 3
`CPU Usage Monitor` Alert is implemented as follows:
  - **Metric**: Max percentage
  - **Threshold**: Percent of total CPU system process above 0.5 for the last 5 minutes
  - **Vulnerability Mitigated**: Malicious software and viruses
  - **Reliability**: High reliability

_TODO Note: Explain at least 3 alerts. Add more if time allows._

### Suggestions for Going Further (Optional)
_TODO_: 
- Each alert above pertains to a specific vulnerability/exploit. Recall that alerts only detect malicious behavior, but do not stop it. For each vulnerability/exploit identified by the alerts above, suggest a patch. E.g., implementing a blocklist is an effective tactic against brute-force attacks. It is not necessary to explain _how_ to implement each patch.

The logs and alerts generated during the assessment suggest that this network is susceptible to several active threats, identified by the alerts above. In addition to watching for occurrences of such threats, the network should be hardened against them. The Blue Team suggests that IT implement the fixes below to protect the network:
- Vulnerability 1
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
- Vulnerability 2
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
- Vulnerability 3
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
