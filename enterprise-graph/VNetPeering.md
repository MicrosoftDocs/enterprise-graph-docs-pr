---
title: Enable VNet Peering with Enterprise Graph by Microsoft
description: Learn how to enable VNet peering with Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: tutorial
ms.date: 07/29/2019
ms.author: coch
---

#VNet peering

Azure virtual network peering could enable you seamlessly connect two Azure Vnet even cross subscription.  Once peered, the virtual networks appear as one, for connectivity purposes. The traffic between virtual machines in the peered virtual networks is routed through the Microsoft backbone infrastructure, much like traffic is routed between virtual machines in the same virtual network, through private IP addresses only.

To enable Vnet Peering in Enterprise Graph, please make sure the "Use VNet Peering" box is checked when you provision it. The VNet subnet range is the private ip addresses that can be used by the physical resources in MS subnet. Please make sure you leave at least 128 ip addresses.
![Source schema view](media/vnetpeering/vnetpeering.png)

#Steps to enable VNet Peering in Enterprise graph

Enabling VNet Peering needs collaboration betweeen user of customer subscription and user of Microsoft subscription. 

Step 1: Assign network contributor role of the customer VNet to the user of MS MEG subscription.
Step 2: Assigned network contributor role of the MS MEG VNet to the user of customer subscription.
Step 3: Inform user of MS MEG subscription enable VNet peering. When it is done, user of customer subscription needs to do the following steps to configure NSG rules.
Step 4: Install powershell 6.2
Step 5: Execute the powershell 6.2 you just installed with administrator role.   
Step 6: Set-ExecutionPolicy unrestricted 
Step 7: on Powershell log in using command "Connect-AzAccount", follow the instruction to log in customer subscription 
Step 8: Obtain nsg_Az.ps1 script from user of MS subscription, and run it to configure NSG rules, example: 
nsg_Az.ps1 <ms-subscription> <ms-resource-group> <ms-vnet> <customer-subscription> <customer-resource-group> <customer-vnet>