---
layout: default
---

[Back Home](./index.md)


# Forage Virtual Experience - Telstra Cyberattack

Date: 8/27/2024

<br/><br/>
### Start Simulation

Before starting the simulation, I actually had to look up Telstra as I wasn't familiar with this company. Telstra is a telecomm company based in Australia with similar offerings to AT&T. With that information, I started the simulation and was immediately provided with some background information:

### Task 1  
![2024-08-27_12-56](https://github.com/user-attachments/assets/50dafd9f-bd1a-4d86-a76c-55a2f04c7cff)  
![2024-08-27_12-57](https://github.com/user-attachments/assets/89078adf-a06e-43d8-acb1-856e257baa8f)  

I was also given references, a log file, and an email template to work from.  
![2024-08-27_12-57_1](https://github.com/user-attachments/assets/b0f707c4-19dd-44c9-9667-c5fe6cc7d027)  

I've heard of Spring4Shell elsewhere in learning about CVEs, but I definitely needed the provided references to be able to complete this task. I learned that Spring4Shell (CVE-2022-22965) is a zero-day RCE vulnerability and requires specific conditions: JDK 9+, Apache Tomcat, WAR file format, spring-webmvr or spring-webflux dependencies, and Spring Framework 5.3.17 or ealier (for those using the 5.3 framwork).

With the necessary background information on the vulnerability, my first task was to write up an email to the affected team letting them know we identified the reason for the service disruption, the critical nature of the incident, and what is being done to fix the issue. Identifying the details of the incident and the affected team was done by looking through the provided firewall and infrastructure document.  
![2024-08-27_13-04](https://github.com/user-attachments/assets/f6d09fa0-ec1a-450d-912e-3e071db0f320)  
![2024-08-27_13-05](https://github.com/user-attachments/assets/7d7df62a-6df0-479f-8b9f-696bc7813d04)  
![2024-08-27_13-05_1](https://github.com/user-attachments/assets/4728f51c-51b6-4e80-863b-b66df1d619cf)  

This information gave me what I needed to write up a quick professional email to our team concerning this incident.  
![2024-08-27_13-21](https://github.com/user-attachments/assets/b24d71ed-b220-48fc-a06a-b8c3d5444483)

With that email sent, Task 1 was complete. In the Incident Response Lifecycle, this step (and part of step 2) would be grouped together as Detection and Analysis, so we still have some more analysis to do before we can move onto Containment, Eradication, and Recovery.

### Task 2  
![2024-08-27_13-27](https://github.com/user-attachments/assets/c575c006-f995-4769-8c4f-e336ba9c9776)  
![2024-08-27_13-28](https://github.com/user-attachments/assets/665d18fa-77d4-4408-beb4-d411c12ffb8e)  

Upon further analysis of the incident, we can determine steps to take to cut-off the immediate threat. I know the patch wasn't available at this time when Spring4Shell was first discovered, but I felt like I could work it into the email as though it was being developed and we just had to triage the situation while a permanent solution was in development. I decided to implement a firewall rule to block "/tomcatwar.jsp" from being used as a client request path.  
![2024-08-27_13-56](https://github.com/user-attachments/assets/e3ce288b-e5d3-445d-a1ec-c254a9240900)  

My solution turned out to be a little overkill though. The simulation also provided "ideal" responses for each task and I should have specified to block traffic based on the request path AND certain headers, which would have been a more targeted approach as opposed to my blanket rule.

<br/><br/>
[Back Home](./index.md)
