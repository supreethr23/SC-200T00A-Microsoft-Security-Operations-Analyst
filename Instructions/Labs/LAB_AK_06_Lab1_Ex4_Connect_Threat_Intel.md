---
Lab - Do not use. Temporarily not operational!:
---

# Module 6 - Lab 1 - Exercise 4 - Connect Threat intelligence to Microsoft Sentinel using data connectors (READ ONLY)


### Task 1: Connect Threat intelligence.

In this task, you will connect a Threat intelligence provider with the Threat intelligence - TAXII connector.

1. Log in to the WIN1 virtual machine with the password as provided in the Environment tab.  

1. In the Edge browser, navigate to the Azure portal at (https://portal.azure.com).

1. In the **Sign in** dialog box, copy and paste in the **Username** provided in the environment details page (odl_user_DID@xxxxx.onmicrosoft.com) and then select Next.

1. In the **Enter password** dialog box, copy and paste in the Password and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select the Microsoft Sentinel Workspace you created earlier.

1. From the Data Connectors tab, Search and select the **Threat intelligence - TAXII** connector.

1. Select the **Open connector page** on the connector information blade.

1. In the Configuration area, for the **Friendly name (for server)** enter *PhishURLs*

1. For the API root URL enter https://limo.anomali.com/api/v1/taxii2/feeds/

1. Enter **107** for the Collection ID.

1. Enter **guest** for username.

1. Enter **guest** for the password.

1. Now select **Add** button.  

    Phishing URLs will be pulled and populated in the ThreatIntelligenceIndicator table.

    **Note:** For additional collections open https://limo.anomali.com/api/v1/taxii2/feeds/collections/ in a Browser, use the guest username and password to review the different Collection IDs available.

## You have completed the lab.
