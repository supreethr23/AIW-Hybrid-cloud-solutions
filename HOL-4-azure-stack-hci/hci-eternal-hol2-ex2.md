# Exercise 2: Azure Backup Server on Azure Stack

In this exercise, you will learn how to install Azure Backup Server on Azure Stack, which enables backup and recovery capabilities for files and applications within the Azure environment. This exercise focuses on deploying and configuring Azure Backup Server to safeguard critical data and applications hosted on Azure Stack, ensuring robust protection and restore capabilities in the cloud environment.

### Task 1: Create a Recovery Service Vault

A Recovery Services vault is a management entity that stores recovery points that are created over time, and it provides an interface to perform backup-related operations. These operations include taking on-demand backups, performing restores, and creating backup policies.

1. In the Azure portal, search for **Backup center** and then navigate to the **Backup center** dashboard.

   ![](media/hci24-18.png)

2. On the Overview pane, select Vault.

   ![](media/hci24-19.png)

3. Select Recovery Services vault > Continue.

   ![](media/hci24-20.png)

4. On the Recovery Services vault pane, enter the following values:

    - Subscription: Select the available subscription to use
    - Resource group: Use an existing resource group named **AzureStackHCI**
    - Vault name: **hci-backup-vault** 
    - Region: select the same region where Azure Satck HCI is deployed i.e, **East US**

   ![](media/hci24-21.png)

5. After providing the values, select Review + create.

   ![](media/hci24-22.png)

6. To finish creating the Recovery Services vault, select Create.

   It can take a while to create the Recovery Services vault. Monitor the status notifications in the Notifications area at the upper right. After the vault is created, it appears in the list of Recovery Services vaults. If the vault doesn't appear, select Refresh.

### Task 2: Enable Azure Backup and Download Azure Backup Server installer



### Task 3: Install the Azure Backup Server

1. Once you've downloaded all files to your Azure Stack Hub virtual machine, go to the download location i.e, `C:\Users\arcdemo\Downloads`.

    ![](media/hci24-27.png)

1. To start the installation, from the list of downloaded files, select **MicrosoftAzureBackupserverInstaller.exe**.

    > [!WARNING]
    > At least 4GB of free space is required to extract the setup files.
    >

2. In the Azure Backup Server wizard, select **Next** to continue.

    ![Microsoft Azure Backup Setup Wizard](./media/backup-mabs-install-azure-stack/mabs-install-wiz-1.png)

3. Choose the path for the Azure Backup Server files, and select **Next**.

   ![Select destination for files](./media/backup-mabs-install-azure-stack/mabs-install-wizard-select-destination-1.png)

4. Verify the extraction location, and select **Extract**.

   ![Verify extraction location](./media/backup-mabs-install-azure-stack/mabs-install-wizard-extract-2.png)

5. The wizard extracts the files and readies the installation process.

   ![Wizard extracts files](./media/backup-mabs-install-azure-stack/mabs-install-wizard-install-3.png)

6. Once the extraction process completes, select **Finish**. By default, **Execute setup.exe** is selected. When you select **Finish**, Setup.exe installs Microsoft Azure Backup Server to the specified location.

   ![Setup extracts Microsoft Azure Backup Server files](./media/backup-mabs-install-azure-stack/mabs-install-wizard-finish-4.png)

