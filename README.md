## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![RedTeam Cloud Server](https://github.com/Dannytraj/elk-project/blob/main/RedTeam%20Cloud%20Server.png)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the __.yml__ file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/Dannytraj/elk-project/tree/main/Ansible%20Playbook
  
  This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly **available**, in addition to restricting __access__ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers protect the network from DDoS attacks by re-routing traffic. The advantage of a jump box is it gives users access to a single enrty point which is easy to secure and monitor.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **network** and system **logs**.
- _TODO: What does Filebeat watch for? It monitores for any system changes and logs those changes.
- _TODO: What does Metricbeat record? It records metrics and statistics and can be shipped to specified outputs.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    | Webserver| 10.0.0.5   | Linux            |
| Web 2    | Webserver| 10.0.0.6   | Linux            |
| ElkServer| Elkstack | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the **JumpBox** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses **104.210.95.194**

Machines within the network can only be accessed by through the JumpBox via **SSH**.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?The JumpBox VM: IP 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |   104.210.95.194     |
| Web 1    | No                  |                      |
| Web 2    | No                  |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?
The advantage is that you can run commands to multiple servers from the one playbook

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
* Install: docker.io
* Install: python-pip
* Install: docker module
* Command: sysctl -w vm.max_map_count=262144
* Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![DockerPS](https://github.com/Dannytraj/elk-project/blob/main/DockerPS.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring
* Web 1: 10.0.0.5
* Web 2: 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed
* Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
* Filebeat monitores for any file system changes and logs those changes. 
* Metricbeat records metrics and statistics and can be shipped to specified outputs.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? All the .yml files are individual playbooks. Where do you copy it? root@3412fa1f0570:/etc/ansible/roles# ls
filebeat-install.yml  install-elk.yml- 
- _Which file do you update to make Ansible run the playbook on a specific machine? You need to update the hosts file /etc/ansible/hosts in the webservers category by adding the webservers IP and the ELK IP.  How do I specify which machine to install the ELK server on versus which to install Filebeat on? In the install.yml files you need to specify the hosts name you would like the programs installed on.
- _Which URL do you navigate to in order to check that the ELK server is running? http://[public ip of elk VM]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

ssh RedAdmin@104.210.95.194/
sudo docker ps -a/
sudo docker start gracious_ganguly/
sudo docker attach gracious_ganguly/
cd /etc/ansible/roles/
ansible-playbook filebeat-install.yml 

