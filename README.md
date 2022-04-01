## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Update the path with the name of your diagram](Images/diagram_filename.png)

![image](https://user-images.githubusercontent.com/94412159/160733626-02904990-dd43-4e35-8a6d-b2430c30b904.png)

 
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.
  -filebeat-playbook.yml
  -metricbeat-playbook.yml
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? Load Balancers protect servers from being overloaded with traffic by distributing traffic among different servers.
 What is the advantage of a jump box?_
It serves as a single access point that can be used to control administrative tasks
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Logs and system Traffic.
- What does Filebeat watch for? Log files and Events
- What does Metricbeat record? Records Metrics and Statistical Data
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
Name	Function	IP Address	Operating System
Jump-Box-Provisoner	Gateway	10.0.0.4	Linux
Web-1	VM	10.0.0.5	Linux
Web-2	VM	10.0.0.6	Linux
ELK Server	ELK	10.1.0.5	Linux

### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-
Machines within the network can only be accessed by _____.
- Which machine did you allow to access your ELK VM? What was its IP address? 40.78.12.36 
A summary of the access policies in place can be found in the table below.
Name	Publicly Accessible	Allowed IPs
Jump-Box-Provisioner	Yes	40.78.12.36
Web-1	No	10.0.0.4
Web-2	No	10.0.0.4
ELK-Server	No	10.0.0.4
|
### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_
Servers can be deployed virtual which make the process quick and simple
The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Installs Docker io
- Installs pip3
- Installs Python
- Downloads and Configures ELK container
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
!(Images/docker_ps_output.png)
![image](https://user-images.githubusercontent.com/94412159/160733742-5e0f510d-9199-4694-9ae4-5c6fdd9d383e.png)

 
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
- Web-1 10.0.0.5
- Web-2 10.0.0.6
We have installed the following Beats on these machines:
- Specify which Beats you successfully installed_
- Filebeat
- Metricbeat
These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, 
and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat collects data of Log files and Log Events (ex: Elasticsearh)
Metricbeat collects statistical Data (ex:lightweight shipper for metrics)
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the playbook file to ansible.
- Update the configuration file to include the Private IP and Elk server files
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
_ Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
Playbooks are the .yml files. 
- elk-playbook
- filebeat-playbook
-metricbeat-playbook
They are copied to the ansible files container
- _Which file do you update to make Ansible run the playbook on a specific machine? 
Hosts Configuration file 
How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
Within the Hosts file
- _Which URL do you navigate to in order to check that the ELK server is running? http://10.1.0.5:5601 (elk server IP)
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

1.	ssh public ip
2.	sudo docker list -a
3.	sudo docker start "container name"
4.	sudo docker attach "container name"
5.	cd /etc/ansible
6.	ansible-playbook "elk playbook name".yml 
7.	cd /etc/ansible/
8.	ansible-playbook "beats-playbook name".yml 

