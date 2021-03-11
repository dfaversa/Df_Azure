## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
[cloud security HW 12 (1).pdf](https://github.com/dfaversa/Df_Azure/files/6119605/cloud.security.HW.12.1.pdf)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml_____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._             																root@4d2c8d5a2466:~# /etc/ansible/roles/filebeat-playbook.y								 					root@4d2c8d5a2466:~# /etc/ansible/roles/elk-playbook 															root@4d2c8d5a2466:~# /etc/ansible/roles/metricbeat-playbook.yml
	


This document contains the following details:
- Description of the Topologu
-Access policies 

- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _responsive____, in addition to restricting __traffic___ to the network.
- _TODO: What aspect of security do load balancers protect? defends an organization against distributed denial-of-service (DDoS) attacks. It does this by shifting attack traffic from the corporate server to a public cloud provider. What is the advantage of a jump box?_ jump box is a system on a network used to access and manage devices in a separate security zone. A jump server is a hardened and monitored device that spans two dissimilar security zones and provides a controlled means of access between them. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- _TODO: What does Filebeat watch for?_ Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- _TODO: What does Metricbeat record?_ takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway | 10.0.0.1  | Linux            
| Web 1    |  server | 10.0.0.8  | Linux                 
| Web 2    |  server | 10.0.0.9  | Linux                 
| Web 3    |  server | 10.0.0.10 | Linux                 
  Elk-VM   |  server | 10.1.0.4  | Linux  
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_76.98.103.19

Machines within the network can only be accessed by SSH.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_JumpBox IP 40.76.223.47

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses 
|----------|---------------------|----------------------
| Jump Box |  Yes                | 10.0.0.4    |
| Web 1    |  No                 | 10.0.0.8    |                      
| Web 2    |  No                 | 10.0.0.9    |                                                                            | Web 3    |  No                 | 10.0.0.10   | 			
No### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ The playbook implements the following tasks:
•	In 3-5 bullets, explain the steps of the ELK installation
•	... Create ELK VM in Azure
•	... SSH to Jump Box
•	... Attach Ansible
•	... SSH to ELK VM and run playbooks
•	The following screenshot displays the result of running (docker ps) after successfully configuring the ELK instance.



The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.						 

[cloud security HW 12 (1).pdf](https://github.com/dfaversa/Df_Azure/files/6119588/cloud.security.HW.12.1.pdf)
![project azure 1 pic](https://user-images.githubusercontent.com/73912396/110716798-d5ce0d00-81d5-11eb-848d-6b581b5761bc.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:		10.0.0.4											10.0.0.8											10.0.0.9											10.0.0.10

We have installed the following Beats on these machines:
 Filebeat was successfully installed
 Metricbeat was successfully installed


These Beats allow us to collect the following information from each machine:
Filebeat is used to collect log files from specific files on remote machines. An example would be MS Azure and MySQL databases.
the system Metricbeat collects machine metrics. It is a measurrement to analyze how healthy is

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat file to /etc/ansible/roles/files.
- Update the _filebeat-config.yml file to include the elk private IP in lines 1106 and 1806
- Run the playbook, and navigate to HTTP://20.36.137.243:5601/app/kabana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_filebeat-playbook.yml  								       	Which file do you update to make Ansible run the playbook on a specific machine? Metricbeat-config.yml to include ELK on private IP on lines 62 and 96										  How do I specify which machine to install the ELK server on versus which to install Filebeat on? In the etc/ansible/hosts file two groups must be specified. One group is  the webservers which have the IPs of the VMs, and the other group are the elkservers.
- _Which URL do you navigate to in order to check that the ELK server is running? http://20.36.137.243:5601/app/kabana																																																						As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
													To create the filebeat-config.yml file: nano filebeat-config.yml..
I created the playbook: nano filebeat-playbook.yml
![launching filebeat](https://user-images.githubusercontent.com/73912396/110720182-23e60f00-81dc-11eb-8fa3-277a50521ef0.png)
																						 To run the playbook: ansible-playbook filebeat-playbook.yml
In order to run the playbook, you have to be in the directory. Or navigate into the path (ansible-playbook /etc/ansible/roles/filebeat-playbook) To create the metricbeat-config.yml file: nano metricbeat-config.yml.
I created the playbook: nano metricbeat-playbook.yml
 ![launching metricbeat](https://user-images.githubusercontent.com/73912396/110720215-3102fe00-81dc-11eb-9ef3-734ac0ce4712.png)

________________________________________
 Run the playbook: ansible-playbook metricbeat-playbook.yml
In order to run this playbook, you must be in the directory where the playbook is, or use the path (ansible-playbook /etc/ansible/roles/metricbeat-playbook.yml)

