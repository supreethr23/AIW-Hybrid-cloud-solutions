# Lab Overview: Azure Stack HCI

### Getting started:
HCIBox is a turnkey solution that provides a complete sandbox for exploring Azure Stack HCI capabilities and hybrid cloud integration in a virtualized environment. HCIBox is designed to be completely self-contained within a single Azure subscription and resource group, which will make it easy for a user to get hands-on with Azure Stack HCI and Azure Arc technology without the need for physical hardware.

Azure Stack HCI 23H2 is now generally available. 23H2 simplifies configuration and deployment of HCI clusters and related workloads like VM management for VM self-service management in Azure portal. HCIBox has also been updated and now offers clusters built on the new 23H2 OS, and prior Azure Stack HCI releases are no longer part of HCIBox or supported by the Jumpstart team. If you've used earlier versions of HCIBox you should read this guide thoroughly to understand the new HCIBox deployment process.

  ![](./media/hci24-overview-1.png)

### Use cases:

- Sandbox environment for getting hands-on with Azure Stack HCI and Azure Arc technologies
- Accelerator for Proof-of-concepts or pilots
- Training tool for skills development
- Demo environment for customer presentations or events
- Rapid integration testing platform

   ![](./media/hci24-overview-2.png)

### Azure Stack HCI capabilities available in HCIBox

**2-node Azure Stack HCI cluster**

HCIBox automatically creates and configures a two-node Azure Stack HCI cluster using nested virtualization with Hyper-V running on an Azure Virtual Machine. This Hyper-V host creates three guest virtual machines: two Azure Stack HCI nodes (AzSHost1, AzSHost2), and one nested Hyper-V host (AzSMGMT). AzSMGMT itself hosts two guest VMs: an Active Directory domain controller, and a Routing and Remote Access Server acting as a virtual router.

  ![](./media/hci24-overview-3.png)

**Virtual machine management**: HCIBox comes with guest VM management in Azure portal. The HCIBox documentation will walk you through how to use this feature, including configuring VM images from Azure marketplace and creating VMs on your cluster.

**Azure Kubernetes Service on Azure Stack HCI**: Azure Stack HCI includes Azure Kubernetes Services on Azure Stack HCI (AKS hybrid) as part of the default configuration. A user script is provided that can be used to create a workload cluster.
