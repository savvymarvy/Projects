## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Azure network diagram.png (https://github.com/savvymarvy/Projects/blob/main/Azure%20network%20diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as File beat.

Enter the playbook file. Filebat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _reliable and available____, in addition to restricting _traffic overload___ to the network.
- _TODO: What aspect of security do load balancers protect?  Load balancers help to protect a system from Ddos attacks and ensures the availability of the network by distributing traffic to various servers across the network. What is the advantage of a jump box?_Jumpbox helps to give access to a user through a single node that enables easy monitoring and security of the network

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _data____ and system logs_____.
- _TODO: What does Filebeat watch for?_Filebeat watches for log files.
- _TODO: What does Metricbeat record?_Metricbeat records the metrics and statistics that it collects.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| Web-1    |  web server        |    10.1.0.5        |       Linux           |
| Web-2     |   web server       |    10.1.0.6	        |    Linux              |
| ELK VM     |  elk server        |     10.2.0.4       |       Linux               |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the elk server_____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 172.64.172.204

Machines within the network can only be accessed by _my computer and jumpbox____.
- _TODO: Which machine did you allow to access your ELK VM? My jumpbox What was its IP address?_ 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes             | Computer IP @ home    |
|    Web 1  and 2    |       No              |     10.1.0.4                 |
|   Elk server       |         No         | Computer through tcp 5601                     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
The main advantage of automating configuration through ansible is that you can input commands into multiple servers from a single playbook.
The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...install: docker.io
Install: python-pip
- ...install: docker
Command :sysctl -w vm.max_map_count = ‘262144’
Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
 
![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web 1 and Web 2 VMs
- _TODO: List the IP addresses of the machines you are monitoring_
10.1.05 and 10.1.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ Filebeat and metricbeat

These Beats allow us to collect the following information from each machine:
.
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
File beat allows log information while metric beat allows metric and system statistics

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _ansible configuration____ file to _ansible container in the etc folder____.
- Update the __host__ file to include...webservers and elk servers
- Run the playbook, and navigate to ansible-playbook____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Pentest.yml and elk-to-red.yml Where do you copy it?_in the etc folder
- _Which file do you update to make Ansible run the playbook on a specific machine? Host file How do I specify which machine to install the ELK server on versus which to install Filebeat on?_Add ip address for web servers and elk servers
- _Which URL do you navigate to in order to check that the ELK server is running? www.173.64.173.204:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

