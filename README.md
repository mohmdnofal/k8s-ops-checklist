# k8s-ops-checklist (Under Construction)

This project is intended to provide insights and recommendations on how you can setup your Kubernetes cluster in Azure, the project will be focused on the 2 managed platforms Azure Kubernetes Service and Azure Red Hat OpenShift v4. 

The main focus here is Network and Security in a hybrid environment.  

The story:

* A WordPress WebSite hosted in an AKS or ARO cluster 
Why WordPress? WordPress is Familiar for most folks and has many components, FrontEnd, BackEnd, Databases, Requires Container Images, requires objects that can be stored in an Object Storage, requires management for the content, etc... so as you can imagine WordPress can get very complex, and in here we will exploit all these complexities 
* The WordPress will require remote management from on-premises network
* The WordPress will require access to some on-premises assets 
* The Website will require security (SSL Offloading, Waf, DDoS, etc..) 
* The Cluster should be secure as well (Secure AuthN and AuthZ)


## What we need to accomplish 

* Management, all management access will be handled by an on premises network over VPN 
* Cluster will have secure egress flow using Azure Firewall 
* Cluster will have secure ingress flow using Azure Application Gateway 
* The Website will make use of Azure caching offering (CDN or FrontDoor)




## Decisions 

1. VNET Setup 
* Hub Design
* Spoke Design 
  - based on the network model (Kubenet or CNI) sizing will be decided 
  - UDRs on the Spoke
  - Peering on the Spoke

* On-Premise Access using VPN 
* 
2. Egress Traffic 
* Egress to internet 
* Egress to on-premises
3. Ingress 
* Ingress from internet 
  - ingress to a WAF
  - CDN required? 
* Ingress from on-premises 
1. Authentication and Authorization 
* AAD integration
* RBAC setup 
5. Azure Service access 
* what to use Private link or service endpoints 
* We require access to ACR and Storage Account, Azure Disk, etc..
6. Dev environment setup 
7. Logging and Monitoring 