## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://user-images.githubusercontent.com/86903011/155901384-499a6bdb-d9cc-42a9-a437-4fa56a4875cb.png)

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

Load balancing ensures that the application will be highly available and reliable, in addition to restricting in-bound access to the network.
  -What aspect of security do load balancers protect?
    *Load balancers protects the system from DDoS attacks by shifting      attack traffic.  
  -What is the advantage of a jump box?
    *The advantage of a jump box is to give access to the user from a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
  -What does Filebeat watch for?
    *Filebeat watches for any information in the file system that has      been changed and when it was changed.
  -What does Metricbeat record?
    *Metricbeat takes the metrics and statistics and sends them to the specified output.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

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
| Jump Box | Yes                 | 47.221.21.213        |
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
- Copy the Elk_playbook.yml file to Ansible Control Node.
- Update the hosts file to include webserver and ELK.
- Run the playbook, and navigate to Kibana (http://[Host IP:5601]/app/kibana) to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ 
