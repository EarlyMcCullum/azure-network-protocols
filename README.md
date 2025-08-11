<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>



1. **Create an NSG**  
   - In the Azure Portal, search for **Network Security Groups** and click **Create**.  
   - Fill in details like name, resource group, and region.

2. **Attach the NSG**  
   - Associate the NSG with a **subnet** or a **VM’s network interface**.  
   - Subnet-level rules apply to all VMs in that subnet.

3. **Define Rules**  
   - Add **Inbound** and **Outbound** rules for allowed or denied traffic.  
   - Set source/destination IPs, port ranges, and protocols.

4. **Inspect Traffic**  
   - Use **Azure Network Watcher → IP Flow Verify** to test connectivity.  
   - See if traffic is allowed or blocked and which rule is responsible.

---

## Visual Walkthrough
<img src="https://i.imgur.com/x6BXXrM.png" alt="Traffic Examination"/>
</p>
Step 1: Create a Network Security Group (NSG)
Action: In the Azure Portal, navigate to Network Security Groups and click Create (fill in details like name, resource group, and region).

What you see: The NSG creation form with fields for subscription, resource group, name, and region.

Why it matters: This creates the NSG foundation to enforce network access policies. 

<img src="https://i.imgur.com/Iu50NOp.png" alt="Traffic Examination"/>
</p>
Step 2: Associate NSG to a Subnet
Action: Inside the NSG's settings, go to the Subnets section and click Associate, then choose the appropriate Virtual Network and Subnet.

What you see: The Azure interface showing the option to link the NSG to a subnet.

Why it matters: Associating the NSG ensures its rules apply to all VMs within that subnet.

<img src="https://i.imgur.com/ix0Masf.png" alt="Traffic Examination"/>
</p>
Step 3: Verify Traffic with IP Flow Verify
Action: Use Azure Network Watcher → IP Flow Verify, fill in VM, protocol, direction (Inbound/Outbound), and port details, then run the test.

What you see: The IP Flow Verify tool; you can enter packet information and view if traffic is allowed or blocked, and identify the rule responsible.

Why it matters: It helps troubleshoot connectivity issues by showing which NSG rule is affecting traffic.

Notes
- NSGs act like a firewall for your Azure resources.
- Rules are processed in order of priority (lowest number first).
- Always test your rules to avoid accidental service outages.
