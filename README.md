# Azure Secure Storage with Private Endpoint

## 🚀 Overview

This project demonstrates a secure Azure Storage architecture using **Private Endpoint** to eliminate public exposure and enforce private-only access inside a Virtual Network (VNet). All communication with the Storage Account is routed through Azure’s private backbone network for improved security and compliance.

All resources were created manually using the **Azure Portal**, and at the final stage, the infrastructure was exported as a **Bicep template** for analysis and documentation purposes.

---

## ✅ What I Built

- 1 Azure Storage Account (Blob, File, Queue, Table)
- 1 Private Endpoint for secure internal access
- 1 Virtual Network (isolated environment)
- 1 Subnet dedicated to Private Endpoint
- 1 Network Security Group (NSG)
- 1 Network Interface (NIC linked to Private Endpoint)
- Private DNS Zone for name resolution

---

## 📍 Architecture Flow
Client VM (Inside VNet)
↓
Private DNS Resolution
↓
Private Endpoint (Private IP)
↓
Azure Storage Account (Public access disabled)


---

## 🛠️ Technologies Used

- Azure Storage Account
- Azure Private Endpoint (Private Link)
- Azure Virtual Network (VNet)
- Azure Network Security Group (NSG)
- Azure Private DNS Zone
- Azure Network Interface

---

## 🏗️ How I Built It

1/All resources were created manually using **Azure Portal**:
2/Created Virtual Network (VNet)
3/Created Subnet for Private Endpoint
4/Deployed Storage Account
5/Disabled public network access
6/Created Private Endpoint
7/NIC was auto-provisioned
8/Configured NSG rules
9/Configured Private DNS Zone

At the end of the deployment:

- Exported **Bicep template** from Azure Portal  
- Used it only for analysis and understanding IaC structure  
- Deployment was NOT done using Bicep (portal-based build)
