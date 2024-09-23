# Exercise 2: Onboard Azure Arc-enabled servers to Microsoft Sentinel and Microsoft Defender for Cloud
### Estimated Duration: 30 Minutes
## Overview

This exercise focuses on integrating Azure Arc-enabled servers with Microsoft Sentinel and Microsoft Defender for Cloud to enhance security monitoring and threat detection across hybrid environments. Participants will enable Microsoft Defender for Cloud to monitor non-Azure servers and onboard them to Microsoft Sentinel for security event collection.

## Objectives

In this exercise, you will be performing the following tasks:

- Task 01: Enable Microsoft Defender for Cloud.
- Task 02: Onboard Azure Arc-enabled servers to Microsoft Sentinel
   
## Task 1: Enable Microsoft Defender for Cloud.
Microsoft Defender for Cloud can monitor the security posture of your non-Azure computers, but first, you need to connect them to Azure.
You can connect your non-Azure computers in any of the following ways:
  
  * Using Azure Arc enabled machines **(recommended)**
  
  * From Microsoft Defender for cloud pages in the Azure portal **(Getting started and Inventory)**
 
1. Search for **Microsoft Defender for Cloud** in the Azure portal search bar and then click on **Microsoft Defender for Cloud**.
    
   ![](.././media/H1-Ex2-task2-001.png)
   
1. From the Getting Started page, scroll down and then check on all the checkboxes and click on **Upgrade**. Please note in your lab environment you may find it already upgraded, in that case, please skip this and the next step.

   ![](.././media/H1-Ex2-task2-02.png)
   
1. Now, select the subscription listed and click on **Install agents**.
   
   > **Note**: If you see that the Install Agents button is not available, It means that the agent will get automatically installed with the help of Defender and log analytics.

   ![](.././media/H1-Ex2-task2-03.png)

1. Click on **Inventory** under **General** from the Microsoft Defender for Cloud.

   ![](.././media/H1-Ex2-task2-04.png)

1. You find the **ubuntu-k8s** Arc-enabled machine available in the resources list because the **LogAnalytics** agent is already enabled for it and the same Log Analytics workspace is connected to Microsoft Defender for Cloud. 

   > **Note**: Agent monitoring will take a few minutes to update and show the status as **Monitored** for Arc-enabled machine **ubuntu-k8s** as shown in the below screen. You can continue to the next exercise and come back later to check on this.

   > Please note that due to some latest updates, the status is not changing to **Monitored** for Arc-enabled machine **ubuntu-k8s**, this is a temporary issue and will fixed in future updates.   

   ![](.././media/H1-Ex2-task2-07.png)

   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
 
   - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task.
   - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.
 
<validation step="98bec6a2-c611-434b-adee-e6227f006309" />
   
## Task 2: Onboard Azure Arc-enabled servers to Microsoft Sentinel

Microsoft Sentinel comes with several connectors for Microsoft solutions, available out of the box and providing real-time integration. For physical and virtual machines, you can install the Log Analytics agent that collects the logs and forwards them to Microsoft Sentinel. Arc-enabled servers support deploying the Log Analytics agent using the following methods:

#### Using the VM extensions framework:
This feature in Azure Arc-enabled servers allows you to deploy the Log Analytics agent VM extension to a non-Azure Windows and/or Linux server. VM extensions can be managed using the following methods on your hybrid machines or servers managed by Arc-enabled servers:
 
 * The Azure portal
 
 * The Azure CLI
 
 * Azure PowerShell
 
 * Azure Resource Manager templates

#### Using Azure Policy:
You can use the Azure Policy Deploy Log Analytics agent to Linux or Windows Azure Arc machine's built-in policy to audit if the Arc-enabled server has the Log Analytics agent installed. If the agent is not installed, it automatically deploys it using a remediation task. Alternatively, if you plan to monitor the machines with Azure Monitor for VMs, use the Enable Azure Monitor for VMs initiative to install and configure the Log Analytics agent.

  > **Note**: You have already installed Log Analytics Agent into the Linux VM - ubuntu-k8s in the previous exercise. You can refer **Task 5** in the previous exercise to review it again. Also, the screenshots of the log results can be mismatched because the result can take more time to get the same results. 
 
1. Search for ```Microsoft Sentinel``` on the Azure portal and, then select the **Microsoft Sentinel** from the search result.

   ![](.././media/ss1.png)
    
2. On **Microsoft Sentinel** blade, click on **+ Create** to add Microsoft Sentinel to a workspace.

   > **Note**: You may also find **+ Add/+ New** button in place of **+ Create**. 

   ![](.././media/microsoft-sentinel-create.png)
    
3. Select the existing log analytics workspace shown named LogAnalyticsWS-<inject key="DeploymentID" enableCopy="false"/>
  and then click on the **Add** button.

   ![](.././media/microsoft-sentinel-add.png)
    
4. You will see a notification in the upper right corner **Adding Microsoft Sentinel**. It will take around 1 minute to get added.
    
5. Once the Microsoft Sentinel is added you will see another notification which says **Successfully added Microsoft Sentinel** as shown below.
     
   ![](.././media/microsen-success.png)
 
6. Click on the **Overview** on the Microsoft Sentinel page from where you can view the insights after a few minutes. If you are not able to view the insights after a few minutes, then refresh the browser tab.
    
   ![](.././media/microsoft-sentinel-overview.png)

7. Click on the **Content Hub** on the Microsoft Sentinel page, Search and select **Syslog** from the second page of the solution. Click on **Install**. Wait until it's installed before proceeding to the next step.

   ![](.././media/hybridcloud-ex2-t2-1.png)
    
7. Now, click on the **Workbooks** from the left pane under the **Threat Management** section and search for ```Linux machines``` and select **Linux machines** from the search result.
    
   ![](.././media/microsoft-sentinel-workbook.png)
    
8. Then from the bottom-right corner of the Azure portal, click on **Save** and then on **OK** to save the workbook. 
 
   ![](.././media/as-08.png)
    
9. Now, go back to **Microsoft Sentinel Overview** blade by clicking on **Overview(1)** under General section on the left. Disable the **New Overview(2)** toggle and then click on **INSIGHTSMETER(3)** to query the **ubuntu-k8s** VM insights. The count of **Events** could be different on your Microsoft Sentinel Dashboard.

   ![](.././media/H1E2T2S9.png)
    
10. You will see **Results** for ```union InsightsMetrics``` in query explorer. You can see operations around the Network, Logical Disk, Memory, and Processor for **ubuntu-k8s** VM. If you are not able to see the results, then try to adjust the query editor size and you will be able to see the outcome.

    ![](.././media/as-10.png)
    
1. Let us check for **ubuntu-k8s** processes by running the following query, you can change the time range limit as well to see the result of a specific time interval. You can scroll right on the **Results** section and see more details and descriptions about every process. 

   > **Note**: The data might take around 30 mins to get populated. If you don't find the data, you can skip to Task 2: Enable Microsoft Defender for Cloud and come back later to this task to re-execute the query and filter the data.

   ```
   VMProcess 
   | where TimeGenerated > ago(24h) 
   | limit 10
   ```

   > **Note**: In the above query, against TimeGenerated,  ago(24h) means "24 hours ago" so this query only returns records from the last 24 hours.

   ![](.././media/as-11.png)   
    
1. You can save the query for later use by clicking on the **Save (1)** and then **Save as query (2)** button.

    ![](.././media/hol1ex2stp12.png) 
   
1. Now, provide `VMProcess` for the **Query name (1)**, then click on **Save (2)**.

    ![](.././media/as-121-v2.png) 

1. You can see and run the saved **queries** by browsing to **Queries**
   
    ![](.././media/as-13-v2.png) 
   
1. Then, you will find the `VMProcess` query under **Queries**, click on **Run** to run the query.
   
    ![](.././media/as-131-v2.png) 

## Summary
 
In this exercise, you onboarded an Azure Arc-enabled machine to Microsoft Sentinel, enhancing its security and threat detection capabilities. Additionally, you enabled Microsoft Defender for Cloud to further strengthen security posture, ensuring comprehensive protection and monitoring across your hybrid infrastructure.

### You have successfully completed the Exercise

