# Azure HCI Eternal Training Hands-on Lab: 2

## Exercise 1: Configure and Monitor cluster performance from the Windows Admin Center dashboard

### Task 1: Install Windows Admin Center on each Node

1. On the **HCIBox-Client** virtual machine, click on search button search for **Hyper-V** and select **Hyper-V Manager**.

   ![](media/hol2-ex1-task1-step1.png)

2. On the **Hyper-V Manager**, select **HCIBOX-CLIENT** from the left menu under the Hyper-V Manager list, and  double-click on **AzHost1** node.

   ![](media/hol2-ex1-task1-step2.png)

3. Connect to **AzHost1** box, and then click on the Connect button.

   ![](media/hol2-ex1-task1-step3.png)

4. On the **login** window, enter the Username as **arcdemo** hit **tab** button, enter password as **ArcPassword123!!** and hit **Enter** to login. 

   ![](media/hol2-ex1-task1-step4.png)

5. On the **Welcome to Azure Stack HCI** window, in **Enter number to select an option** enter **15** and hit **Enter** button. 

   ![](media/hol2-ex1-task1-step5.png)

6. Run the following command to install **Windows Admin Center**.

   ```
   msiexec /i WindowsAdminCenter.msi /qn /L*v log.txt SME_PORT=6516 SSL_CERTIFICATE_OPTION=generate
   ```

7. Install **Windows Admin Center** for **AzHost2** node, by repeating the **step 4 to step 6** .

### Task 2: Monitor Cluster in Windows Admin Center

1. Navigate to the Resource Group in the Azure portal navigation section.

   ![](.././media/navigate-resource-group.png "Select Resource Group from Navigate Option")

2. From the Resource groups pane, click on **AzureStakHCI** resource group and verify the resources present in it.

   ![](media/azurestackhci-rg.png "Select Azure Stack HCI Resource Group")

3. In the  **AzureStakHCI** resource group in the search bar search for **hciboxcluster** **(1)** and select **hciboxcluster** **(2)** Azure Stack HCI.

   ![](media/selecth-ciboxcluster-hci.png)

4. In the **hciboxcluster** Azure Stack HCI, from the left menu select **Logical networks** **(1)** under Resources, and click on **+ Create logical network** **(2)**.

   ![](media/logic1network-create.png)

5. In the **Create logical network** tab, under Basic fill the fallowing details and click on **Next: Network Configuartion** **(5)**.

   - Subscription : Default subscription **(1)**
   - Resource group : **AzureStackHCI** **(2)**
   - Logical network name: **hcibox-aks-lnet-vlan110** **(3)**
   - Virtual switch name: **ConvergedSwitch(hci)** **(4)**

      ![](media/logic-1network-basic.png)

6. In the **Network Configuation** tab, under the fallowing deatils and click on **Next: Tags** **(9)**.

   | **Variables**                | **Values**                                                    |
   | ---------------------------- |---------------------------------------------------------------|
   | IP address assignment | **Static** **(1)** |
   | IPv4 address space    | **10.10.0.0** **(2)** from the drop down  address prefix select **\24** **(3)** |
   | IP pools              | Enter Start IP **10.10.0.101** **(4)** and End IP **10.10.0.199** **(5)** |
   | Default Gateway       | Enter Default Gateway address as **10.10.0.1** **(6)** |
   | DNS Servers           | Enter DNS Servers **192.168.1.254** **(7)** |
   | VLAN ID               | Enter **110** **(8)** | 


   ![](media/logic-1network-network.png)

7. In the **Tag** tab, leave it as default and click **Next: Review + Create**.

8. In the **Review + Create** tab, click on on **Create** button.

   ![](media/logic-1network-create.png)

9. Once the deployment got succedded, navigate back to **hciboxcluster** Azure Stack HCI, from the left menu select **Logical networks** **(1)** under Resources, and click on **+ Create logical network** **(2)**.

   ![](media/logic2network-create.png)

10. In the **Create logical network** tab, under Basic fill the fallowing details and click on **Next: Network Configuartion** **(5)**.

    - Subscription : Default subscription **(1)**
    - Resource group : **AzureStackHCI** **(2)**
    - Logical network name: **hcibox-vm-lnet-vlan200** **(3)**
    - Virtual switch name: **ConvergedSwitch(hci)** **(4)**

      ![](media/logic-2network-basic.png)

11. In the **Network Configuation** tab, under the fallowing deatils and click on **Next: Tags** **(7)**.

    | **Variables**                | **Values**                                                    |
    | ---------------------------- |---------------------------------------------------------------|
    | IP address assignment | **Static** **(1)** |
    | IPv4 address space    | **192.168.200.0** **(2)** from the drop down  address prefix select **\24** **(3)** |
    | Default Gateway       | Enter Default Gateway address as **192.168.200.1** **(4)** |
    | DNS Servers           | Enter DNS Servers **192.168.1.254** **(5)** |
    | VLAN ID               | Enter **200** **(6)** | 


      ![](media/logic-2network-network.png)

12. In the **Tag** tab, leave it as default and click **Next: Review + Create**.

13. In the **Review + Create** tab, click on on **Create** button.

    ![](media/logic-2network-create.png)

14. Once the deployment got succedded, navigate back to **hciboxcluster** Azure Stack HCI, from the left menu select **Windows Admin Center (preview)** **(1)** under setting and click on **SetUp** **(2)**.

    ![](media/wac-setup.png)

15. In the **Windows Admin Center** pop-up leave Listening port to **6516**, click on **Install**. 

    ![](media/wac-install.png)

   > **Note**: This may take 5 minutes to get ready please wait.
 