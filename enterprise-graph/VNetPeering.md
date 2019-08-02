---
title: Enable VNet Peering with Enterprise Graph by Microsoft
description: Learn how to enable VNet peering with Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: tutorial
ms.date: 07/29/2019
ms.author: coch
---

# VNet peering

Azure virtual network peering could enable you seamlessly connect two Azure virtual networks across Azure Tenents. Once peered, the virtual networks appear as one, for connectivity purposes. The traffic between virtual machines in the peered virtual networks is routed through the Microsoft backbone infrastructure, much like traffic is routed between virtual machines in the same virtual network, through private IP addresses only.

To enable VNet Peering in Enterprise Graph, please make sure the "Use VNet Peering" box is checked when you provision it. The VNet subnet range is the private ip addresses that can be used by the physical resources in MS subnet. Please make sure you leave at least 128 ip addresses.
![Source schema view](media/vnetpeering/vnetpeering.PNG)

# Steps to enable VNet Peering in Enterprise graph

Enabling VNet Peering needs collaboration betweeen customer and Microsoft admins.

* Customer admin assigns network contributor role of the customer VNet to a MS admin user from MEG team.
* MEG admin assigns network contributor role of the MS MEG VNet to a customer admin user.
* Customer admin informs MEG admin to enable VNet peering. When it is done, customer admin can do the following steps to configure NSG rules to block the traffic from MS VNet to Customer VNet to improve security.

* Install powershell 6.2 on a Machine/VM in customer VNet.
* Execute the powershell with administrator role.
* Run "``Set-ExecutionPolicy unrestricted``" to set execution policy unrestricted.
* Run command "``Connect-AzAccount``", and follow the instructions to log in customer subscription.
* Obtain nsg_Az.ps1 script from MS Admin, and use the following command to configure NSG rules.

```
nsg_Az.ps1 <ms-subscription> <ms-resource-group> <ms-vnet> <customer-subscription> <customer-resource-group> <customer-vnet>
```