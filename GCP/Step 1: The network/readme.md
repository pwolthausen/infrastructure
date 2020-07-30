# Creating the network

## Context

Each project has a default VPC network, this default network uses a very large range of IPs by default and has multiple insecure default firewall rules. As such, you will be creating your own network.

### Step 1: The VPCs

You will need to create a new VPC network. Make this network in any regions you choose, make sure to spread the VPC over a minimum of 3 regions. Each subnet must be a /25 or larger. Define the CIDR blocks for each subnet as you see fit. Once you have built the first VPC network, create a second one, using the same guidelines but make sure to use different regions and make sure the CIDR blocks do not overlap with the first VPC

### Step 2: Connecting the VPCs

Next you will configure VPC peering between the two VPC networks. This is frequently used to connect two networks that are in different projects and allow the two networks to act as a single, larger network. Refer to GCP public documentation on how to configure the peering.

### Step 3: Firewall rules

Create firewall rules to accomplish the following:
- Allow all internal traffic within each VPC
- Allow all traffic between both VPCs
- Allow HTTP, HTTPS, SSH, and RDP traffic to specific instances using network tags

## Alternate Step 2: Use Cloud VPN

As an alternate to VPC peering, you can use Cloud VPN. Cloud VPN is very useful when you need to connect the VPC to another network outside of GCP (such as on prem or another cloud). You can try using CLoud VPN instead of using VPC peering to test this resource. Connecting two GCP VPC networks (especially in the same project) is not recommended, this should only be used to test out the cloud VPN. 
