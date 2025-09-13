# Scenario Overview - Web Defacement

**Description**  
Today is Alice's first day at the Wayne Enterprises' Security Operations Center.  
Lucius sits Alice down and gives her first assignment: A memo from Gotham City Police Department (GCPD).  
Apparently, GCPD has found evidence online ([pastebin link](http://pastebin.com/Gw6dWjS9)) that the website  
[www.imreallynotbatman.com](http://www.imreallynotbatman.com) hosted on Wayne Enterprises' IP address space  
has been compromised.

The attacker group has multiple objectives, but a key aspect of their modus operandi  
is to deface websites in order to embarrass their victim.  
Lucius has asked Alice to determine if Wayne Enterprises’ CEO’s personal blog  
([www.imreallynotbatman.com](http://www.imreallynotbatman.com)) was really compromised.


**Log Sources Used**  
- Web logs  
- Proxy logs  
- DNS logs (`stream:dns`)  
- HTTP stream logs (`stream:http`)  
- FortiGate (FGT) firewall logs  
- Gotham City Police Department memo  

**Resources**  
- Splunk server: https://gettingstarted.splunk.show  
- Credentials: `user001-splk / Splunk.5`  
- Bots v1 sourcetype summary: https://botscontent.netlify.app/v1/bots_sourcetypes.html  
- Splunk quick reference guide: https://www.splunk.com/pdfs/solution-guides/splunk-quick-reference-guide.pdf  
- GCPD Poison Ivy memo: https://botscontent.netlify.app/v1/gcpd-poisonivy-memo.html  
- Alice’s journal: https://botscontent.netlify.app/v1/alice-journal.html  
- Mission document: https://botscontent.netlify.app/v1/mission_document.html  


**Questions Covered**  
- Q101 → Q109 (note: Q107 is missing in dataset)

**Note**  
All logs used for this investigation come directly from the Splunk BOTS v1 dataset:  
- `stream:http`, `stream:dns` for network traffic  
- Proxy logs for web access  
- FortiGate logs for firewall context  
- Additional memo/evidence provided by GCPD  
