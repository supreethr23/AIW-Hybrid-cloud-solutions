# Not Required Steps

## HOL 2: Exercise: 1
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
