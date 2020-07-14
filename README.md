## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

  ![image](https://github.com/angel329623/Project1/blob/master/Images/diagram.JPG)
  
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook files may be used to install only certain pieces of it, such as Filebeat.

  ![Filebeat Playbook](https://github.com/angel329623/Project1/blob/master/filebeat-playbook.yml)

  ![Metricbeat Playbook](https://github.com/angel329623/Project1/blob/master/metricbeat-playbook.yml)

This documents contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure from distributed denial-of-service (DDoS) attacks by switching traffic from a private server to a public cloud, in addition to restricting unauthorized access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web01    | Server   | 10.0.0.6   | Linux            |
| web02    | Server   | 10.0.0.7   | Linux            |
| ELK-SER  | Server   | 10.1.0.4   | Linux            |


### Access Policies
The machines on the internal network are not exposed to the public Internet. 

Only the Elk Server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

-10.0.0.4

Machines within the network can only be accessed by using the Jump Box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.4             |
| web01    | No                  | 10.0.0.6             |
| web02    | No                  | 10.0.0.7             |
| Elk-SER  | No                  | 10.1.0.4             |


### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows administrators to automate daily tasks and allows IT personel to focus on more important projects.

The playbook implements the following tasks:
- Crate an Azure account with in the same resource group.
- Download images that install Docker and configures to ELK container.
- Run both playbooks 
- Modify ELK server and restrict access.
 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

  ![image](https://github.com/angel329623/Project1/blob/master/Images/docker_ps.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat, collects file system log data. Monitors log files, specific log events and forwards all logs to ELK.
- Metricbeat, Collects machine metrics from the OS. Statistics are gather to any specified output and forwards data to ELK.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy both the Filebeat Playbook and Metricbeat Playbook files to ansible machine.
- Update the hosts file to include specific private IP adresses for each machine that ELK is desired.
- Run the playbook, and navigate http://ELKserverpublicIP:5601/app/kibana to to check that the installation worked as expected.

_Commands_

```
docker ps

nano /etc/ansible/hosts/

curl https://github.com/angel329623/Project1/blob/master/filebeat-playbook.yml > your/path/filebeat-config.yml

curl https://github.com/angel329623/Project1/blob/master/metricbeat-playbook.yml > your/path/metricbeat-config.yml

```
