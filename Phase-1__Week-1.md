# Week 1: Azure Storage & Security Foundation

## Objective
Master **Azure Data Lake Storage (ADLS) Gen2** and **Identity Management**, with clear mental mapping from AWS concepts.

---

## Monday: The Cloud Pivot (2 Hours)

### Focus
Understanding the Azure hierarchy vs. AWS.

### Tasks
- **Azure Structure**
  - Management Groups → Subscriptions → Resource Groups → Resources  
  - AWS equivalent: Organization → Accounts → Tags

- **Account Setup**
  - Create your Azure Free Account
  - https://azure.microsoft.com/free/

- **Hands-on**
  - Create your first Resource Group:
    ```
    rg-data-engineer-prod
    ```

### Resource
- Microsoft Learn: **Azure Fundamentals (Part 1)**
https://learn.microsoft.com/en-us/training/paths/az-900-describe-cloud-concepts/
---

## Tuesday: ADLS Gen2 vs. S3 (2 Hours)

### Focus
Why ADLS Gen2 is built for big data (unlike flat S3).

### Tasks
- **Storage Accounts**
  - Create a Storage Account
  - Enable **Hierarchical Namespace (HNS)**
  - This is what turns Blob Storage into a Data Lake

- **Endpoints**
  - Blob endpoint (Web): object storage access
  - DFS endpoint: big data and analytics access

### Resource
- **ADLS Gen2 Introduction**
https://learn.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction
---

## Wednesday: Security & Identity (2 Hours)

### Focus
Moving from AWS IAM to **Azure Entra ID** (formerly Azure AD).

### Tasks
- **RBAC**
  - Assign yourself the role:
    - `Storage Blob Data Contributor`

- **Access Models**
  - Understand **Account Keys** vs. **Shared Access Signatures (SAS)**
  - Why SAS is safer and more granular

### Resource
- **Secure your Azure Storage**
[https://learn.microsoft.com/en-us/azure/storage/common/storage-network-security](https://learn.microsoft.com/en-us/azure/storage/blobs/security-recommendations)
---

## Thursday: Networking & Firewalls (2 Hours)

### Focus
Private Endpoints and Service Endpoints  
(AWS VPC Endpoints equivalent)

### Tasks
- **Networking**
  - Restrict your Storage Account access to your own public IP only

- **Tooling**
  - Download and install **Azure Storage Explorer**
  - Connect using your Microsoft login
  - https://azure.microsoft.com/en-us/products/storage/storage-explorer/

### Resource
- **Configure Azure Storage Firewalls**
https://learn.microsoft.com/en-us/azure/storage/common/storage-network-security
---

## Friday: Data Lifecycles & Cold Storage (2 Hours)

### Focus
Cost control with Hot, Cool, and Archive tiers.

### Tasks
- **Lifecycle Management**
  - Create a rule to move data:
    - Hot → Archive after 30 days
  - AWS equivalent: S3 Lifecycle Rules

- **Soft Delete**
  - Enable Soft Delete for blobs
  - Protect against accidental deletions

### Resource
- **Optimize costs with Lifecycle Management**
https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview
---

## Weekend: The “Big Data Migration” Lab (8 Hours)

### Saturday: Practical Implementation (4 Hours)

#### The Medallion Setup
Inside your Storage Account, create three containers:
- `01-bronze`
- `02-silver`
- `03-gold`

#### The Dataset
- Download a public dataset (example: **NYC Taxi Data**)
- https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

#### Upload
- Use **AzCopy** (AWS `aws s3 cp` equivalent)
- Upload ~10GB of data into the `01-bronze` container

---

### Sunday: Governance & Documentation (4 Hours)

#### Logging
- Enable **Diagnostic Settings** on your Storage Account
- Track who accessed which files and when

#### Comparison Matrix
Create a personal cheat sheet (Excel or Notion):

| AWS | Azure |
|----|------|
| S3 Bucket | Azure Container |
| IAM Policy | Azure RBAC |
| S3 Intelligent Tiering | Azure Lifecycle Management |

#### Blog Preparation
Outline your first technical blog:

**“Day 1 for an AWS Engineer on Azure: What I Wish I Knew About ADLS”**

---

## Week 1 Quick-Start Links

- **Tool**
  - Install **Azure CLI**  https://learn.microsoft.com/en-us/cli/azure/install-azure-cli
  - Essential for daily 2-hour sessions

- **Documentation**
  - **DP-203 Study Guide**  
  - Keep this open as your North Star
  - https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/dp-203
