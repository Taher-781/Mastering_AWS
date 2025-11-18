1. VPC Creation
• Search for "VPC" and select "Create VPC".
• Name the VPC (e.g., three-tier).
• Assign the CIDR range: 10.0.0.0/16. This /16 mask yields 65,534 IP addresses.
• The selection for this should remain the private Network.
• Post-Creation Step: Edit the VPC settings to enable DNS hostnames, which are necessary for Public Access.

2. Subnet Creation
The goal is to create three subnets within the three-tier VPC:
• Subnet 1 (App Servers):
    ◦ Availability Zone: US 1a.
    ◦ CIDR Range: 10.0.1.0/24 (This yields 254 IPs).
• Subnet 2 (Web Servers):
    ◦ Availability Zone: US 1b.
    ◦ CIDR Range: 10.0.2.0/24.
• Subnet 3 (DB Servers):
    ◦ Availability Zone: US 1c.
    ◦ CIDR Range: 10.0.3.0/24.
    
3. Internet Gateway Creation and Attachment
• Create a new Internet Gateway (IGW).
• Click "Actions" and select "Attach to VPC," choosing the newly created three-tier VPC. This signals to the IGW that it should allow traffic for this VPC.

4. Route Table Creation and Configuration
• Create a Route Table (e.g., three-tier RT) and associate it with the three-tier VPC.
• Edit Routes: This step defines where the traffic goes.
    ◦ The destination 0.0.0.0/0 (which represents all public traffic) is used.
    ◦ The target is set to the newly created Internet Gateway. (Note: The instructor advises that allowing all traffic via 0.0.0.0/0 should be avoided in real-time, production environments.)
• Subnet Association: Associate the Route Table with all three subnets (Web Servers, App Servers, and DB Servers). This configuration is necessary to allow these subnets to route traffic outside of the VPC.
