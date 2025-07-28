### Virtual Network (Vnet)

An Azure Virtual Network (VNET) is a private network within Azure where resource like virtual machines can securely communicate with each other, the internet and on-premises network. 
-- Define the IP address range (CIDR block)
-- Supports subnets, DNS, routing, NSGs, and more

In this project, two Vnet was deployed:
CoreServicesvnet 10.20.0.0/16 ----- Using Azure portal
ManufacturingVnet  10.30.0.0/16 --- Using ARM template.json


### Subnet
Subnets divide a virtual network into smaller, logical sections. Each subnet has its own range of Ip addresses and can be used to isolate workloads.
-- Useful for grouping similarservices(e.g frontend, backend, database)
-- You can apply separate security rules and routing per subnet

Two Subnets are created each for Vnet
Vnet ------ CoreServicesvnet 10.20.0.0/16

      --CoreServicesvnet-SharedServicesSubnet 10.20.10.0/24 

      --CoreServicesvnet-DatabaseSubnet 10.20.20.0/24 

ManufacturingVnet  10.30.0.0/16 --- Using ARM template.json
    -- ManufacturingVnet-Sensor1 10.30.20.0/24 

    -- ManufacturingVnet-Sensor2 10.30.21.0/24 

### Application Security Group (ASG)
An ASG is used to group VM NICs (network interfaces) logically. This allows you to apply network security rules based on groupsrather than IPs or subnets.
-- Helps manage access between tiers (eg web, app, DB)
-- Flexible and scalable for dynamic VM sets

ASG is defined as asg-web 

### Network Security Group (NSG)
An NSG acts like a virtual firewall for controlling inbound and outbound traffic to VMs, subnets,or NICs.

 -- Contains rules that allow or deny traffic based on:
      -- Source/destination ASG : asg-web
      -- Port number (eg TCP 80, 443)
      -- Direction (inbound/outbound)

  NSG myNSGsecure  allows incoming HTTP,HTTPS(port 80,443)

### Public DNS
Public DNS is used to map domain names

--You can also configure custom DNS records(A, CNAME) for apps
-- If using Azure DNS Zones, you manage records natively in Azure.

DNS Zones
dokkslink.com




 
