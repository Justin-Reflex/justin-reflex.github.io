---
layout: default
---

[Back Home](./index.md)


# Python Scripting to Update & PDF Documents

Date: 8/30/2024

Background: My company's corporate headquarters just moved to a new street address. Part of my responsibilities include keeping all of our documentation updated. The first task I set for myself was to update the company address on the all templates/forms we use, which was quick and easy using brute-force. The not-so-easy task was to then update all existing documentation to the new address (archived documents and completed forms/reports are not included in this update). To give some perspective, we have over 500 materials that I need to have current documentation on. Not counting Spec sheets (1 per material) and Certificates of Analysis (dozens per material), there are 2743 docx regulatory files that need to be updated and converted to pdf.

The Solution: Automate the update with a python script.

Before I get to the script, I must admit that haven't done this before. My experience with Python so far has been limited to courses I've taken to learn about cybersecurity. However, I do have some experience with programming in Objective C, C#, and the visual scripting used in Unreal Engine, and so I'm very familiar with researching code snippets and adapating to my own project. 

Besides importing the necessary libraries, the first part defines the directory variables I used. I adapted my code from a python tutorial on automatically finding and replacing text: [YouTube Tutorial by Coding is Fun](https://www.youtube.com/watch?v=cUUjkEgnCjs).  
![image](https://github.com/user-attachments/assets/d9ac5021-9a9d-407a-babf-a12ac5167381)  

Additional variables are needed for the find/replace function, including the variables to identify what to find and what to replace.  
![image](https://github.com/user-attachments/assets/d2fd89d5-aca3-42bb-a956-6d311eb44ac4)  

Additional settings/variables are set before the script can actually work.  
![image](https://github.com/user-attachments/assets/2e658765-cdbb-4739-a4aa-fea3c820af52)  

Once everything is set, a for loop is called to itterate through all ".doc" and ".docx" files in the input_dir:  
![image](https://github.com/user-attachments/assets/7f96c0e5-b8a0-4338-9e4f-0a8cf98c1f3a)  

Within that for loop, we have our find/replace functions. The first set is looking for the address I specified in the code with either "St." (find_str) or "Street" (find_str2) and then replace with the variable replace_with. However, this doesn't fully solve my problem as you'll see by the next set of find/replace functions.  
![image](https://github.com/user-attachments/assets/09d4de4c-84bc-4849-a968-cdf70b321e0d)  

The first set only looks for matching text within the body of the document. It doesn't search text boxes or headers and footers. We don't use text boxes, so I didn't initially include that function in my script. We do include information such addresses in our footers though. This was a painful issue and I was unable to find any code snippet from other developers that would address this issue. The solution is simple, but it took a while to find it. I know word views the header/footer as a different section/window pane, so I tried to manually change the active pane, but it didn't seem to work. Ultimately, I looked up Micorosoft's Office VBA Reference and adapted the VBA code to python script, which I already had a primer of thanks to the YT tutorial. So I came up with the below and it worked perfectly.  
![image](https://github.com/user-attachments/assets/10a89dcd-ec39-4ffb-ae10-941f4114e922)  

Finally, with those changes in place, we save the docx and pdf files to the designated location and quit Word.  
![image](https://github.com/user-attachments/assets/ae60e8ec-aae3-43ac-854c-fb3de0db80c9)  

If you're wondering, there are some instances where I might want to designate a different file path, which is why I want to keep the pathing variables and keep the word_app SaveChanges set to false. I also duplicated the same script and took out everything except the pdf conversion. I occassionally need to pdf several documents and the Adobe solution built in Windows is just so clunky.

I really enjoyed working on this. It took me a full day to research and finalize this script. However, I can now update and pdf 300 documents in approximately 5 minutes. I'd say this was well worth it. I could have set the script to run on all documents in all folders, but I like the compartmentalizing. I much prefer running a script 20 times for 1-5 minutes each than running it once for 100 minutes. There's less likelihood of something going wrong and if something did happen, then it would be much easier to recover.

<br/><br/>
[Back Home](./index.md)
