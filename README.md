ElkProject1
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Diagrams/Adam_Dooley_Diagram_1.pdf file may be used to install only certain pieces of it, such as Filebeat.

  - Ansible/YML_Scripts.txt
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system metrics.


The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| Web - 1  | Container | 10.0.0.6   | Linux            |
| Web - 2  | Container | 10.0.0.7   | Linux            |
| Elk-VM   | Container | 10.1.0.4.  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 4.1.85.138


Machines within the network can only be accessed by Jumpbox VM 52.173.135.34.


A summary of the access policies in place can be found in the table below.

| Name         | Publicly Accessible | Allowed IP Addresses   |
|--------------|---------------------|------------------------|
| Jump Box     | No/SSH (22)         | 4.1.85.138             |
| Load Balancer| Yes                 | 4.1.85.138             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it significantly simplifies the process.

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install Docker python module

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
- Images/Docker_ps

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web - 1: Internal IP 10.0.0.6
- Web - 2: Internal IP 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat
These Beats allow us to collect the following information from each machine:
- Filebeat is responsible for collecting log data which could be something like logs from security tools a network has in place.
- Metricbeat is responsible for collecting metric data such as looking at what the current state of your ram is.

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to /etc/ansible.
- Update the hosts file to include the container IP
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it? /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? /etc/ansible/Hosts and put the ELK IP under its own host group and not in the web servers group.
- _Which URL do you navigate to in order to check that the ELK server is running? 52.160.90.0:5601/app/kibana

- ansible - playbook YAML file
