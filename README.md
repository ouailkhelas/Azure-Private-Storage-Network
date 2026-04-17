## 📋 Overview

This project demonstrates how to securely access an Azure Storage Account through a Private Endpoint, eliminating public exposure. All traffic flows within Azure's private backbone network, ensuring high security, low latency, and compliance with modern cloud standards.

## 🧱 Architecture

The solution consists of the following components:

- **Storage Account** → Target service (Blob, File, Queue, Table)
- **Private Endpoint** → Provides a private IP address inside the VNet
- **Network Interface (NIC)** → Linked to the Private Endpoint
- **Virtual Network (VNet)** → Isolated network environment
- **Network Security Group (NSG)** → Controls inbound/outbound traffic

### 🔄 Traffic Flow

```
Client (inside VNet)
        ⬇
Private Endpoint (Private IP)
        ⬇
Storage Account (No public access)
```

## ✨ Features

- 🔒 **Private access only** — No public endpoint exposure
- 🌐 **Full network isolation** — Using Azure Virtual Network
- 🛡️ **Traffic filtering** — Controlled via Network Security Groups
- ⚡ **Optimized performance** — Traffic routed through Azure backbone
- 📦 **Secure communication** — All Storage services accessible privately

## 🛠️ Azure Services Used

- Azure Storage Account
- Azure Private Endpoint
- Azure Virtual Network (VNet)
- Azure Network Security Group (NSG)
- Azure Network Interface (NIC)

## 🚀 Deployment

### Prerequisites

- Azure CLI installed
- Active Azure subscription
- Appropriate permissions to create resources

### Using Bicep

1. **Create a resource group:**

```bash
az group create --name rg-private-storage --location francecentral
```

2. **Deploy the infrastructure:**

```bash
az deployment group create \
  --resource-group rg-private-storage \
  --template-file main.bicep
```

## 🔐 Security Design

| Component | Configuration |
|-----------|---------------|
| **Public network access** | Disabled |
| **Access method** | Private Endpoint only |
| **NSG rules** | Allow internal VNet traffic<br>Deny external/public traffic |
| **Encryption** | In-transit and at-rest |

## 🧪 Validation

Follow these steps to validate your deployment:

1. ✅ Verify Private Endpoint has a private IP assigned
2. ✅ Test access from a VM inside the VNet (should succeed)
3. ❌ Test access from the internet (should fail)

### Example validation commands:

```bash
# Check Private Endpoint IP
az network private-endpoint show \
  --resource-group rg-private-storage \
  --name <endpoint-name> \
  --query 'customDnsConfigs[0].ipAddresses[0]'

# Test connectivity from a VM in the VNet
az storage blob list \
  --account-name <storage-account-name> \
  --container-name <container-name>
```

## 🎯 Use Cases

- Secure cloud storage for enterprise applications
- Internal microservices communication
- Compliance-focused architectures (HIPAA, GDPR, etc.)
- Data residency and sovereignty requirements
- Zero-trust network architectures

## 📚 Additional Resources

- [Azure Private Endpoint Documentation](https://docs.microsoft.com/azure/private-link/private-endpoint-overview)
- [Azure Storage Security Guide](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
- [Azure Bicep Documentation](https://docs.microsoft.com/azure/azure-resource-manager/bicep/)

## 👤 Author

**Ouail Mokhtar Khelas**
---
