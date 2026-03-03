# ADDS & Entra/Zendesk Lab
Enterprise Infrastructure Simulation of Windows Server Active Directory Domain Services and Entra ID provisioning for Zendesk, steps with images.

## Project Overview
This lab simulates a professional corporate environment by bridging **On-Premises Windows Infrastructure** with **Cloud-based SaaS** tools. I built a private network from scratch, configured core networking services, and integrated a ticketing system to handle real-world Service Desk scenarios.

## Creating the Virtual Machines
* I created two virtual machines with Microsoft Hyper-V, allocating 4GB of RAM to each and 80GB of virtual disk space. One is the domain controller (DC01) with Windows Server 2022 and the other is a client workstation (CLIENT01) with Windows 10.
![Hyper-V Setup](images/1.png)
* I created two virtual network interfaces, one called 

## Configuration of DC01
* When Windows Server OS finished installing, I entered "Administrator" for the username and the password something strong which I could remember.
* Upon logging in, I went to Network Connections (run ncpa.cpl) and configured a static IP
![Static IP](images/2.png)
