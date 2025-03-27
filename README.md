---
title: Introduction
layout: home
nav_order: 1
---

# TechExcel: Securely migrate Windows Server and SQL Server workloads to Azure

Tailspin Toys is a global manufacturer of children’s toys that was founded in 1957 with its global headquarters located in Milwaukee, WI. Their mission-critical workloads are currently hosted in an on-premises datacenter and are beginning a journey to modernize and migrate into the cloud using Microsoft Azure.

During the Envision Workshop, Kaylee Frye, CTO of Tailspin Toys, saw the value of digital transformation, adopting the Microsoft Azure cloud, and modernizing their infrastructure. She has already had the Technical Architects at Tailspin Toys begin assessing their current environment and what it will take to migrate to the cloud. They are looking to optimize their technology investments by reducing technical debt, streamlining operations, and simplifying their DevOps workflow. According to Kaylee Frye, "Our development teams have already begun adopting DevOps strategies and implemented CI/CD (continuous integration and continuous delivery) pipelines with Azure DevOps. We really look forward to better streamlining IT operations as we adopt Microsoft Azure for the infrastructure too."

In this lab, attendees will perform steps toward migrating Tailspin Toy's on-premises Windows Server and SQL Server workloads to Azure. Tailspin needs a new Windows Server VM created in Azure for hosting their Web application, an on-premises SQL Server database migrated to Azure SQL Managed Instance, secure Windows Server, and an on-premises Windows Server VM to be Azure Arc-enabled.
Tailspin already has a Hub and Spoke network setup in Azure with Azure Bastion for enabling secure remote management of Azure VM using Azure Bastion. The Azure resources provisioned throughout this lab will be deployed into this environment.

## Azure services and related products

- Azure VMs
- Azure Arc
- Azure SQL Managed Instance
- Azure Networking
- Microsoft Data Migration Assistant
- Azure Data Studio - Azure SQL Migration Extension
- Azure Defender
- Azure Firewall

## Solution architecture

![Diagram showing on-premises network connected to Azure using Azure ExpressRoute with a Hub and Spoke network in Azure. The Spoke VNet contains the migrated Front-end, Back-end, and SQL Database workloads running within Subnets inside the Spoke VNet in Azure.](Hands-on%20lab/images/PreferredSolutionDiagram.png "Preferred Solution Diagram")

The diagram shows an on-premises network connected to Azure using Azure ExpressRoute with a Hub and Spoke network in Azure. The Spoke VNet contains the migrated Front-end, Back-end, and SQL Database workloads running within Subnets inside the Spoke VNet in Azure.

### Redundant Azure ExpressRoute peering locations

Redundant Azure ExpressRoute peering locations provide an additional layer of resiliency and high availability for your connectivity to Azure. With redundant peering locations, you can establish ExpressRoute circuits in two different peering locations, providing a backup connection in case of an outage or disruption in one of the locations.

This redundancy ensures that your connectivity to Azure remains uninterrupted, even in the event of a failure in one of the peering locations. By leveraging redundant peering locations, you can minimize downtime and ensure that your workloads and applications continue to run smoothly, even in the face of unexpected disruptions.

{: .note }
> You can find more information about Redundant Azure ExpressRoute peering locations at [https://learn.microsoft.com/en-us/azure/expressroute/designing-for-disaster-recovery-with-expressroute-privatepeering](https://learn.microsoft.com/en-us/azure/expressroute/designing-for-disaster-recovery-with-expressroute-privatepeering) and [https://azure.microsoft.com/en-us/blog/building-resilient-expressroute-connectivity-for-business-continuity-and-disaster-recovery-2/](https://azure.microsoft.com/en-us/blog/building-resilient-expressroute-connectivity-for-business-continuity-and-disaster-recovery-2/).

### S2S VPN as a backup for ExpressRoute private peering

A Site-to-Site (S2S) VPN connection can be used as a secure failover path for ExpressRoute private peering. This means that if the ExpressRoute connection experiences an outage or disruption, the S2S VPN connection can provide a backup connection to ensure continued connectivity to Azure.

To set up a S2S VPN connection as a backup for ExpressRoute private peering, you need to create two virtual network gateways for the same virtual network: one using the gateway type 'VPN' and the other using the gateway type 'ExpressRoute'. Once the S2S VPN connection is configured, it can provide a secure and reliable failover path for ExpressRoute private peering, ensuring that your connectivity to Azure remains uninterrupted even in the event of an outage or disruption in the ExpressRoute connection. 

{: .note }
> You can find more information about Redundant Azure ExpressRoute peering locations at [https://learn.microsoft.com/en-us/azure/expressroute/use-s2s-vpn-as-backup-for-expressroute-privatepeering](https://learn.microsoft.com/en-us/azure/expressroute/use-s2s-vpn-as-backup-for-expressroute-privatepeering)


### ExpressRoute Gateway SKU Zone redundancy

Azure zone-aware SKUs provide high availability and resiliency for your workloads and applications by distributing resources across multiple availability zones within an Azure region. Each availability zone is a separate physical location with independent power, cooling, and networking, providing protection against datacenter-level failures.

By using zone-aware SKUs, you can deploy your resources, such as virtual machines, managed disks, and load balancers, across multiple availability zones, ensuring that your workloads and applications remain available even if one of the zones experiences an outage. This redundancy helps to minimize downtime and ensure that your services continue to run smoothly, even in the face of unexpected disruptions.

{: .note }
> You can find more information about Azure Availability Zones at [https://learn.microsoft.com/en-us/azure/reliability/availability-zones-overview?tabs=azure-cli](https://learn.microsoft.com/en-us/azure/reliability/availability-zones-overview?tabs=azure-cli).



## Exercises

This lab has exercises on:

* Provisioning a Windows Server VM
* Set up a Windows Server for application migration to Azure
* Migrate an on-premises SQL Server Database to Azure SQL Managed Instance (SQL MI)
* Secure Windows Server
* Enable Azure Arc on an on-premises virtual machine so it can be managed from Azure

This lab is available as GitHub pages [here](https://jonathan-vella.github.io/Securely-migrate-Windows-Server-and-SQL-Server-workloads-to-Azure)


## Prerequisites

For running this lab you will need:

* An Azure subscription without a spending cap.
* A desktop, laptop, or virtual machine and access to install software on that machine.
  

# Project

> This repo has been populated by an initial template to help get you started. Please
> make sure to update the content to build a great experience for community-building.

As the maintainer of this project, please make a few updates:

- Improving this README.MD file to provide a great experience
- Updating SUPPORT.MD with content about this project's support experience
- Understanding the security reporting process in SECURITY.MD
- Remove this section from the README

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
