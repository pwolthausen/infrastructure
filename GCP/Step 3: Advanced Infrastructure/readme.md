# Advanced Infrastructure

## Context

Each project has a default VPC network, this default network uses a very large range of IPs by default and has multiple insecure default firewall rules. As such, you will be creating your own network.

### Step 1: Create an instance template



### Step 2: Create Managed Instance Group



### Step 3: HTTTP/S Load Balancer


### Step 4: Infrastructure as Code

Use an Infrastructure as Code software to create all the resources built so far. Use tools such as terraform or Google Deployment Manager. You should be able to recreate the full infrastructure in a new project (or at least a new VPC) that will be nearly identical to the one currently running.
