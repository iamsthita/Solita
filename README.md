# Solita

This repository is for Solita interview discussion.

## Context:

- Secure an Azure Function app that is currently exposed to the public internet.
- The goal is to restrict access and create a secure environment for the function app to operate.

## High-Level Overview:

- The solution leverages a Virtual Network (VNet) to isolate the Azure Function and control network traffic.
- A private endpoint is created within the VNet, providing a secure access point for authorized resources within the VNet to reach the Azure Function.
- This approach restricts both inbound and outbound traffic, enhancing the overall security posture.

## Key Decisions:

- **VNet Integration:** Enabling VNet integration for the Azure Function restricts inbound and outbound traffic, limiting access to authorized resources.
- **Private Endpoint:** Creating a private endpoint within the VNet provides a secure and private connection point for authorized resources to access the function.
- **Storage Account Access:** Securing the Azure storage account used by the function by restricting access only to the VNet ensures secure communication between the function and storage.

## Stakeholders:

- **Client Members:** To discuss changes to the function app, potential cost implications of upgrading the App Service plan, and the estimated time to implement the security measures (ETA).
- **Cloud Architect/DevOps Engineer:** Responsible for implementing and collaborating on the secure architecture for both Azure Function and VNet deployment.
- **Security Engineer:** Reviews the architecture to ensure it meets security best practices.
- **Application Developers:** Developers who utilize the Azure Function in their applications.

## Challenges:

- **Consumption Plan Limitations:** VNet integration is not supported with the Consumption Hosting option. Upgrading the hosting option to Functions Premium or App service plan is required.
- **Migration Process:** Directly migrating an Azure Function from a Consumption plan to an App Service plan is not currently supported. A recommended approach involves:
  - Creating a new function app within the desired App Service plan.
  - Migrating existing Function configuration and code to the new function app.
- **Downtime:** There might be a brief period of downtime during the traffic migration process.
- **Cost Potential:** App Service plans have associated costs based on the chosen tier, which might be higher compared to the Consumption plan.
- **Testing:** Thoroughly testing the function's functionality and security after implementing the VNet restrictions is crucial.

<br>

**App Service Hosting Plan:**
<br> 
<img width="532" alt="image" src="https://github.com/iamsthita/Solita/assets/132139960/0e34508e-b5ff-4490-9f80-a562bafa36bd">

<br>

**Architecture:**
<br> 
<img width="900" alt="image" src="https://github.com/iamsthita/Solita/assets/132139960/ae0e5afb-1a43-4b85-bbad-5afa8fbec364">


