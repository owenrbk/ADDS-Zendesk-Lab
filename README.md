# ADDS & Entra/Zendesk Lab
Enterprise Infrastructure Simulation of Windows Server Active Directory Domain Services and Entra ID provisioning for Zendesk, steps with images.

## Project Overview
This lab simulates a professional corporate environment by bridging **On-Premises Windows Infrastructure** with **Cloud-based SaaS** tools. I built a private network from scratch, configured core networking services, and integrated a ticketing system to handle real-world Service Desk scenarios.

## Creating the Virtual Machines
* I created two virtual machines with Microsoft Hyper-V, allocating 4GB of RAM to each and 80GB of virtual disk space. One is the domain controller (DC01) with Windows Server 2022 and the other is a client workstation (CLIENT01) with Windows 10.
![Hyper-V Setup](images/1.png)
* I created two virtual network interfaces, one called Internal-Lab, which connects the Client to the Domain Controller, and one called Internet-Bridge, which bridges internet connectivity from the Domain Controller to the Client. By configuring this dual-homed setup, I established a secure gateway where the Domain Controller functions as a router, providing the internal lab assets (Client) with WAN access through Network Address Translation (NAT) without exposing them directly to the public internet. We configure this fully when we set up RRAS.
![Network Interfaces](images/3.png)
![Network Interface Setup, Internal Only and External Virtual Switch](images/4.png)

## Configuration of DC01
* When Windows Server OS finished installing, I entered "Administrator" for the username and a strong password I could remember.
* Upon logging in, I went to Network Connections (run ncpa.cpl) and configured a static IP
![Static IP](images/2.png)

## Configuring Active Directory
* In the Server Manager, I click Add Roles and Features under Manage in the top right corner.
* I select "Role-based or feature-based installation".
* I select DC01 as the Server.
* I select Active Directory Domain Services, DHCP Server, DNS Server, and Remote Access. Any default features I also add.
* I confirm installation and click install.

## Promoting to Domain Controller
* Once the features are done installing, I click the yellow flag in the top right corner and click promote to domain controller
![Promote to DC](images/5.png)
* In the AD DS Wizard, I click "Add a new forest". For now, my root domain name is "lab.local"
![Domain Name](images/6.png)
* In the next steps, I leave them as default and I input a Directory Services Restore Mode password, which is something that needs to be saved in case AD is in need of recovery.
* I leave the rest of the steps as the default and ignore warnings in the Prerequisites Check, as is this a lab environment. Then I click install.
![Domain Name](images/7.png)
