## How to install Sysmon on Windows and forward the logs to Splunk Enterprise

To do this, we first need to download the Sysmon installation file.

![image](https://github.com/user-attachments/assets/1b4609b5-eb3f-45ab-9501-00f62ac194cd)

When we type "sysmon download" in our internet browser, we go to the corresponding site of Microsoft.

![image](https://github.com/user-attachments/assets/18034b9a-7ae6-47cc-80dd-a5149d287fc3)

We click on the "Download Sysmon" link on this page of Microsoft and the file is downloaded with zip.
https://download.sysinternals.com/files/Sysmon.zip

![image](https://github.com/user-attachments/assets/8f748ba6-c97b-49a5-96d8-996160dad948)

We go to the location of the Sysmon file that has been downloaded to our computer, right-click on the file and say "Extract All".

![image](https://github.com/user-attachments/assets/10418c98-c6ce-4989-b603-ca3c51da51f8)

Here, by clicking the "Extract" button, we extract the files compressed in zip format to the normal folder.

![image](https://github.com/user-attachments/assets/ced5de56-4c4e-4b45-b643-7192faf74276)

 We have extracted our files to the normal folder.

![image](https://github.com/user-attachments/assets/f710babd-8312-417f-91fc-473fcd294edb)

We couldn't click and run the Sysmon installation files because they were blocked by Anti-Virus or another system. So we're going to run it through CMD. For this,  we will run CMD as Administrator.

![image](https://github.com/user-attachments/assets/92383c24-af6d-471f-adfd-eaaa89b3ab76)

Since we want to run it as Administrator, we will run CMD in Administrator mode by pressing the "Yes" button here.

![image](https://github.com/user-attachments/assets/d7441982-1612-4151-8ef5-4e635b1e75f1)

Before we can install Sysmon through CMD, we must first go to its location. To do this, we go to the corresponding location using the "cd" command.

![image](https://github.com/user-attachments/assets/8a9efc03-c81c-4c6f-939d-0bf74a64d548)

For the installation process, we write "Sysmon.exe -i" and press Enter.

![image](https://github.com/user-attachments/assets/fb3a6c76-f019-4112-a3ab-792b444bf87d)

If we see this screen, the Sysmon installation process is complete.

Now we download the Sysmon Configuration  file with the xml extension we need and install it with the sysmon.exe -accepteula -i <file name> command. Even if we want to upload a different file later, we  update it with the sysmon.exe -c <new file name> command.

![image](https://github.com/user-attachments/assets/2a1b2b71-47b2-4ef4-a185-2b32510c420e)

Finally,  in the Task Manager, right-click on Sysmon from the Services section  and do Restart.

![image](https://github.com/user-attachments/assets/476110ee-8d37-4a81-a043-53e5641fd25f) 

© Splunk Inc.

To check if all these processes are working properly, we go to Splunk Enterprise and  ask it to fetch all the Logs by typing the * sign on the query screen.

![image](https://github.com/user-attachments/assets/b0a7876d-ec5b-4f38-8fc7-cb76cd45d8d8) © Splunk Inc.

 If the log comes from the devices we have installed Splunk Universal Forwarder from the results, the device names should appear in the "host" section.

![image](https://github.com/user-attachments/assets/c439c1e4-4816-4210-8eb2-828f686ff73a) © Splunk Inc.

 From the results, we can see the Log types from the devices we have installed Splunk Universal Forwarder in the "source" or "sourcetype" sections. As you can see from here, all the Logs we have set, including Sysmon Logs, are coming.


### In  order to perform more and different queries in Splunk, we may need different Logs to be transferred. For example; Defender Logs...

![image](https://github.com/user-attachments/assets/c3daa624-070d-4b96-abe8-1e586b0de5a3)

In such a case, we need to access the "inputs.conf" file of the Splunk Universal Forwarder of our computer, which we need different logs, and add it to the list for the new Log type we want.
For this process, we first need to run the Notepad program as Administrator. 

![image](https://github.com/user-attachments/assets/aa265a44-26d2-467b-9d5a-b0e0a27ce0c5)

Since we want to run it as Administrator, we will run Notepad in Administrator mode by pressing the "Yes" button here.

![image](https://github.com/user-attachments/assets/d3385f73-1eb3-4f5d-b812-7085fe9eeec1)

In the Notepad program that opens, click on the File tab in the upper left section  and click Open from the menu that opens.

![image](https://github.com/user-attachments/assets/ee6dd3a0-cad8-40aa-83b5-c6843c359ad3)

From this window that opens, we go to the location of the inputs.conf file where we will define new types of logs.

![image](https://github.com/user-attachments/assets/7fa47c02-b0bb-45f7-ad8e-2e0728ae836a)

C:\Program Files\SplunkUniversalForwarder\etc\apps\SplunkUniversalForwarder\local

In order to see the file, the file type section above the Open button at the bottom right must be selected as "All Files".

![image](https://github.com/user-attachments/assets/95a98c04-349a-4e6a-b1aa-dc9a77020b44)

We add and subtract the logs we want to this file.

![image](https://github.com/user-attachments/assets/f0ea5c8a-139b-45fe-b23d-50c4314db0d7)

We click on the cross at the top right to save the changes we have made and press the "Save" button for the changes to be saved.

![image](https://github.com/user-attachments/assets/24003f1f-1e92-43af-966c-d3d1c5015f52)

In order to implement the changes we have made, we need to Restart the Splunk Forwarder from the Services section in the Task Manager.

### * Now, to monitor our system more effectively, we need to create dashboards for several use cases based on the logs collected by Splunk Universal Forwarder and sent to Splunk Enterprise.

- [Splunk Use Cases & Dashboards](https://github.com/ademataydir/splunk-use-cases)

### Note
This content has been prepared for personal learning purposes related to the installation of Splunk software. All screenshots and software are the property of Splunk Inc. This page is not intended for commercial use.
