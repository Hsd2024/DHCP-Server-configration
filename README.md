# DHCP-Server-configration
Configuring a DHCP (Dynamic Host Configuration Protocol) server for a business network involves more complex and structured settings compared to home networks. The goal is to efficiently manage IP addresses for a larger number of devices and to support business needs such as scalability, network segmentation, security, and redundancy.

![DHCP Diagram](https://github.com/user-attachments/assets/52b2f1c6-b22c-44e6-9aac-0eea64005578)

Let's go one by one how to do it,

# Step 1: Plan the Network Addressing Scheme

Before configuring DHCP, it’s important to plan out your network's addressing scheme to ensure it meets the needs of your business and allows for future growth.

Example for a medium-sized business:

Use 192.168.1.0/24 for general devices.

Use 192.168.2.0/24 for VoIP phones.

Use 192.168.3.0/24 for printers or security devices.

# Step 2: Choose a DHCP Server
Dedicated DHCP Server: In business environments, you can use a dedicated Windows Server or Linux server to run the DHCP server. I chose Windows Server.

# Step 3: Configure the DHCP Server

Set IP Address Range (Scope)
Define the range of IP addresses the DHCP server will assign to clients. For example:

Start IP: 192.168.1.100

End IP: 192.168.1.200

Subnet mask 255.255.255.0

Default Gateway (Router)
Define the default gateway IP address, For example, 192.168.1.1.

DNS Servers
Set the DNS servers to be used by clients. This can either be:
The local DNS server within your business. or
Public DNS servers like Google DNS (8.8.8.8 and 8.8.4.4) or Cloudflare (1.1.1.1).

If you use internal services or custom domains, point to internal DNS servers.

 Lease Time
Set the lease time (how long an IP address is valid for a client). For business environments, shorter lease times may be used for devices that move around frequently (e.g., laptops), while longer times can be set for fixed devices (e.g., servers).

Example: 8 hours, 24 hours, or even 1 week for servers and fixed equipment.

DHCP Reservations (Static IP Mapping)
For certain devices (e.g., servers, printers, or network appliances), you’ll want to reserve specific IP addresses so that those devices always receive the same IP address.
To do this, associate a specific MAC address to an IP address in the DHCP server settings.

# Step 4: Implement Redundancy and High Availability
In a business network, redundancy and high availability are essential for minimizing downtime.

DHCP Failover: Set up DHCP failover to ensure continuity in case one DHCP server goes down. 
Failover Setup: For a Windows-based DHCP server, you can configure a failover relationship between two DHCP servers, ensuring that IP address leasing is always available.

# Step 5: Implement Security Measures
Security is crucial in a business network.

DHCP Snooping: Implement DHCP snooping on network switches to prevent rogue DHCP servers from assigning incorrect IP addresses to clients.

IP Address Filtering: Consider using IP filtering to only allow specific devices to request IP addresses (based on MAC addresses).

Network Segmentation: Use VLANs (Virtual Local Area Networks) to segment different departments or services (e.g., separating HR from finance or isolating guest networks). Each segment can have its own DHCP scope and policies.

Access Control Lists (ACLs): Set up ACLs on routers or switches to control which devices can access the DHCP server.

Step 6: Monitor and Maintain the DHCP Server

DHCP Monitoring Tools: Use monitoring tools to track DHCP server performance and usage, ensuring IP address allocation is efficient.

Capacity Planning: Ensure that your DHCP scopes have enough IP addresses to cover all devices on your network, especially as your business grows.

Step 7: Test the Configuration
Test by connecting different types of devices to the network (computers, phones, printers, etc.).

Ensure they receive the correct IP addresses and can access internal and external resources (like the internet or servers).





























