# GCP Infrastructure basics

###Intro

This doc serves as both a guide and a workshop and help introduce beginners to the Google Cloud Platform.
In GCP, much of the basic networking is simplified so very little focus will be put on the networking aspect.
This also wil not touch on serverless infrastructure or Big Data.

## Context

You are looking to migrate a simple web application that is currently running on a barebones server in your data center to GCP.
As this is a public facing server, there is no need for a VPN or dealing with possible IP range overlap. There is no image to
import either, you just need to build up the infrastructure in GCP and the app team will handle moving the application.

### Step 1

In your GCP project, build 2 GCE VM Linux instances. One of these will act as the web server, the other will act as a bastion.

#### Web server
The webserver needs to be configured as a LAMP stack. There are a number of ways to achieve this, use which ever way your feel
most comfortable with (marketplace image, script, configuring it manually). The instance needs to have a static external IP address
and needs to allow external access on ports 443 and 8080. No other ports should be exposed.

Ideally, the server should contain 2 disks, one for boot and one for the LAMP DB data path. (This is optional, don't lose too much time here)

#### Bastion
The webserver will not allow connections on any port other than 443 and 8080, thus you will be unable to SSH to it. To keep the
environment secure, you need to create a Bastion server. The bastion should only allow SSH access from specific public IPs (including yours).
To ensure the security of the Bastion, no scopes or permissions should be assigned to it. The bastion will be running little to no
applications so it should also be a small machine type. As with the webserver, the bastion should come with certain tools for debugging, 
use your preferred method to install the following:
- curl
- nmap
- Apache Bench
- tcpdump

Once both are created, make sure that you can [SSH to the bastion server](https://cloud.google.com/compute/docs/instances/connecting-to-instance#gcetools), then from the bastion to the web server.
You should also see the default apache web page if you visit the web server's exernal IP.
