# Project 1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project-1/Images/ELK Stack Network Diagram.PNG](Elk Stack Network Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient/redundant, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
  The Load balancer can Protect/mitigate against DDOS attacks that are amied at overloading the netowork when a public facing application is primarily hosted by one server. 
  The Jumpbox reduces the overall attack surface of the network by allowing only one virtual Machine to restricted access by an established outside computer. Allowing network admins to gain access through to this machine which can than access the internal virtual network and all other virtual machines.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
- _TODO: What does Filebeat watch for?
Filebeat watches and monitors the log files or locations that users specify,collects log events, and forwards them 
- _TODO: What does Metricbeat record?
Metric beat records and perodically collect metrics from the operating system and from services running on the server and takes the metrics and statistics and ships them

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.



### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 173.61.49.208

Machines within the network can only be accessed by REdAdmin/jumpbox Container.
- _TODO: Which machine did you allow to access your ELK VM? Container on Jumpbox Cofident Carson What was its IP address?10.0.0.13

A summary of the access policies in place can be found in the table below.
| Name      | Function   | IP Address | Operating System |
|-----------|------------|------------|------------------|
| Jump box  | Gateway    | 10.0.0.13  | Linux            |
| Elk Stack | Monitors   | 10.1.0.4   | linux            |
| Web-1     | Web Server | 10.0.0.14  | Linux            |
| Web-2     | Web Server | 10.0.0.15  | Linux            |
| Web-3     | Web Server | 10.0.0.4   | Linux            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
Ansible can makes maintaining and updating mutiple machines far more managable by simply updating/running on ansible playbook file without having to login in an update each individual machine

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- - Installs the necessary Modules/Tools to  Docker, Python-Pip and Docker python
- - Set ups the system to increase Memory for 
- Pulls the Docker Image specifically containing the ELK enviroment
- Tells the VM what ports ELK well being using to commuicate with
- Enables the Docker Service image containing ELK on the server/VM

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Project-1/Images/Elk Stack Container Screenshot.PNG](Elk Stack Container Screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
 10.0.0.14, 10.0.0.15,10.0.0.4

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
 Filebeat
These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat collects log data like getting inputs from /var/log/apache2/ apache a webserver application. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook.yml file to the ansible container in jumpbox.
- Update the ansible.cfg file to include the Three Webserver IP Addresses 10.0.0.14, 10.0.0.15,10.0.0.4
- Run the playbook, and navigate to http://52.254.67.239:5601/app/kibana or THE IP Address the webservers are severing the application on ?  to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? Filebeat is copied in into the ansible container
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ Update the Ansible.cfg by adding the Elks ip addresss
- _Which URL do you navigate to in order to check that the ELK server is running? http://52.183.31.107:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
