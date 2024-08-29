---
layout: default
---

[Back Home](./index.md)


# Forage Virtual Experience - Telstra Cyberattack

Date: 8/27/2024

<br/><br/>
### Start Simulation

Before starting the simulation, I actually had to look up Telstra as I wasn't familiar with this company. Telstra is a telecomm company based in Australia with similar offerings to AT&T. With that information, I started the simulation and was immediately provided with some background information:

<br/><br/>
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

This information gave me what I needed to write up a quick professional email to our team concerning this incident. I was not aware of where this simulation was going, so this email with the patch information doesn't exactly match up well with the other tasks.  
![2024-08-27_13-21](https://github.com/user-attachments/assets/b24d71ed-b220-48fc-a06a-b8c3d5444483)

With that email sent, Task 1 was complete. In the Incident Response Lifecycle, this step (and part of step 2) would be grouped together as Detection and Analysis, so we still have some more analysis to do before we can move onto Containment, Eradication, and Recovery.

<br/><br/>
### Task 2  
![2024-08-27_13-27](https://github.com/user-attachments/assets/c575c006-f995-4769-8c4f-e336ba9c9776)  
![2024-08-27_13-28](https://github.com/user-attachments/assets/665d18fa-77d4-4408-beb4-d411c12ffb8e)  

Upon further analysis of the incident, we can determine steps to take to cut-off the immediate threat. I know the patch wasn't available at this time when Spring4Shell was first discovered, but I felt like I could work it into the email as though it was being developed and we just had to triage the situation while a permanent solution was in development. I decided to implement a firewall rule to block "/tomcatwar.jsp" from being used as a client request path.  
![2024-08-27_13-56](https://github.com/user-attachments/assets/e3ce288b-e5d3-445d-a1ec-c254a9240900)  

My solution turned out to be a little overkill though. The simulation also provided "ideal" responses for each task and I should have specified to block traffic based on the request path AND certain headers, which would have been a more targeted approach as opposed to my blanket rule.

<br/><br/>
### Task 3
![2024-08-27_14-01](https://github.com/user-attachments/assets/857f7d84-33a7-49b3-aea9-ea5b2c08ee80)  
![2024-08-27_14-01_1](https://github.com/user-attachments/assets/14c370b8-43ef-4cff-874c-8ae0161a4ed4)  

For the third task, I was to use Python to develop a firewall rule and test that rule using a simulated environment on my computer. I haven't used Python in this way before and so I unsure how long this would take me, but I knew I would make it happen. Thankfully, the task gave a basic template to run the http server and test attack program (though Microsoft Defender did not like me downloading that zip file) and Python has awesome resources online.

After some research and plenty of trial and error, I came up with the following code:  
![2024-08-27_15-53](https://github.com/user-attachments/assets/396e42fb-d418-4d71-b9a6-266b7c64e494)

And the results from the attack run...  
![2024-08-27_15-52](https://github.com/user-attachments/assets/7674967c-817a-46f5-8fe5-efea1223e5f7)  
![2024-08-27_15-52_1](https://github.com/user-attachments/assets/ca3d89e7-034b-4a42-8b93-57e4c437950a)  

My code was successful. Yay! However, like mentioned previously, there was a better way. The below code was provided after completing the task. You can see that they define a list of bad headers, then if a client requests the "/tomcatwar.jsp" path, the loop runs to determine if any of the bad headers are a match before blocking the traffic. They also used a 403 error code instead of 401 like I did.  
![2024-08-27_16-03](https://github.com/user-attachments/assets/002f26b7-9967-46a9-8f99-f30335101842)  

<br/><br/>
### Task 4

Task 4 corresponds to step 4 in the NIST Incident Response Lifecycle. We perform a Postmortem or Lessons learned exercise to break down the various steps of response process, further analyze the situation and determine if any changes need to be made to the organization's infrastructure or employed frameworks.

For this task, I was given a template, which was helpful, but the details took a while to write out by myself.  
![2024-08-27_16-08](https://github.com/user-attachments/assets/e22a6793-e90e-44f2-8f93-d2a8688cb11e)  
![2024-08-27_16-55](https://github.com/user-attachments/assets/d332ac37-cdf6-496a-90cf-1b11dbfeef31)  

Here is the "ideal response" provided by the module once completed:  
![2024-08-29_10-38](https://github.com/user-attachments/assets/ae0f1114-e6cb-4230-abfb-33b45c032652)  
![2024-08-29_10-38_1](https://github.com/user-attachments/assets/885d1833-eda5-4fab-9f75-1c61378bc581)  

<br/><br/>
# Summary

I really enjoyed this module. It challended me and made me feel more confident in my ability to learn new things and navigate the cybersecurity space. I can't wait to tackle other modules on Forage.

<br/><br/>
[Back Home](./index.md)
