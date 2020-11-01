## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Images/Project1_Diagram_Adam_Brounstein.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable and efficient, in addition to restricting traffic to the network.
- Load balancers protect application servers. The advantage of a Jumpbox is to access and manage devices in a separate security zone.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat collects data about the file system.
- Metricbeat collects machine metrics such as up time and memory.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.5   | Linux            |
| Web1     | Gateway  | 10.0.0.4   | Linux            |
| Web2     | Gateway  | 10.0.0.7   | Linux            |
| ELK      | Gateway  | 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- I whitelisted my public IP 76.115.2.89

Machines within the network can only be accessed by SSH.
- We allowed the Jumpbox to access the ELK VM from the IP 10.0.0.5

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |   Yes               | 76.115.2.89          |
|   ELK    |   No                |    10.2.0.4          |
|   Web1   |   No                |    10.0.0.4          |
|   Web2   |   No                |    10.0.0.7          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- it allows you to make difficult tasks repeatable and easily executable. Basically it's a time saver.

The playbook implements the following tasks:
- Configure the web VM with docker
- Docker.io
- Install pip3
- Install a python docker module
- Use more memory
- Install docker container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

! Screen shot of install-elk.yml running (Desktop/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4
- 10.0.0.7
- 10.0.0.9

We have installed the following Beats on these machines:
- We installed Filebeat Packetbeat and Metricbeat.

These Beats allow us to collect the following information from each machine:
- Filebeat collects log data and forwards the data to Elasticsearch or Logstash for indexing. 
Packetbeat is used to track activity on the network by collecting packets that pass through the NIC.
Metricbeat collects system metrics such as CPU usage and memory statistics. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbooks file to the Ansible Control Node.
- Update the annsible file to include the playbook.
- Run the playbook, and navigate to container to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
