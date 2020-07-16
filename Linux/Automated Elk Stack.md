## Automated ELK Stack Deployment

https://docs.google.com/document/d/1in7w8S2agPMOMxw2-w7An5bz8xXp19773atkbRlqv4Y/edit?usp=sharing 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeatinstall.yml and metricbeatinstall.yml file may be used to install specific beats such as Filebeat or Metricbeat. 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system metrics and system logs.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|---------------|-------------|--------------|--------------------------|
| Jump Box | Jumpbox |10.0.0.4   | Linux                      |
| Web - 01   | VM         | 10.0.0.5  | Linux                      |
| Web - 02   | VM         | 10.0.0.6  | Linux                      |
| Web - 03   | VM         | 10.0.0.6  | Linux                      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
73.63.21.224

Machines within the network can only be accessed by Jumpbox 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|---------------|----------------------|----------------------------------|
| Jump Box | No                     |   Public Home IP                |
| Web - 01   | No                     |  10.0.0.4                         |
| Web - 02   | No                     |  10.0.0.4                         |
| Web - 03   | No                        | 10.0.0.4                          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for easy automation across multiple machines within networks. 
The playbook implements the following tasks:
Installing docker.io
Installing python 3 pip
Download and launch a docker web container 
Enable docker services 


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://docs.google.com/document/d/1yAOQf32CXy_RMaH_WZiFR3ggjLGpZW55HidyhWXismI/edit

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.8

We have installed the following Beats on these machines:
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the beat configuration file file to files directory.
- Update the hosts file to include the additional ip address
- Run the playbook, and navigate to http://40.65.224.227:5601/app/kibana#/home?_g=()  to check that the installation worked as expected.





