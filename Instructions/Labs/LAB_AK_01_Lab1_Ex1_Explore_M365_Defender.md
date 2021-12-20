# Module 1 - Lab 1 - Exercise 1 - Explore Microsoft 365 Defender 

## Lab scenario

You are a Security Operations Analyst working at a company that is implementing Microsoft 365 Defender. You start by assigning preset security policies in EOP and Microsoft Defender for Office 365.

### Obtain Your Microsoft 365 Credentials

Once you launch the lab, a free trial tenant will be made available to you to access in the Microsoft virtual Lab environment. This tenant will be automatically assigned a unique username and password. You must retrieve this username and password so that you can sign in to Azure and Microsoft 365 within the Microsoft Virtual Lab environment. 

Because this course can be offered by learning partners using any one of several Authorized Lab Hosting (ALH) providers, the actual steps involved to retrieve the tenant ID associated with your tenant may vary by lab hosting provider. Therefore, your instructor will provide you with the necessary instructions for how to retrieve this information for your course. The information that you should note for later use includes:

- **Tenant suffix ID.** This ID is for the onmicrosoft.com accounts that you will use to sign in to Microsoft 365 throughout the labs. This is in the format of **{username}@ZZZZZZ.onmicrosoft.com**, where ZZZZZZ is your unique tenant suffix ID provided by your lab hosting provider. Record this ZZZZZZ value for later use. When any of the lab steps direct you to sign in to Microsoft 365 portals, you must enter the ZZZZZZ value that you obtained here.
- **Tenant password.** This is the password for the admin account provided by your lab hosting provider.

### Create a Group 

1. On WIN1 Virtual machine, Navigate to Microsoft 365 Admin center (https://admin.microsoft.com/AdminPortal/Home)

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. On the **Stay signed in?** dialog box, select the Don’t show this again check box and then select **No**.

1. From the navigation menu select **Teams and Groups** and choose **Active teams and groups**

1. Select **Add a group**

1. Choose the default option (Microsoft 365) on  **Choose a group type**. Select **Next** 

1. Enter **Sg-IT** as the name of the group, give the Description and select **Next**.

1. On the **Assign owners** page select **+ Assign Owners** and select the **ODLuser** from the list and select **Add(1)** and then **Next**.

1. On the **Add members** page select **+ Add members** and select the **ODLuser** from the list and select **Add(1)** and then **Next**.

**Note**: DID is your unique deployment ID and can be found under the environment details tab.

1. On the **Edit Settings** enter **SG-IT-DID** under the **Group Email address**. Leave the rest of the options unchanged and select **Next**.

1. On the **Review and finish adding group** and select **Create Group**.
 
### Initialize Microsoft Defender for Endpoint.
 
In this task, you will perform the initialization of the Microsoft Defender for Endpoint portal.

1. On WIN1 virtual machine, Open the Microsoft Edge browser, search for "edge browser update", download, and install the new Microsoft Edge browser. This is necessary to ensure you're running the latest version of Microsoft Edge in your hosted virtual machine. Start the new Edge browser.

1.  In the Edge browser, go to the Microsoft Defender Security Center at (https://securitycenter.microsoft.com).

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

   **Note**: if you receive a message "You can't access this section.",  wait 5 minutes and try again.  Sometimes the access rules need to propagate the tenant.  

1. On the **Microsoft Security Center** setup Step 2, select **Next**.

1. On Step 3 **Set up preferences**, select the data storage location appropriate for where this training tenant is being managed.  You may want to validate with your course instructor.

1. Confirm the Preview features are **On**.

1. Select **Next**.  

1. Select Continue on the **Create your cloud instance**

1. After the **Creating your Microsoft Defender for Endpoint account** progress bar completes. Step 4 options will be displayed.  Select **Start using Microsoft Defender for Endpoint**.

1. In the Setup incomplete dialog box select **Proceed anyway**.

### Task 1: Apply Microsoft Defender for Office 365 preset security policies

In this task, you will assign preset security policies for EOP and Microsoft Defender for Office 365 in the Microsoft 365 security portal.

1. Login to WIN1 virtual machine as Admin with the password: **Pa55w.rd**.  

1. Start the Microsoft Edge browser.

1. In the Edge browser, go to the Microsoft 365 Defender portal at (https://security.microsoft.com).

1. In the **Sign in** dialog box, copy and paste in the tenant Email account for the admin username provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the admin's tenant password provided by your lab hosting provider and then select **Sign in**.

    >**Note**: if you receive a message "You can't access this section." wait 5 minutes and try again. Sometimes the access rules need to propagate the tenant which can take many minutes.  

1. If shown, close the Microsoft 365 Defender quick tour.

1. From the navigation menu, under *Email & Collaboration*, select **Polices & Rules**.

1. On the *Policy & Rules* dashboard, select **Threat Policies**.

1. On the *Policy dashboard*, select **Preset Security Policies**.

1. Under *Standard protection*, select **manage**.

1. In *EOP protections apply to*, under **Domains** write your tenant's domain name, select it and select **Next**. Notice that this configuration applies policies for anti-spam, outbound spam filter, anti-malware, anti-phishing.

1. In *Defender for Office 365 protections​ apply to*, apply the same configuration as the previous step and select **Next**. Notice that this configuration applies policies for anti-phishing, Safe Attachments, Safe Links.

1. Read the content under *Review and confirm your changes* and select **Confirm** to apply the changes and select **Done** to finish.

1. Under *Strict protection*, select **manage**.

1. In *EOP protections apply to*, under **Groups** write **Leadership**, select it and select **Next**. Notice that this configuration applies policies for anti-spam, outbound spam filter, anti-malware, anti-phishing.

1. In *Defender for Office 365 protections​ apply to*, apply the same configuration as the previous step and select **Next**. Notice that this configuration applies policies for anti-phishing, Safe Attachments, Safe Links.

1. Read the content under *Review and confirm your changes* and select **Confirm** to apply the changes and select **Done** to finish.

1. On the top middle menu, select **Threat policies** to go back and under *Policies*, select **Safe Attachments**. Notice that both preset policies appears here and the Status is On.

1. In the menu, select **Settings**.

1. Read through the available options and select the toggle under **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams** and select **Save**.

## You have completed the lab.
