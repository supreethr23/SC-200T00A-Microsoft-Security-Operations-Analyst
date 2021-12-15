# Module 1 - Lab 1 - Exercise 1 - Explore Microsoft 365 Defender 

## Lab scenario

You are a Security Operations Analyst working at a company that is implementing Microsoft 365 Defender. You start by assigning preset security policies in EOP and Microsoft Defender for Office 365.

### Task : Obtain Your Microsoft 365 Credentials

Once you launch the lab, a free trial tenant will be made available to you to access in the Microsoft virtual Lab environment. This tenant will be automatically assigned a unique username and password. You must retrieve this username and password so that you can sign in to Azure and Microsoft 365 within the Microsoft Virtual Lab environment. 

Because this course can be offered by learning partners using any one of several Authorized Lab Hosting (ALH) providers, the actual steps involved to retrieve the tenant ID associated with your tenant may vary by lab hosting provider. Therefore, your instructor will provide you with the necessary instructions for how to retrieve this information for your course. The information that you should note for later use includes:

- **Tenant suffix ID.** This ID is for the onmicrosoft.com accounts that you will use to sign in to Microsoft 365 throughout the labs. This is in the format of **{username}@ZZZZZZ.onmicrosoft.com**, where ZZZZZZ is your unique tenant suffix ID provided by your lab hosting provider. Record this ZZZZZZ value for later use. When any of the lab steps direct you to sign in to Microsoft 365 portals, you must enter the ZZZZZZ value that you obtained here.
- **Tenant password.** This is the password for the admin account provided by your lab hosting provider.

### Create a Group 

1. Navigate to Microsoft 365 Admin center (https://admin.microsoft.com/AdminPortal/Home).	

2. From the navigation menu select **Teams and Groups** and choose **Active teams and groups**

3. Select **Add a group**

4. Choose the default option (Microsoft 365) on  **Choose a group type**. Select **Next** 

5. Enter **Sg-IT** as the name of the group and select **Next**(1) Add

6. On the **Assign owners** page select **+ Assign Owners** and select the **ODLuser** from the list and select **(1) Add** and then **Next**.

7. On the **Add members** page select **+ Add members** and select the **ODLuser** from the list and select **(1) Add** and then **Next.

**Note**: DID is your unique deployment ID and can be found under the environment details tab.

8. On the **Edit Settings** enter **SG-IT-DID** under the **Group Email address**. Leave the rest of the options unchanged and select **Next**.

9. On the **Review and finish adding group** and select **Create Group**.
 
### Initialize Microsoft Defender for Endpoint.
 
In this task, you will perform the initialization of the Microsoft Defender for Endpoint portal.


1.  Log in to WIN1 virtual machine as Admin with the password: **Pa55w.rd**.  

2.  Open the Microsoft Edge browser, search for "edge browser update", download, and install the new Microsoft Edge browser. This is necessary to ensure you're running the latest version of Microsoft Edge in your hosted virtual machine. Start the new Edge browser.

3.  In the Edge browser, go to the Microsoft Defender Security Center at (https://securitycenter.microsoft.com).

4. In the **Sign in** dialog box, copy and paste in the tenant Email account for the admin username provided by your lab hosting provider and then select **Next**.

5. In the **Enter password** dialog box, copy and paste in the admin's tenant password provided by your lab hosting provider and then select **Sign in**.

**Note**: if you receive a message "You can't access this section.",  wait 5 minutes and try again.  Sometimes the access rules need to propagate the tenant.  

6. On the **Microsoft Security Center** setup Step 2, select **Next**.

7. On Step 3 **Set up preferences**, select the data storage location appropriate for where this training tenant is being managed.  You may want to validate with your course instructor.

8. Confirm the Preview features are **On**.

9. Select **Next**.  

10. Select Continue on the **Create your cloud instance**

11. After the **Creating your Microsoft Defender for Endpoint account** progress bar completes. Step 4 options will be displayed.  Select **Start using Microsoft Defender for Endpoint**.

12. In the Setup incomplete dialog box select **Proceed anyway**.

### Task 1: Apply Microsoft Defender for Office 365 preset security policies

In this task, you will assign preset security policies for EOP and Microsoft Defender for Office 365 in the Microsoft 365 security portal.

1. Login to WIN1 virtual machine as Admin with the password: **Pa55w.rd**.  

2. Start the Microsoft Edge browser.

3. In the Edge browser, go to the Microsoft 365 Defender portal at (https://security.microsoft.com).

4. In the **Sign in** dialog box, copy and paste in the tenant Email account for the admin username provided by your lab hosting provider and then select **Next**.

5. In the **Enter password** dialog box, copy and paste in the admin's tenant password provided by your lab hosting provider and then select **Sign in**.

    >**Note**: if you receive a message "You can't access this section." wait 5 minutes and try again. Sometimes the access rules need to propagate the tenant which can take many minutes.  

6. If shown, close the Microsoft 365 Defender quick tour.

7. From the navigation menu, under *Email & Collaboration*, select **Polices & Rules**.

8. On the *Policy & Rules* dashboard, select **Threat Policies**.

9. On the *Policy dashboard*, select **Preset Security Policies**.

10. Under *Standard protection*, select **manage**.

11. In *EOP protections apply to*, under **Domains** write your tenant's domain name, select it and select **Next**. Notice that this configuration applies policies for anti-spam, outbound spam filter, anti-malware, anti-phishing.

12. In *Defender for Office 365 protections​ apply to*, apply the same configuration as the previous step and select **Next**. Notice that this configuration applies policies for anti-phishing, Safe Attachments, Safe Links.

13. Read the content under *Review and confirm your changes* and select **Confirm** to apply the changes and select **Done** to finish.

14. Under *Strict protection*, select **manage**.

15. In *EOP protections apply to*, under **Groups** write **Leadership**, select it and select **Next**. Notice that this configuration applies policies for anti-spam, outbound spam filter, anti-malware, anti-phishing.

16. In *Defender for Office 365 protections​ apply to*, apply the same configuration as the previous step and select **Next**. Notice that this configuration applies policies for anti-phishing, Safe Attachments, Safe Links.

17. Read the content under *Review and confirm your changes* and select **Confirm** to apply the changes and select **Done** to finish.

18. On the top middle menu, select **Threat policies** to go back and under *Policies*, select **Safe Attachments**. Notice that both preset policies appears here and the Status is On.

19. In the menu, select **Settings**.

20. Read through the available options and select the toggle under **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams** and select **Save**.

## You have completed the lab.
