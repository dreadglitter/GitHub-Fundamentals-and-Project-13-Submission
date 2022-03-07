# GitHub-Fundamentals-and-Project-13-Submission
Homework and Project files
# azure-cloud-project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Azure and elk stack diagram](https://github.com/dreadglitter/GitHub-Fundamentals-and-Project-13-Submission/blob/a69be4c468917f979fc7b44341c38c652878ac80/Images/azure_network_elk-.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

![Filebeat playbook](https://github.com/dreadglitter/GitHub-Fundamentals-and-Project-13-Submission/blob/a69be4c468917f979fc7b44341c38c652878ac80/Images/filebeat_playbook.PNG)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the DVWA Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting access to the network.
-Load balancer provides DDOS and redundancy protection. What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system files.
- Installed filebeat to watch for changes in the system and log files.
- Instaled metricbeat to record metric's from each VM in the network.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web 1    |    VM    | 10.1.0.13  | Linux            |
| Web 2    |    VM    | 10.1.0.14  |  Linux           |
| Web  3   |    VM    | 10.1.0.7   |  Linux           |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.***.***.**

Machines within the network can only be accessed by the Jumpbox and elk stack VM's.
- Web 1 with Private IP of 10.1.0.13 has access to the Jumpbox and elk stack
- Web 2 with Private IP of 10.1.0.14 has access to the Jumpbox and elk stack
- Web 3 with Private IP of 10.1.0.7 has access to the Jumpbox and elk stack

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1             |
| Web 1    | No                  | 10.1.0.13            |
| Web 2    | No                  | 10.1.0.14            |
| Web 3    | No                  | 10.1.0.7             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The advantage of using Ansible to automate setup on each of the VM's and the elk machine is the ablity to easly scale up or down depending on the need.

The playbook implements the following tasks:
- Installs docker.io
- Installs python3-pip
- installs Docker module 
- Increases memory used 
- downloads and launch a elk container and allows ports 5601, 9200, and 5044 to be used.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps on elk](https://github.com/dreadglitter/GitHub-Fundamentals-and-Project-13-Submission/blob/6afa788d07d3d68dc8e0b36425bdb188593d8198/Images/docker%20ps%20on%20elk.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.13
- 10.1.0.14
- 10.1.0.7

We have installed the following Beats on these machines:
-fileebeat 7.6.1
-metricbeat 7.6.1

These Beats allow us to collect the following information from each machine:
- Filebests allows us to collet agent.host files and other system logs that change for any reason.  The mectricbeats collects and logs host system metric's such as operating sysem and other system status's.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to Ansible instance.
- Update the hosts file to include elk serever
- Run the playbook, and navigate to http://13.67.178.128:5601/app/kibana to check that the installation worked as expected.




