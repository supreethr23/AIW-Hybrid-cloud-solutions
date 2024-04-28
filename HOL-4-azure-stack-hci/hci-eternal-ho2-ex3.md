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