ELK-PROJECT

<img width="539" alt="94220166-02070300-feae-11ea-958e-7dfb9d3862e9 12" src="https://user-images.githubusercontent.com/93232058/142307216-646fde72-b2f4-4b3d-b3c9-c272abe23091.png">
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above.


This document contains the following details:

Description of the Topologu
Access Policies
ELK Configuration

Beats in Use
Machines Being Monitored


How to Use the Ansible Build


Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
The configuration details of each machine may be found below.



Name
Function
IP Address
Operating System




Jump box
Gateway
10.0.2.4
Linux


DVWA-VM
Webserver
10.0.2.8
Linux


DVWA-VM2
Webserver
10.0.2.9
Linux


ELK Server
ELKserver
10.0.2.7
Linux




Access Policies
The machines on the internal network are not exposed to the public Internet.
Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from home network IP.
Machines within the network can only be accessed by home network IP
A summary of the access policies in place can be found in the table below.



Name
Access
IP Address




Jump box
No
Home network IP


DVWA-VM
No
10.0.2.4 & Home Network IP


DVWA-VM2
No
10.0.2.4 & Home Network IP


ELK Server
No
10.0.2.4 & Home Network IP




Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it minimizes the potenital for error and increases potential to save time.
Roles were used to increase utility and functionality. The setup includes the initial alpha.yml file that refrences each playbook's install files titled alpha.yml. This main file saves time and effort because it can dictate which playbooks are in use; streamlining any future edits of the machines.
The playbook implements the following tasks:

Configure Webservers
Install ELK Server
Install Filebeat
Install Metricbeat

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.


Target Machines & Beats
This ELK server is configured to monitor the following machines:

10.0.2.8
10.0.2.9

We have installed the following Beats on these machines:

Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat forwards and centralizes log data. This information is forwarded to Elasticsearch/Logstash thus providing a GUI to simplify monitoring.
Metricbeat provides a way to provide information such as metrics from the operating system and from services running on a server. Metricbeat collects this data and sends it to Elasticsearch/Logstash (user specified)


Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the roles folder to /etc/ansible/roles.
Update the hosts file to include webserver IP's and ELKServer IP
Run the playbook, and navigate to HTTP://<ELKServer_Public_IP>:5601 to check that the installation worked as expected.


Copy the roles folder (linked above) and files to /etc/ansible/roles
Update the /etc/ansible/hosts file to include the webservers IP's and ELKServer IP
Update each configuration file with ELKServer IP

Kibana - uncomment and replace localhost with local IP for ELK Server
Elasticsearch - uncomment and replace localhost with local IP for ELK Server
