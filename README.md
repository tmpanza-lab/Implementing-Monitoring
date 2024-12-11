# Implementing Monitoring

## Objective

In this lab, I learnt about Azure Monitor. I learnt how to create an alert and send it to an action group. I triggered and tested the alert and checked the activity log.

## Architecture diagram
![image](https://github.com/user-attachments/assets/749b0a02-193b-4392-a7db-385375806251)
 


### Job Skills

- Using a template to provision an infrastructure.
- Creating an alert.
- Configuring action group notifications.
- Triggering an alert and confirming it is working.
- Configure an alert processing rule
- Using Azure Monitor to log queries.



### Tools Used

- Azure portal - https://portal.azure.com


## Steps

## Task 1: Use a template to provision an infrastructure

In this task, I will deploy a virtual machine that will be used to test monitoring scenarios.

1.	Download the \Allfiles\Lab11\az104-11-vm-template.json lab files to your computer.
2.	Sign in to the Azure portal - https://portal.azure.com.
3.	From the Azure portal, search for and select Deploy a custom template.
![image](https://github.com/user-attachments/assets/a57ad91d-3b1c-471c-b0f8-750331fe8719)
 
4.	On the custom deployment page, select Build you own template in the editor.
5.	On the edit template page, select Load file.
6.	Locate and select the \Allfiles\Labs11\az104-11-vm-template.json file and select Open.
![image](https://github.com/user-attachments/assets/dd2eb162-0945-42be-8d70-ad9c9dea6e67)
 
7.	Select Save.
8.	Use the following information to complete the custom deployment fields, leaving all other fields with their default values:
![image](https://github.com/user-attachments/assets/234739b1-4a0c-4314-9699-646859caf5bd)
 
1.	Select Review + Create, then select Create.
![image](https://github.com/user-attachments/assets/2d19edf8-f1ee-4d9f-a7b2-963971f7208c)
 
2.	Wait for the deployment to finish, then click Go to resource group.
![image](https://github.com/user-attachments/assets/08ab9c39-c6b5-443a-881b-6c3a112f1cb8)
 
3.	Review what resources were deployed. There should be one virtual network with one virtual machine.
![image](https://github.com/user-attachments/assets/bca6359e-159c-4fc6-b55d-7823cd7e5a12)
 
Configure Azure Monitor for virtual machines (this will be used in the last task)
1.	In the portal, search for and select Monitor.
![image](https://github.com/user-attachments/assets/d063300f-44f4-4e52-b090-61ffc84d5583)
 
2.	Take a minute to review all the insights, detection, triage, and diagnosis tools that are available.
![image](https://github.com/user-attachments/assets/c46d10ba-f91b-43a8-949a-306b27a1c704)
 
3.	Select View in the VM Insights box, and then select Configure Insights.
![image](https://github.com/user-attachments/assets/35b083df-cb3f-484c-aede-1e4bbe326324)
 
4.	Select your virtual machine, and then Enable (twice).
![image](https://github.com/user-attachments/assets/f739682a-f4df-4e1c-9a8d-5a33b5328c29)
 
5.	Take the defaults for subscription and data collection rules, then select Configure.
![image](https://github.com/user-attachments/assets/f5000e63-62f5-4436-8e16-fc1bb06cded8)
 
6.	It will take a few minutes for the virtual machine agent to install and configure, proceed to the next step.

## Task 2: Create an alert

In this task, I will create an alert for when a virtual machine is deleted.

1.	Continue on the Monitor page , select Alerts.
![image](https://github.com/user-attachments/assets/af724f37-207e-4bf2-8213-48aaa66cdced)
 
2.	Select Create + and select Alert rule.
![image](https://github.com/user-attachments/assets/6f22567d-94eb-4de6-adf1-1d94057e3dd3)
 
3.	Select the box for the resource group, then select Apply. This alert will apply to any virtual machines in the resource group. Alternatively, you could just specify one particular machine.
![image](https://github.com/user-attachments/assets/5c15e06f-6a29-44dc-86ee-4e7affae4923)
 
4.	Select the Condition tab and then select the See all signals link.
5.	Search for and select Delete Virtual Machine (Virtual Machines). Notice the other built-in signals. Select Apply
![image](https://github.com/user-attachments/assets/cd05b039-6713-4c20-a0b2-4339a808c7bf)
 
6.	In the Alert logic area (scroll down), review the Event level selections. Leave the default of All selected.
![image](https://github.com/user-attachments/assets/d1e861c7-700b-4fe6-aa79-644839325d23)
![image](https://github.com/user-attachments/assets/61cd1fe1-3136-455e-8a84-82ee8e4ede11)
 

 
7.	Review the Status selections. Leave the default of All selected.
![image](https://github.com/user-attachments/assets/4381de1b-7198-48eb-85b0-741233fe2f7d)
 
8.	Leave the Create an alert rule pane open for the next task.


## Task 3: Configure action group notifications

In this task, if the alert is triggered send an email notification to the operations team.

1.	Continue working on your alert. Select Next: Actions, and then select Create action group.
![image](https://github.com/user-attachments/assets/a4b5ee00-22e2-476d-b4a0-09fc57aaa8bb)
![image](https://github.com/user-attachments/assets/c9f3a2e0-97be-4b80-b0d8-f77e8d85f23b)
 
 
2.	On the Basics tab, enter the following values for each setting.
3.	Select Next: Notifications and enter the following values for each setting.
4.	Select Email, and in the Email box, enter your email address, and then select OK.
5.	Once the action group is created move to the Next: Details tab and enter the following values for each setting.
![image](https://github.com/user-attachments/assets/400b5018-c44c-44f2-901d-a4b95489ca43)
 

## Task 4: Trigger an alert and confirm it is working

In this task, I trigger the alert and confirm a notification is sent.
1.	In the portal, search for and select Virtual machines.
2.	Check the box for the az104-vm0 virtual machine.
![image](https://github.com/user-attachments/assets/66031376-3ba6-4342-a4b4-176e16ede456)
![image](https://github.com/user-attachments/assets/007f866a-b2f4-4c94-a30b-316f123f5621)
 

 
3.	Select Delete from the menu bar.
4.	Check the box for Apply force delete. Check the box at the bottom confirming that you want the resources to be deleted and select Delete.
5.	In the title bar, select the Notifications icon and wait until vm0 is successfully deleted.
![image](https://github.com/user-attachments/assets/074f3c2c-8467-4add-9fd7-96ea9aed2298)
 
6.	You should receive a notification email that reads, Important notice: Azure Monitor alert VM was deleted was activated… If not, open your email program and look for an email from azure-noreply@microsoft.com.
![image](https://github.com/user-attachments/assets/ba35f619-d5bb-4b36-8a91-d99669ae6298)
 
7.	On the Azure portal resource menu, select Monitor, and then select Alerts in the menu on the left.
8.	You should have three verbose alerts that were generated by deleting vm0.
![image](https://github.com/user-attachments/assets/b5e69d34-af53-4b04-bacf-1c3ba8de6d7d)
 
9.	Select the name of one of the alerts (For example, VM was deleted). An Alert details pane appears that shows more details about the event.
![image](https://github.com/user-attachments/assets/17d9b872-5066-4c6e-892c-9d0a2e83700e)
 


## Task 5: Configure an alert processing rule

In this task, I create an alert rule to suppress notifications during a maintenance period.

1.	Continue in the Alerts blade, select Alert processing rules and then + Create.
![image](https://github.com/user-attachments/assets/6a0a3f0a-cee5-4b5b-98dc-2116a236c014)
 
2.	Select your resource group, then select Apply.
3.	Select Next: Rule settings, then select Suppress notifications.
![image](https://github.com/user-attachments/assets/d2067047-97c0-4b4c-8842-45fd2d61bbd7)
 
4.	Select Next: Scheduling.
5.	By default, the rule works all the time, unless you disable it or configure a schedule. You are going to define a rule to suppress notifications during overnight maintenance. Enter these settings for the scheduling of the alert processing rule:
![image](https://github.com/user-attachments/assets/46a469eb-b2c5-4e23-a90e-135513e3bfd5)
 
6.	Select Next: Details and enter these settings:
![image](https://github.com/user-attachments/assets/a658f75d-3697-49c1-bd21-28bb46795fd1)
 
7.	Select Review + create to validate your input, then select Create.
![image](https://github.com/user-attachments/assets/517a5f2f-8ef3-4937-b4f4-8c936061ea67)
 


## Task 6: Use Azure Monitor log queries

In this task, I will use Azure Monitor to query the data captured from the virtual machine.

1.	In the Azure portal, search for and select Monitor blade, click Logs.
2.	If necessary close the splash screen.
![image](https://github.com/user-attachments/assets/cf393247-9960-49e7-b3fd-6407299df145)
 
3.	Select a scope, your resource group. Select Apply.
4.	In the Queries tab, select Virtual machines (left pane).
5.	Review the queries that are available. Run (hover over the query) the Count heartbeats query.
6.	You should receive a heartbeat count for when the virtual machine was running.
7.	Review the query. This query uses the heartbeat table.
8.	Replace the query with this one, and then click Run. Review the resulting chart.
![image](https://github.com/user-attachments/assets/9262c739-f514-4bc5-b7b6-8480f5ba4298)
![image](https://github.com/user-attachments/assets/ad84f124-fce1-4895-a949-2b4a84e9bb2d)
 
9.	As you have time, review and run other queries.


