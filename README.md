# 🛡️ Splunk DNS Log Analysis

A hands-on Splunk lab for analyzing **DNS logs**, identifying top domains, active hosts, query types, and detecting anomalies such as suspicious domains, failed lookups, and high-risk DNS behavior—designed to build practical SOC investigation skills.
---

## 🎯 Objective  
- To ingest and parse Zeek-style DNS logs in Splunk. 
- To identify frequently queried domains and active client hosts. 
- To analyze DNS query types such as A, AAAA, CNAME,TXT and PTR. 
- To detect anomalies like failed resolutions, suspicious domains, and unusual query patterns.
- To strengthen SOC investigation skills using SPL queries and DNS behavioral analysis.
  
---

## 🧩 Lab Setup  
- **Tool:** Splunk cloud  
- **index:** `main`  
- **source:** `dns_lab`  
- **Sourcetype:** `dns`  

---

## ⚙️ Task 1: Searching DNS Events  

### 🕵️ Retrieve all DNS logs  
```spl
index=main sourcetype="dns"
```

---

## 📊 Task 2: Identify the most frequently queried domain names  

### 🔹 If one domain suddenly appears in the top 10, and it’s unknown or suspicious → possible malware beaconing.
```spl
index="main" sourcetype="dns"
| stats count by query
| sort -count
```

---

## ⚠️ Task 3: Find the most active user IPs generating DNS traffic  
```spl
index="main" sourcetype="dns"
| stats count by "id.orig_h"
| sort -count
```

---

## ⚠️ Task 4: Breakdown of DNS query types 

### 🔹 If an endpoint is making many TXT, NULL, or MX queries:→ Potential tunneling / malware activity
```spl
index="main" sourcetype="dns"
| stats count by qtype

```

---

## 🖼 Dashboard Screenshots 

![image alt](https://github.com/sudarsan143/Splunk-DNS-Log-Analysis/blob/f7c18c6e9dc9720d3434450a3dc728e8c4f3c675/active%20user%20IPs%20generating%20DNS%20traffic.png)
![image alt](https://github.com/sudarsan143/Splunk-DNS-Log-Analysis/blob/f7c18c6e9dc9720d3434450a3dc728e8c4f3c675/queried%20domain%20names.png)
![image alt](https://github.com/sudarsan143/Splunk-DNS-Log-Analysis/blob/f7c18c6e9dc9720d3434450a3dc728e8c4f3c675/active%20user%20IPs%20generating%20DNS%20traffic.png)


---



---

## 🏁 Conclusion  
This project enabled me to deepen my SOC analysis skills by:  
- This project provided hands-on experience in ingesting and analyzing DNS logs using Splunk SIEM.
- I successfully identified top queried domains, active client hosts, and DNS record type distributions.
- The analysis helped uncover potential anomalies such as failed lookups, suspicious domains, and unusual DNS behavior.
- Through SPL queries, I gained deeper understanding of DNS patterns useful for threat detection and SOC investigations.
- Overall, this lab strengthened my blue-team skills and enhanced my ability to monitor, investigate, and detect DNS-based threats in an enterprise environment.

---


---

## 🔖 Tags  
`#Splunk` `#CyberSecurity` `#SOC` `#SIEM` `#DNSLogs` `#ThreatDetection` `#BlueTeam` `#HandsOnLearning`

