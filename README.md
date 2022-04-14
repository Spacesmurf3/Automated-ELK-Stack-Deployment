## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://github.com/Spacesmurf3/Automated-ELK-Stack-Deployment/blob/a010f083e23ecf57e52e42302b0f00c82b02d2b2/Images/ElkStackNew.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  [Elk_playbook.yml](https://github.com/Spacesmurf3/Automated-ELK-Stack-Deployment/blob/07b4dc2770b35dd7e01f351a3eeec23d85e2f07b/Elk_playbook.yml)

This document contains the following details:
  - Description of the Topology
  - Access Policies
  - ELK Configuration
  - Beats in Use
  - Machines Being Monitored
  - How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available and reliable, in addition to restricting in-bound access to the network. Load balancers protects the system from DDoS attacks by shifting attack traffic. A load balancer intelligently distributes traffic from clients across multiple servers without the clients having to understand how many servers are in use or how they are configured. Because the load balancer sits between the clients and the servers it can enhance the user experience by providing additional security, performance, resilience and simplify scaling your website. 
  
The advantage of a jump box is to give access to the user from a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network. Filebeat watches for any information in the file system that has been changed and when it was changed. Metricbeat takes the metrics and statistics and sends them to the specified output.

The configuration details of each machine may be found below.

| Name       | Function   | IP Address | Operating System |
|------------|------------|------------|------------------|
| Jump Box   | Gateway    | 10.0.0.4   | Linux            |
| Web-1      | Webserver  | 10.0.0.7   | Linux            |
| Web-2      | Webserver  | 10.0.0.8   | Linux            |
| ELK-Server | Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
  - My IP address: 47.221.21.213

Machines within the network can only be accessed by the jump box provisioner. IP address for jump box provisioner is 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 47.***.***.***       |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because its efficient, simple to learn, and playbooks are written in YAML.

The playbook implements the following tasks:
  - Install docker.io
  - Install pip3
  - Install Docker python module
  - Increase virtual memory
  - Download and launch ELK Docker Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/Spacesmurf3/Automated-ELK-Stack-Deployment/blob/04ab7f522c2cbd769a58ba9e4c5b1425d9ff998e/Images/Project1%20ScreenShot%20Docker%20ps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
  - Web-1 10.0.0.7
  - Web-2 10.0.0.8

We have installed the following Beats on these machines:
  - Metricbeat
  - Filebeat

These Beats allow us to collect the following information from each machine:
  - Filebeat - collects data about the file system
  - Metricbeat - collects machine metrics, such as uptime

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
  - Copy the playbook file to Ansible Control Node. Playbooks for Filebeat and Metricbeat are also here: [filebeat](https://github.com/Spacesmurf3/Automated-ELK-Stack-Deployment/blob/8e77c1cff9f8fd0a90f15313dc113aea8fe45b7a/filebeat-playbook.yml) and [metricbeat](https://github.com/Spacesmurf3/Automated-ELK-Stack-Deployment/blob/8e77c1cff9f8fd0a90f15313dc113aea8fe45b7a/metricbeat-playbook.yml)
  - Update the hosts file to include webserver and ELK.
  - Copy of the hosts file is also here: [hosts](https://github.com/Spacesmurf3/Automated-ELK-Stack-Deployment/blob/8e77c1cff9f8fd0a90f15313dc113aea8fe45b7a/Hosts.txt)
  - Run the playbook, and navigate to Kibana (http://[your_elk_server_ip:5601]/app/kibana) to check that the installation worked as expected. If the installation is working as expected you should see:

![Image](https://github.com/Spacesmurf3/Automated-ELK-Stack-Deployment/blob/955d125f173000eb8ed69d548b53c8707601e1d8/Images/Filebeat_VRF_INSTL.PNG)

and

![Image](https://github.com/Spacesmurf3/Automated-ELK-Stack-Deployment/blob/955d125f173000eb8ed69d548b53c8707601e1d8/Images/Metricbeat_VRF_INSTL.PNG)
