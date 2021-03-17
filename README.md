# Examples-of-my-work
Collection of work that I have completed through Arizona State University Cyber Security Boot Camp
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/Elk Stack Diagram.png)

![Elk Stack Diagram](https://user-images.githubusercontent.com/80176135/111418409-e9c9b100-86a4-11eb-9a42-792583f7fcb4.PNG)




These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.

Elk.yml


![Elk yml 1](https://user-images.githubusercontent.com/80176135/111422037-44fea200-86ab-11eb-8d52-4989944b69e9.PNG)
![Elk yml 2](https://user-images.githubusercontent.com/80176135/111422055-4c25b000-86ab-11eb-8f48-954f8abc5e3f.PNG)




This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
 - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available and reliable, in addition to restricting access to the network.
The aspect of security that load balancers protect are against ddos attacks by shifting the attack traffic. 
The advantage of a jumpbox is that it gives access to a specific user or users from a single node that
can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
- _Filebeat  watches for when and what information in the file system have changed. 
- _Metricbeat is the collector of metrics and statistics that can send to an output of your choosing.

The configuration details of each machine may be found below.


| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
|Jump Box  | Gateway    | 10.0.0.4   | Linux            |
| Web 1    | Web Server | 10.0.0.5   | Linux            |
| Web 2    | Web Server | 10.0.0.6   | Linux            |
| Elk      | Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My IP address : 24.255.7.188

Machines within the network can only be accessed by the jump box provisioner.
- the jump box provisioner IP of 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 24.255.7.188         |
| Web 1    | No                  | 10.0.0.4             |
| Web 2    | No                  | 10.0.0.4             | 
| Elk      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?

The advantage of automating configuration with Ansible is that you can input commands from a single playbook into various different servers.

The playbook implements the following tasks:
- Install docker.io
- Install pip3
- install Docker python module
- use sysctl module to use more memory
- download and launch a docker elk container and enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/ELK docker screenshot.png)

![ELK docker screenshot](https://user-images.githubusercontent.com/80176135/111418483-07971600-86a5-11eb-948b-ed427591e5c1.PNG)



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: 10.0.0.4 and  10.0.0.5 Web 1 and Web 2

We have installed the following Beats on these machines:
- _Filebeat

These Beats allow us to collect the following information from each machine:
- _Filebeat allows us to collect information on log data such as syslog hostnames and processes, what each hostname does.

![Filebeatlogs](https://user-images.githubusercontent.com/80176135/111418557-21385d80-86a5-11eb-84b7-5accbb1ed7e3.PNG)

Metricbeat allows for us to collect information on the dockers running and dockers stopped.

![Metricbeatdata](https://user-images.githubusercontent.com/80176135/111418575-2ac1c580-86a5-11eb-92f9-881b0f43b4fd.PNG)


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to the ansible control node.
- Update the hosts file to include webservers and elk.
- Run the playbook, and navigate to kibana site of http://40.121.164.218:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _filebeat.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
You would need to update the ansible hosts file to configure the groups and playbook files and to specify which machine to install elk and install filebeat once you add the groups in the
playbook instructions you would specify which machine to install each based on the groups you stated in hosts file.
- _Which URL do you navigate to in order to check that the ELK server is running?
http://40.121.164.218:5601/app/kibana#/home
