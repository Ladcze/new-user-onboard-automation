# new-user-onboard-automation
Automating onboard of new user as per triggers

---

# Introduction
A project to automate the process of onboarding a new employee into Azure AD and assigning necessary Azure resources.

---

# Application Architecture
The diagram below provides a visual representation of the services used in this tutorial and how they are connected.    

![OnboardAutomatorAchitecture](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/d13af6e5-6218-4c12-837a-59d33bf8161e)

---

# Services deployed
The key services required (including an Azure account with administrator level access) for this project are:   
Azure Active Directory (Microsoft Entra ID)   
Azure Logic Apps   
Azure Email Service (part of Logic Apps connector)   
Azure Resource Manager   

![AzureAD](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/3cdbb5c7-a318-44f9-8a1c-12d9ab1b505b)   ![LogicApp](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/640b2be8-6a3c-4967-8294-f6f2da8c6dee)   ![Log-Analytics-Workspaces](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/d7c9dd49-4a48-40dc-bfeb-49aa84962e70)   

---

# Steps
1. Set up a new Azure AD instance (if not already present) using the Azure portal.
2. Design a Logic App workflow triggered by an event (like an entry in a SharePoint list or an email to a specific mailbox) indicating a new employee hire.
3. Use the Azure AD connector in Logic Apps to automatically create a new user in Azure AD based on the trigger event's details.
4. Assign predefined roles and groups to the new user based on the job position or department indicated in the trigger.
5. Use the Azure Resource Manager connector in Logic Apps to provision any necessary Azure resources for the user (like VMs or specific permissions).
6. Leverage the Email connector in Logic Apps to send a welcome email to the new hire with instructions and necessary access details.
7. Monitor and review the onboarding process through Logic Apps runs history and Azure AD logs to ensure smooth operations.

---

**1. Azure AD Setup:  Set up a new Azure AD instance (if not already present) using the Azure portal.**   
Log into the Azure portal. Remember, admin-level access is required for the associated tasks. 

![Screenshot 2023-08-31 155321](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/bda80dbd-0a1d-42cc-889b-e192a4adca35)

--- 

**2. Logic App Workflow Design: Design a Logic App workflow triggered by an event (like an entry in a SharePoint list or an email to a specific mailbox) indicating a new employee hire.**   
Search for logic apps.   
Create a new logic app using the Add button.   
Specify relevant details such as Subscription / resource group / Logic app name / Publish type (use workflow) / Location / Plan type (standard or consumption) depending on requirements.   

![Screenshot 2023-08-31 155415](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/542bfe8c-f7fc-42e4-ab03-4260f44a1fea)   

![Screenshot 2023-08-31 160516](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/bf4db535-2bd3-414f-a1ca-6170e55c6b28)   

![Screenshot 2023-09-01 105057](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/3c0e36a8-cb0d-47b1-81b8-f36875150b8d)   


--- 

**3. Azure AD User Creation: Use the Azure AD connector in Logic Apps to automatically create a new user in Azure AD based on the trigger event's details.**

Using the logic app designer, setup a flow using one of the pre-defined options (when an email is received in Outlook). Or you could create one from a blank template.   

![Screenshot 2023-08-31 160546](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/6695008b-5221-434b-beaa-08262b0d53e3)   

Provide necessary connection details for the email account being monitored.   

![Screenshot 2023-08-31 161121](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/bc4c408b-24ba-4362-841e-8dc617c74a22)

Select the next step (after email flow above is done) and enter required paraments for the new user setup.  

![Screenshot 2023-08-31 162241](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/d5ba7cd0-af6b-413b-a640-f3530589bc65) 

--- 

**4. Role and Group Assignment: Assign predefined roles and groups to the new user based on the job position or department indicated in the trigger.**   

![Screenshot 2023-09-01 131004](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/78b5973d-6e89-4795-aa19-2d9256ed5cd6)

--- 

**5. Resource Provisioning: Use the Azure Resource Manager connector in Logic Apps to provision any necessary Azure resources for the user (like VMs or specific permissions).**   

![Screenshot 2023-09-01 130647](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/81fc3034-0add-4f24-80b6-64225fd82a27)   


--- 

**6. Welcome Email: Leverage the Email connector in Logic Apps to send a welcome email to the new hire with relevant access details.**   

![Screenshot 2023-09-01 130524](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/6278dec2-0e09-47a7-be54-87cf309c0e99)   

Save the entries made on the logic app designer.   

![Screenshot 2023-08-31 165136](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/c4c6c425-490b-4070-9574-45faf4ee4547)

There is no need to run the created logic app. This will run automatically as triggers (for instance the new email received or as per schedule).

--- 

**7. Monitoring and Review: Monitor and review the onboarding process through Logic Apps runs history and Azure AD logs to ensure smooth operations.**   

![Screenshot 2023-09-01 091431](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/8d901579-bb51-4c21-a7a6-7fa8e4769375)   

The trigger history shows the flow was successful executed as per trigger.    

![Screenshot 2023-09-01 092302](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/30d3796b-b93f-4540-a7af-b60bbfb16e99)   

Audit logs in Azure AD also reveals success in expected outcomes as per parameters set in triggers. 

![Screenshot 2023-09-01 094113](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/56189adb-c0b4-4503-9048-dab108fcec8d)   


---

# Conclusion/Summary

A new user (username1) was successfully created.   

![Screenshot 2023-09-01 091026](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/8f7245e3-5dbf-41c7-99b9-e376864a8b40)

![Screenshot 2023-09-01 091150](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/b42affcc-ac16-4f40-a209-cf90f5cdce2f)   

Groups also assigned dynamically as per set preference.   

![Screenshot 2023-09-01 131943](https://github.com/Ladcze/new-user-onboard-automation/assets/97769275/4ce9d3b0-f7e7-4b78-833b-e9d4962fa2ff)

<br>   

***I need to review/re-test outgoing email option

--- 

# Reference
https://github.com/madebygps/projects/blob/main/az-104/readme.md 
