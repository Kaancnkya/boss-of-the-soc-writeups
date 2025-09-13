# Question

What is the likely IPv4 address of someone from the Po1s0n1vy group scanning imreallynotbatman.com for web application vulnerabilities?


## Investigation Process

1. **Scenario briefing**  
   The task was to identify the attacker’s IP address scanning the domain `imreallynotbatman.com`.  

   ![Scenario briefing](evidence/0.png)

2. **Index and sourcetype check**  
   Within the `botsv1` index, sourcetypes such as `fgt_event`, `fgt_traffic`, `fgt_utm`, `stream:http`, and `suricata` were observed.  
   These sourcetypes contain web traffic and IDS/IPS data, which are critical for identifying attacker activity.  

   ![Sourcetype overview](evidence/1.png)  
   ![Sourcetype listing](evidence/2.png)  
   ![Sourcetype listing continued](evidence/3.png)
   ![Additional sourcetypes](evidence/4.png)  
   ![Final sourcetype check](evidence/5.png)

3. **Domain-specific search**  
   Query:  index=botsv1 sourcetype=fgt* “imreallynotbatman.com”

Suspicious access logs were found. The field `srcip` highlighted **40.80.148.42**.  

![Domain search result](evidence/6.png)
   ![Additional domain evidence](evidence/7.png)

4. **SrcIP frequency analysis**  
Compared to other IPs, **40.80.148.42** generated ~91% of all requests.  
Another IP, **23.22.63.114**, appeared but its activity was much lower.  

![Frequency analysis](evidence/8.png)  
![Request volume](evidence/9.png)

5. **Correlation – blocked events**  
Filtering with `action="blocked"` confirmed that **40.80.148.42** was blocked due to suspicious activity.  

![Blocked events](evidence/10.png)

6. **Detailed event review**  
- User-Agent contained **acunetix_wvs_security_test** (vulnerability scanner).  
- URI paths like `/joomla/index.php` showed exploit attempts.  
- Suricata alerts flagged **XSS, SQL Injection, XXE, and Host Header Injection**.  

![Event detail 1](evidence/11.png)  
![Event detail 2](evidence/12.png)  
![Event detail 3](evidence/13.png)  
![Event detail 4](evidence/14.png)  
![Event detail 5](evidence/15.png)

7. **Final correlation**  
Suricata queries directly tied multiple attack signatures to **40.80.148.42**, confirming it as the attacker’s IP.  

![Suricata alerts](evidence/16.png)  
![Additional Suricata correlation](evidence/17.png)  
![Attack signature detail](evidence/18.png)  
![Final validation](evidence/19.png)


## Answer

**40.80.148.42**


## Evidence

All screenshots are stored in the `evidence/` folder (`0.png – 19.png`).



## Conclusion

The vulnerability scanning activity associated with the **Po1s0n1vy group** was traced back to **40.80.148.42**.  
This IP was confirmed through both **Fortigate (`fgt_utm`) logs** and **Suricata IDS alerts**, consistently linking it to malicious probing and exploitation attempts against `imreallynotbatman.com`.
