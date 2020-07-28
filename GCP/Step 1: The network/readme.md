# Creating the network

## Context

Each project has a default VPC network, this default network uses a very large range of IPs by default and has multiple insecure default firewall rules. As such, you will be creating your own network.

### Step 1: The VPCs

You will need to create a new VPC network. Make this network in any regions you choose, make sure to spread the VPC over a minimum of 3 regions. Each subnet must be a /25 or larger. Define the CIDR blocks for each subnet as you see fit. Once you have built the first VPC network, create a second one, using the same guidelines but make sure to use different regions and make sure the CIDR blocks do not overlap with the first VPC
