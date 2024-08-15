<h1>Elastic SIEM LAB: Security Information and Event Management with Elastic Stack</h1>


<h2>Description</h2>
Welcome to the Elastic SIEM Home Lab repository! This project provides a step-by-step guide to setting up a Security Information and Event Management (SIEM) system using the Elastic Stack, combined with a Kali Linux virtual machine (VM). This hands-on project is ideal for those looking to enhance their skills in security monitoring and log analysis, and it's a valuable addition to your resume.
<h2>Utilities Used</h2>

- <b>Elastic SIEM</b>
- <b>Nmap</b>

<h2>Environments Used </h2>

- <b>VMware Workstation</b>
- <b>Kali</b>

<h2>Program walk-through:</h2>

<p align="center">
Set up Vmware Workstation and Kali: <br/>
<img src="https://i.imgur.com/OemPiL2.png" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sign up for a free trial to use Elastic Cloud https://cloud.elastic.co/registration:  <br/>
<img src="https://i.imgur.com/h7l03Hi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once you have an Elastic account, log in to the Elastic Cloud console:  <br/>
<img src="https://i.imgur.com/ZaGZABO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click on “Start your free trial" then Click on the “Create Deployment” button and select “Elasticsearch” as the deployment type: <br/>
<img src="https://i.imgur.com/xG9V9UX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to the Integrations page by clicking on the main menu bar at the top left, then selecting “Add Integrations” at the bottom:  <br/>
<img src="https://i.imgur.com/erppKno.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://i.imgur.com/yKq1a6K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Search for “Elastic Defend” and click on it to open the integration page and add it:  <br/>
<img src="https://i.imgur.com/kf8koie.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click on “Install Elastic Defend” and follow the instructions provided on the integration page to install the agent on your Kali VM:  <br/>
<img src="https://i.imgur.com/aA1wnln.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/UuESXtz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/QFwoSow.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/Y2jOv20.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Paste that command into the Kali terminal (command line):  <br/>
<img src="https://i.imgur.com/1iJmoZd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Once the agent is installed, which can take a few minutes, you’ll see a message saying, “Elastic Agent has been successfully installed.” It will automatically start collecting and forwarding logs to your Elastic SIEM instance, although it might take a few minutes for the logs to appear in the SIEM:  <br/>
<img src="https://i.imgur.com/OznRS02.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
You can verify that the agent has been installed correctly by running this command: sudo systemctl status elastic-agent.service:  <br/>
<img src="https://i.imgur.com/NKKntud.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
You can generate some security-related events on your Kali VM to verify that the agent is working correctly. To do this, we can use a tool like Nmap:  <br/>
<img src="https://i.imgur.com/aege6Di.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Now that we have forwarded data from the Kali VM to the SIEM, we can start querying and analyzing the logs in the SIEM, Inside your Elastic Deployment, click on the menu icon at the top-left with the three horizontal lines and then click on the “Logs” tab under “Observability” to view the logs from the Kali VM:  <br/>
<img src="https://i.imgur.com/aeeOpB9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Generated Logs:  <br/>
<img src="https://i.imgur.com/NXFKx0E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
You can create a simple dashboard that shows the number of security events over time:  <br/>
<img src="https://i.imgur.com/1KYzhcv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/GxT2eiM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Click on the “Create Visualization” button to add a new visualization to the dashboard:  <br/>
<img src="https://i.imgur.com/ns4dwKJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Select “Area” or “Line” as the visualization type, depending on your preference. This will create a chart that shows the count of events over time:  <br/>
<img src="https://i.imgur.com/WS9MIps.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
In the “Metrics” section of the visualization editor on the right, select “Count” as the vertical field type and “Timestamp” as the horizontal field. This will show the count of events over time:  <br/>
<img src="https://i.imgur.com/pze31zN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Click on the “Save” button to save the visualization and then complete the rest of the settings:  <br/>
<img src="https://i.imgur.com/WbEGNIX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Dashboard:  <br/>
<img src="https://i.imgur.com/FbuRzTg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Go back to Kali terminal and generate more data on the dashboard:  <br/>
<img src="https://i.imgur.com/O8uoo9I.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
In a SIEM, alerts are a crucial feature for detecting security incidents and responding to them promptly. Alerts are created based on predefined rules or custom queries and can be configured to trigger specific actions when certain conditions are met. In this task, we will walk through the steps of creating an alert in the Elastic SIEM instance to detect Nmap scans. By following these steps, you can create an alert that will monitor your logs for Nmap scan events and then notify you when they are detected.
Here are the steps, Click on the menu icon on the top-left, then under “Security,” click on “Alerts.”
Click on “Manage rules” at the top right:  <br/>
<img src="https://i.imgur.com/FsU4AhK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/WpXUreg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Click on the “Create new rule” button at the top right.
Under the “Define rule” section, select the “Custom query” option from the dropdown menu.
Under “Custom query,” set the conditions for the rule. You can use the following query to detect Nmap scan events:  <br/>
<img src="https://i.imgur.com/uDGKitW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/yKhbSap.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/cQOMDxj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/cBZhoRC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Integrate with other platforms:  <br/>
<img src="https://i.imgur.com/XbfaPyJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Once you’ve created the alert, it will monitor your logs for Nmap scan events. If an Nmap scan event is detected, the alert will be triggered and the selected action will be taken. You can generate another scan on Nmap, then view and manage your alerts in the “Alerts” section under “Security”:  <br/>
<img src="https://i.imgur.com/1P0kCsl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/ChtMUIA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<h2>Conclusion:</h2>
In this guide, we have set up a home lab using Elastic SIEM and a Kali VM. We forwarded data from the Kali VM to the SIEM using the Elastic Beats agent, generated security events on the Kali VM using Nmap and queried and analyzed the logs in the SIEM using the Elastic web interface. We also created a dashboard to visualize security events and then created an alert to detect security events.
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
