<h1>Recovery-Hyper-V-VM-Replication-Guide</h1>

## Introduction

Azure Site Recovery (ASR) is a cloud-based disaster recovery solution offered by Microsoft Azure that provides businesses with a streamlined way to protect and replicate virtual machines (VMs) from on-premises environments, such as those hosted on Hyper-V, to Azure. ASR enables organizations to ensure business continuity by minimizing downtime and safeguarding essential workloads through automated replication, failover, and failback processes.

### Overview of Azure Site Recovery (ASR)
Azure Site Recovery orchestrates and automates the replication of on-premises VMs to Azure or a secondary datacenter, creating a resilient disaster recovery strategy that can be tested and validated periodically. Supporting Hyper-V, VMware, and physical servers, ASR replicates data to Azure, providing a reliable recovery option. The integrated management and monitoring tools in ASR simplify disaster recovery processes and ensure seamless transitions with minimal disruption.

### Purpose of This Guide
This guide serves as a comprehensive resource for IT administrators and cloud engineers aiming to use ASR for Hyper-V VM replication. It includes step-by-step instructions on setting up, configuring, and managing ASR for Hyper-V VMs in Azure. This documentation will help you:
- **Prepare your environment** by covering prerequisites and setup steps.
- **Configure replication** of Hyper-V VMs to Azure.
- **Manage failover and failback** to reduce downtime during critical scenarios.

### Benefits of Replicating Hyper-V VMs to Azure
Using ASR to replicate Hyper-V VMs to Azure offers several advantages:

- **Enhanced Business Continuity**: ASR automates failover and recovery, minimizing downtime in disaster situations and enabling fast operational resumption.
- **Cost-Effective Disaster Recovery**: Leveraging Azure as a disaster recovery site eliminates the expense of maintaining a secondary datacenter.
- **Scalability and Flexibility**: Azure’s scalable infrastructure supports workloads of varying sizes, adapting to business growth.
- **Centralized Management and Monitoring**: ASR integrates with the Azure portal, offering easy management and real-time monitoring of replication and failover.
- **Security and Compliance**: ASR provides built-in encryption and aligns with Microsoft’s compliance certifications, ensuring secure replication and failover of workloads.

This guide will help you realize these benefits as you configure and manage ASR for Hyper-V VM replication, establishing a robust disaster recovery strategy.

## Prerequisites
- Required subscriptions and permissions
- Supported Hyper-V versions and configurations
- Network and storage considerations
- Preparing your environment


## Setup and Configuration
### Step 1: Setting Up Azure Site Recovery
- Go to azure portal and browse to Azure recovery service vault
- Click create vault, enter details and fill to suit your needs
<img width="1680" alt="1 5" src="https://github.com/user-attachments/assets/0a8290ef-f335-46af-abdb-c2d3fe63ca1c">

The vault has been created and now we neede to prepare our hyper-v serevr for the integration 

### Step 2: Preparing Hyper-V Hosts
- In the site recovery vault, click site recovery and click prepare infrastructure 
<img width="1680" alt="2" src="https://github.com/user-attachments/assets/0bf6ec47-ceb2-4a85-b7cd-bd8280aaac13">
- You are taken to an infrastrcuture integration step, select the "Yes, i have done it" option
<img width="1680" alt="3" src="https://github.com/user-attachments/assets/68606960-4337-452a-b3db-c36a5b67ab59">
- In the next step, select the no option, create and add Hyper-v site and give it a name
<img width="1680" alt="5" src="https://github.com/user-attachments/assets/fc61a405-fb39-4301-aa9b-5417b67a6bd6">
- Click the "add Hyper-v server" option to add a server. In this step, you will need to download the "installer for the microsoft azure site recovery provider" and "vault registration key" on the hyper-v host to finish the integration
<img width="1680" alt="6" src="https://github.com/user-attachments/assets/b193bbac-8775-4a3e-9a0d-dfe283acbe94">
- After downloading the installer, proceed to installation
<img width="1680" alt="8" src="https://github.com/user-attachments/assets/311eb339-b8d3-4e5d-9683-2c3ab4737747">
- Click finish and proceed to browse to the key file and click next
<img width="1680" alt="9" src="https://github.com/user-attachments/assets/617b654e-5135-46b3-bfcb-6d385a63cffe">
- In the next option, select the option that best suits your personal or ogarnizational needs
<img width="1680" alt="10" src="https://github.com/user-attachments/assets/66819dde-c319-42a6-85e8-7e7e4cd7cec4">
- Then finish up the installation
<img width="1680" alt="10 5" src="https://github.com/user-attachments/assets/2bcb15d9-9e6b-44ef-a3c2-7444fccfd632">
- Go back to your azure portal, then go back to the vault and click site recovery infrastructure
<img width="1680" alt="11 25" src="https://github.com/user-attachments/assets/69fac3eb-53cf-4d5e-899d-1555aa93b779">
- Select the "Hyper-V Hosts" option 
<img width="1680" alt="11 50" src="https://github.com/user-attachments/assets/d158fcde-e524-408a-a081-f5504b35e27a">
- You will see your hyper-v host there, and showing connected
<img width="1680" alt="11 75" src="https://github.com/user-attachments/assets/05092f63-6566-4fb4-997f-b2ea302e342b">
- Then go back to the prepare infrastructure step and your server should be showing, click next and move to the next step 
<img width="1680" alt="12 5" src="https://github.com/user-attachments/assets/f8655363-6d49-4598-a4b0-7b0b31d691d4">
- In the replication policy, select any policy or create one
<img width="1680" alt="13" src="https://github.com/user-attachments/assets/23501dff-14cd-4c0e-bbf9-77c66254540d">
- Click the create option and create a policy
<img width="1680" alt="13 5" src="https://github.com/user-attachments/assets/16a6b1fb-cc02-42ca-a998-49dbb3c9aa7d">
<img width="1680" alt="13 55" src="https://github.com/user-attachments/assets/e77865bd-b0d9-43bc-a4d2-83245eb515af">
- Then finish the process and prepare the infrastructure
<img width="1680" alt="13 75" src="https://github.com/user-attachments/assets/1fac6c9e-4ba1-4cea-8753-f20ba9082b4d">

### Step 3: Replicating Hyper-V VMs
- Go the site recovery and click " enable replication"
<img width="1680" alt="14" src="https://github.com/user-attachments/assets/086b9ef0-7d37-428a-bf89-75afc8b52083">
- Select the appropriate options, and when you get to the " Replication settions option" select your vm you want to replicate, select the os disk, disk type and target name 
<img width="1680" alt="16" src="https://github.com/user-attachments/assets/646a0a66-db6f-4506-b69f-0ccde7317aff">
- Select your created or previously existing policy and finish the replication 
<img width="1680" alt="16 5" src="https://github.com/user-attachments/assets/c4579782-01d9-448d-9efa-e20a5c80816c">
- Go to the vault and then in overview, select the site recovery option. It should show you the connection from azure to your host, your replication health etc
<img width="1680" alt="17" src="https://github.com/user-attachments/assets/f31fd48e-e796-4d51-8ff7-9d8d638b05c0">
-  Then under replication health click on the "view all vm's" to see the synchronization status, wait till its a 100% then the replication is complete 
<img width="1680" alt="17 5" src="https://github.com/user-attachments/assets/5a9b99a8-1a54-451e-9957-897cb4d02959">

## Managing Replication









































