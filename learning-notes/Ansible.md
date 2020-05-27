# Learning Notes - Configuration Management & ANSIBLE

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)
---


## What is Ansible?

**Ansible**  is an automation and orchestration tool popular for its simplicity of installation, ease of use in what concerns the connectivity to clients, its lack of agent for ansible clients and the multitude of skills.

Ansible functions by connecting via SSH to the clients, so it doesn't need a special agent on the client-side, and by pushing modules to the clients. The modules are then executed locally, on the client-side, and the output is pushed back to the Ansible server.

Since it uses SSH, it can very easily connect to clients using SSH-Keys, simplifying though the whole process. Client details, like hostnames or IP addresses and SSH ports, are stored in files called inventory files. Once you have created an inventory file and populated it, ansible can use it.

## Why use Ansible?

Here are some important pros/benefits of using Ansible

-   One of the most significant advantages of Ansible is that it is free to use by everyone.
-   It does not need any special system administrator skills to install and use Ansible, and the official documentation is very comprehensive.
-   Its modularity regarding plugins, modules, inventories, and playbooks make Ansible the perfect companion to orchestrate large environments.
-   Ansible is very lightweight and consistent, and no constraints regarding the operating system or underlying hardware are present.
-   It is also very secure due to its agentless capabilities and due to the use of OpenSSH security features.
-   Another advantage that encourages the adoption of Ansible is its smooth learning curve determined by the comprehensive documentation and easy to learn structure and configuration.

## History of Ansible

Here, are important land marks from the history of ansible:

-   In February 2012 the Ansible project began. It was first developed by Michael DeHaan, the creator of Cobbler and Func, Fedora Unified Network Controller.
-   Initially called AnsibleWorks Inc, the company funding the ansible tool was acquired in 2015 by RedHat and later on, along with RedHat, moved under the umbrella of IBM.
-   In the present, Ansible comes included in distributions like Fedora Linux, RHEL, Centos and Oracle Linux.

## Important terms used in Ansible

-   ### Ansible server:

    The machine where Ansible is installed and from which all tasks and playbooks will be ran
-   ### Module:

    Basically, a module is a command or set of similar commands meant to be executed on the client-side
-   ### Task:

    A task is a section that consists of a single procedure to be completed
-   ### Role:

    A way of organizing tasks and related files to be later called in a playbook
-   ### Fact:

    Information fetched from the client system from the global variables with the gather-facts operation
-   ### Inventory:

    File containing data about the ansible client servers. Defined in later examples as hosts file
-   ### Play:

    Execution of a playbook
-   ### Handler:

    Task which is called only if a notifier is present
-   ### Notifier:

    Section attributed to a task which calls a handler if the output is changed
-   ### Tag:

    Name set to a task which can be used later on to issue just that specific task or group of tasks.

## Ansible Installation in Linux

Once you have compared and weighed your options and decided to go for Ansible, the next step is to have it installed on your system. We will go through the steps of installation in different Linux distributions.

### Install Ansible on Centos/RedHat systems

**Step 1)**  Install EPEL repo
```
[ubuntu@ansible-server ~]# sudo yum install epel-release
```
**Step 2)** Install ansible package
```
[ubuntu@ansible-server ~]# sudo  yum install -y ansible
```
[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto1.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto1.png)

### Install ansible on Ubuntu/Debian systems

**Step 1)**  Perform an update to the packages
```
$ sudo apt update
```
**Step 2)**  Install the software-properties-common package
```
$ sudo apt install software-properties-common
```
**Step 3)**  Install ansible personal package archive
```
$ sudo apt-add-repository ppa:ansible/ansible
```
**Step 4)**  Install ansible
```
$ sudo apt update
$ sudo apt install ansible
```

## Ansible ad-hoc commands

One of the simplest ways Ansible can be used is by using ad-hoc commands. These can be used when you want to issue some commands on a server or a bunch of servers. Ad-hoc commands are not stored for future uses but represent a fast way to interact with the desired servers.

For this tutorial, a simple two servers hosts file will be configured, containing host1 and host2.

You can make sure that the hosts are accessible from the ansible server by issuing a ping command on all hosts.

```
[ubuntu@ansible-server test_ansible]# ansible -i hosts all -m ping
```

```

host1 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
host2 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}

```

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto2.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto2.png)

Explanation:

1.  Status of the command, in this case, SUCCESS
2.  Host on which the command ran
3.  The command issued via the -m parameter, in this case, ping
4.  With the -i parameter, you can point to the hosts file.

You can issue the same command only on a specific host if needed.

```
[ubuntu@ansible-server test_ansible]# ansible -i hosts all -m ping --limit host2
```

```

host2 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}


```
[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto3.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto3.png)

Explanation:

1.  –Limit parameter can be used to issue commands only on specific hosts in the host's file
2.  Name of the host as defined in the inventory file

If you need to copy a file to multiple destinations rapidly, you can use the copy module in ansible which uses SCP. So the command and its output look like below:

```
[ubuntu@ansible-server test_ansible]# ansible -i hosts all -m copy -u ubuntu --become-user=root -a "src=/home/ubuntu/testfile dest=/tmp/testfile"
```

```
host1 | SUCCESS => {
    "changed": true,
    "checksum": "da39a3ee5e6b4b0d3255bfef95601890afd80709",
    "dest": "/tmp/testfile",
    "gid": 0,
    "group": "root",
    "md5sum": "d41d8cd98f00b204e9800998ecf8427e",
    "mode": "0644",
    "owner": "root",
    "size": 0,
    "src": "/home/ubuntu/.ansible/tmp/ansible-tmp-1562216392.43-256741011164877/source",
    "state": "file",
    "uid": 0
}
host2 | SUCCESS => {
    "changed": true,
    "checksum": "da39a3ee5e6b4b0d3255bfef95601890afd80709",
    "dest": "/tmp/testfile",
    "gid": 0,
    "group": "root",
    "md5sum": "d41d8cd98f00b204e9800998ecf8427e",
    "mode": "0644",
    "owner": "root",
    "size": 0,
    "src": "/home/ubuntu/.ansible/tmp/ansible-tmp-1562216392.6-280302911361278/source",
    "state": "file",
    "uid": 0
}
```


[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto4.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto4.png)

Explanation:

1.  Copy module defined
2.  Module arguments, in this case, are source absolute path and destination absolute path.
3.  Ansible command output reflecting the success of the copy command and other details like the sha1 or md5 checksums for file integrity check and metadata like owner, size, or permissions.


## Example Adhoc Commands in Ansible

```
ansible all -i inventory-file -l inventory-group -m shell -u username --become-user=root -b -a 'date; apt-get install ntp -y ; service ntp stop ; sudo ntpd -gq ; service ntp start; date'
```

```
ansible all -i inventory-file -l inventory-group -m copy -u admin --become-user=root -b -a 'src=/etc/httpd/conf/httpd.conf dest=/tmp/httpd.conf.backup'
```

```
ansible all -i inventory-file -l inventory-group -m shell -u username --become-user=root -b -a 'ls -ltr'
```


## Installing Netdata Using Adhoc commands

```
curl -Ss https://raw.githubusercontent.com/BINPIPE/shell-scripts/master/install_netdata.sh > /tmp/install_netdata.sh ; chmod +x /tmp/install_netdata.sh

ansible all -i hosts -l all -m script -u ubuntu --become-user=root -b -a '/tmp/install_netdata.sh'

```



    It is effortless to have a package installed on a bunch of servers. Ansible has several modules that interact with used installers, like yum, apt, dnf, etc.

In the next example, you will find out how to install a package via the apt module on two CentOS hosts.

```
[centos@ansible-server]# ansible -i hosts all -m yum -u centos --become-user=root -a 'name=ncdu state=present'
```

```
host1 | SUCCESS => {
    "changed": true,
    "msg": "",
    "rc": 0,
    "results": [


"Loaded plugins: fastestmirror\nLoading mirror speeds from cached hostfile\n * base: mirror.netsite.dk\n * elrepo: mirrors.xservers.ro\n * epel: fedora.mirrors.telekom.ro\n * extras: centos.mirrors.telekom.ro\n * remi-php70: remi.schlundtech.de\n * remi-safe: remi.schlundtech.de\n * updates: centos.mirror.iphh.net\nResolving Dependencies\n--> Running transaction check\n---> Package ncdu.x86_64 0:1.14-1.el7 will be installed\n--> Finished Dependency Resolution\n\nDependencies Resolved\n\n================================================================================\n Package         Arch              Version                Repository       Size\n================================================================================\nInstalling:\n ncdu            x86_64            1.14-1.el7             epel             51 k\n\nTransaction Summary\n================================================================================\nInstall  1 Package\n\nTotal download size: 51 k\nInstalled size: 87 k\nDownloading packages:\nRunning transaction check\nRunning transaction test\nTransaction test succeeded\nRunning transaction\n  Installing : ncdu-1.14-1.el7.x86_64                                       1/1 \n  Verifying  : ncdu-1.14-1.el7.x86_64                                       1/1 \n\nInstalled:\n  ncdu.x86_64 0:1.14-1.el7                                                      \n\nComplete!\n"
    ]
}

host2 | SUCCESS => {
    "changed": true,
    "msg": "",
    "rc": 0,
    "results": [
        "Loaded plugins: fastestmirror\nLoading mirror speeds from cached hostfile\n * base: mirror.netsite.dk\n * elrepo: mirrors.leadhosts.com\n * epel: mirrors.nav.ro\n * extras: centos.mirrors.telekom.ro\n * remi-php70: mirrors.uni-ruse.bg\n * remi-safe: mirrors.uni-ruse.bg\n * updates: centos.mirror.iphh.net\nResolving Dependencies\n--> Running transaction check\n---> Package ncdu.x86_64 0:1.14-1.el7 will be installed\n--> Finished Dependency Resolution\n\nDependencies Resolved\n\n================================================================================\n Package         Arch              Version                Repository       Size\n================================================================================\nInstalling:\n ncdu            x86_64            1.14-1.el7             epel             51 k\n\nTransaction Summary\n================================================================================\nInstall  1 Package\n\nTotal download size: 51 k\nInstalled size: 87 k\nDownloading packages:\nRunning transaction check\nRunning transaction test\nTransaction test succeeded\nRunning transaction\n  Installing : ncdu-1.14-1.el7.x86_64                                       1/1 \n  Verifying  : ncdu-1.14-1.el7.x86_64                                       1/1 \n\nInstalled:\n  ncdu.x86_64 0:1.14-1.el7                                                      \n\nComplete!\n"
    ]
}
```


[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto5.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto5.png)

Explanation:

1.  yum module is used in this example
2.  - It defines the module arguments, and in this case, you will choose the name of the package and its state. If the state is absent, for example, the package will be searched and if found, removed
3.  When colored in yellow, you will see the output of the ansible command with the state changed, meaning in this case, that the package was found and installed.
4.  Status of the yum install command issued via ansible. In this case the package ncdu.x86_64 0:1.14-1.el7 was installed.

Of course, all of the yum installer options can be used via ansible, including update, install, latest version, or remove.

In the below example the same command was issued to remove the previously installed ncdu package.

```
[centos@ansible-server]# ansible -i hosts all -m yum -a 'name=ncdu state=absent'
```

```

host1 | SUCCESS => {
    "changed": true,
    "msg": "",
    "rc": 0,
    "results": [
        "Loaded plugins: fastestmirror\nResolving Dependencies\n--> Running transaction check\n---> Package ncdu.x86_64 0:1.14-1.el7 will be erased\n--> Finished Dependency Resolution\n\nDependencies Resolved\n\n================================================================================\n Package         Arch              Version               Repository        Size\n================================================================================\nRemoving:\n ncdu            x86_64            1.14-1.el7            @epel             87 k\n\nTransaction Summary\n================================================================================\nRemove  1 Package\n\nInstalled size: 87 k\nDownloading packages:\nRunning transaction check\nRunning transaction test\nTransaction test succeeded\nRunning transaction\n  Erasing    : ncdu-1.14-1.el7.x86_64                                       1/1 \n  Verifying  : ncdu-1.14-1.el7.x86_64                                       1/1 \n\nRemoved:\n  ncdu.x86_64 0:1.14-1.el7                                                      \n\nComplete!\n"
    ]
}
host2 | SUCCESS => {
    "changed": true,
    "msg": "",
    "rc": 0,
    "results": [
        "Loaded plugins: fastestmirror\nResolving Dependencies\n--> Running transaction check\n---> Package ncdu.x86_64 0:1.14-1.el7 will be erased\n--> Finished Dependency Resolution\n\nDependencies Resolved\n\n================================================================================\n Package         Arch              Version               Repository        Size\n================================================================================\nRemoving:\n ncdu            x86_64            1.14-1.el7            @epel             87 k\n\nTransaction Summary\n================================================================================\nRemove  1 Package\n\nInstalled size: 87 k\nDownloading packages:\nRunning transaction check\nRunning transaction test\nTransaction test succeeded\nRunning transaction\n  Erasing    : ncdu-1.14-1.el7.x86_64                                       1/1 \n  Verifying  : ncdu-1.14-1.el7.x86_64                                       1/1 \n\nRemoved:\n  ncdu.x86_64 0:1.14-1.el7                                                      \n\nComplete!\n"
    ]
}

```

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto6.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto6.png)

Explanation:

1.  The output of the yum command shows that the package was removed.

Another useful and essential feature that ansible uses to interact with the client's server is to gather some facts about the system. So, it fetches hardware, software, and versioning information from the system and stores each value in a variable that can be later on used.

If you need detailed information about the systems to be modified via ansible, the next command can be used. The setup module gathers facts from the system variables.

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto7.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto7.png)

## Ansible Playbooks

In comparison with ad-hoc commands, playbooks are used in complex scenarios, and they offer increased flexibility. Playbooks use YAML format, so there is not much syntax needed, but indentation must be respected. Ansible playbooks tend to be more of a configuration language than a programming language.

Like the name is saying, a playbook is a collection of plays. Through a playbook, you can designate specific roles to some of the hosts and other roles to other hosts. By doing so, you can orchestrate multiple servers in very diverse scenarios, all in one playbook.

To have all the details precise before continuing with examples, we must first define a task. These are the interface to ansible modules for roles and playbooks.

One playbook with one play, containing multiple tasks looks like this.


```
---

- hosts: group1
  tasks:
  - name: Install lldpad package
    yum:
      name: lldpad
      state: latest
  - name: check lldpad service status
    service:
      name: lldpad
      state: started

```

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto8.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto8.png)

In the above example, the group1 of hosts in the host's file is targeted for lldpad package installation using the yum module and afterward the service lldpad created after the installation is then started using the service module used mostly to interact with systemd ensemble.

Explanation:

1.  Group of hosts on which the playbook will run
2.  Yum module is used in this task for lldpad installation
3.  The service module is used to check if the service is up and running after installation

Each ansible playbook works with an inventory file. The inventory file contains a list of servers divided into groups for better control for details like IP address and SSH port for each host.

The inventory file you can use for this example looks like below. There are two groups, named group1 and group2 each containing host1 and host2 respectively.
```
[group1]
host1 ansible_host=192.168.100.2 ansible_ssh_port=22
[group2]
host2 ansible_host=192.168.100.3 ansible_ssh_port=22
```
[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto9.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto9.png)

Explanation:

1.  Group name
2.  Hostname, with IP address and ssh port, in this case, the default one, 22.

Another useful example of an Ansible playbook containing this time two plays for two hosts is the next one. For the first group of hosts, group1, selinux will be enabled. If it is enabled, then a message will appear on the screen of the host.

For the second group of hosts, httpd package will be installed only if the ansible_os_family is RedHat and ansible_system_vendor is HP.

Ansible_os_family and ansible_system_vendor are variables gathered with gather_facts option and can be used like in this conditional example.


```
---

- hosts: group1
  tasks:
  - name: Enable SELinux
    selinux:
      state: enabled
    when: ansible_os_family == 'Debian'
    register: enable_selinux

  - debug:
      Imsg: "Selinux Enabled. Please restart the server to apply changes."
    when: enable_selinux.changed == true

- hosts: group2
  tasks:
  - name: Install apache
    yum:
      name: httpd
      state: present
    when: ansible_system_vendor == 'HP' and ansible_os_family == 'RedHat'
```


[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto10.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto10.png)

Explanation:

1.  Example of the when clause, In this case, when OS type is Debian. The ansible_os_family variable is gathered via gather_facts functionality.
2.  The task output is registered for future use, with its name enable_selinux
3.  Another example of the when clause. In this case, a message will be displayed for the host user if the SELinux was indeed enabled before.
4.  Another example of the when clause consisting of two rules

Besides tasks, there are also some particular tasks called handlers. Handlers must have a unique name throughout the playbook. These work in the same way as a regular task but a handler can be notified via a notifier.

If a handler is not notified during the run of the playbook, it will not run. However, if more than one task notifies a handler, this will run only once after all the tasks are finished.

In the example shown below, you can see how a specific task has a notify section which calls upon another task. If the output of the first task is changed, then a handler task will be called. The best example is to have a configuration file changed and afterward restart that specific service.



```
---

- hosts: group2
  tasks:
  - name: sshd config file modify port
    lineinfile:
     path: /etc/ssh/sshd_config
     regexp: 'Port 28675'
     line: '#Port 22'
    notify:
       - restart sshd
handlers
    - name: restart sshd
      service: sshd
        name: sshd
        state: restarted

```

In this case, if the first task, "sshd config file modify port" is changed, meaning that if the port is not 28675 in the first place, then it will be modified and the task will notify the handler with the same name to run, and it will restart the sshd service.

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto11.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto11.png)

Explanation:

1.  Example of a notifier
2.  Example of a handler

## Ansible Roles

When dealing with extensive playbooks, it is easier to split the tasks into roles. This also helps in reusing the roles in the future. Roles are a collection of tasks, which can be moved from one playbook to another, can be run independently but only through a playbook file.

Roles are stored in separate directories and have a particular directory structure.
```
[ubuntu@ansible-server test2]# tree
.
`-- role1
    |-- defaults
    |   `-- main.yml
    |-- handlers
    |   `-- main.yml
    |-- meta
    |   `-- main.yml
    |-- README.md
    |-- tasks
    |   `-- main.yml
    |-- tests
    |   |-- inventory
    |   `-- test.yml
    `-- vars
        `-- main.yml

7 directories, 8 files
```


The yaml file in the defaults directory contains a list of default variables that are to be used along with the playbook. The handlers directory is used to store handlers. The meta-directory is supposed to have information about the author and role dependencies. In the tasks directory, there is the main yaml file for the role.

The tests directory contains a sample yaml playbook file and a sample inventory file and is mostly used for testing purposes before creating the actual role.

The vars directory contains the yaml file in which all the variables used by the role will be defined. The directory templates and the directory files should contain files and templates that will be used by the tasks in the role.

To create the directory tree for a role, you should use the following command with the last parameter, the role name:

```
[ubuntu@ansible-server test2]# ansible-galaxy init role1
```

Ansible also works well with templates. As a language for templating, it uses Jinja2.

In the next example, you will find out how a basic jinja2 template looks like and use it in a role.

At the run time, depending on, let's say in which datacenter your server is located, you can select from more than one nameservers, each corresponding to a datacenter, using the variable "resolver_ip_addresses."

```
{% for resolver in resolver_ip_addresses %}
nameserver {{ resolver }}
{% endfor %}

options timeout:1
options attempts:5
options rotate
```

In this example, in the playbook directory, there are defined some variables, including a variable named resolver_ip_addresses with different values depending on the datacenter.

```
- name: Set resolver for server
  template:
    src: dns.j2
    dest: /etc/resolv.conf
    group: root
    owner: root
    mode: "0644"
    tag: resolver
```

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto12.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto12.png)

Explanation:

1.  Name of the template to be used. Template is located in templates dir in the role path
2.  Destination path of the filename to be replaced with the template, on the client-side.
3.  Permissions of the destination file

The roles tasks can also have a tag field, which has a name attributed. More than one task can share the same tag. When running an ansible playbook, you can specify the tag as well, so those tasks will be executed.

## Case Study

In this section, we will analyze a Case study of an essential ansible playbook that has three roles. The purpose of this is to give a practical example of what we talked about before. Some of the examples used before in this tutorial will be adapted and used in this playbook.

Below is the directory structure of the playbook. The Yaml file that will be used will be p4.yml.
```
[ubuntu@ansible-server test_ansible]# ls -lrth
total 16K
-rw-r--r--. 1 root root   0 Jul  3 10:13 testfile
-rw-r--r--. 1 root root 203 Jul  3 13:30 p1.yml
-rw-r--r--. 1 root root 125 Jul  3 15:00 hosts
-rw-r--r--. 1 root root 488 Jul  3 16:40 p2.yml
-rw-r--r--. 1 root root 188 Jul  4 17:33 p4.yml
drwxr-xr-x. 5 root root  47 Jul  4 17:35 roles
[ubuntu@ansible-server test_ansible]# cd roles
[ubuntu@ansible-server roles]# ls -lrth
total 12K
drwxr-xr-x. 9 root root 4.0K Jul  4 12:52 httpd
drwxr-xr-x. 9 root root 4.0K Jul  4 13:55 selinux
drwxr-xr-x. 9 root root 4.0K Jul  4 16:54 resolver
```

The playbook has three roles, one called resolver that sets a specific nameserver on the servers by copying a file from the server to the /etc/resolv.conf destination. Another one is called httpd, and it installs the httpd package with yum module, and the third one enables SELinux and notifies the logged user to reboot the system. Each role was created using ansible-galaxy command.

Resolver role, main.yml task:

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto13.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto13.png)

Httpd role, main.yml task:

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto14.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto14.png)

Selinux role, main.yml task:

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto15.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto15.png)

Below is the p4.yml playbook defined. It will run on all hosts if not otherwise specified in the command line, it will run as root user on port 22 (SSH), it will gather facts before running the roles, and it will run all three roles mentioned before. Each role can be run independently by specifying the tag in the ansible-playbook command line with the –t parameter.


```
---

- hosts: all
  user: root
  port: 22
  gather_facts: True
  roles:
    - { role: selinux, tags: selinux }
    - { role: httpd, tags: httpd }
    - { role: resolver, tags: resolver }

```



Running the p4.yml playbook on two hosts and interpreting the output. The same command can be run with the –check parameter for a dry-run. In case you want to use password authentication, use -k parameter.

[![](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto16.png)](https://github.com/BINPIPE/learning-resources/blob/master/learning-notes/images/070919_1256_AnsibleTuto16.png)

Explanation:

1.  Ansible-playbook command that runs p4.yml
2.  Playbook skips SELinux role because it is already enabled.
3.  Ansible found that httpd package is already installed, so it returns ok.
4.  Resolver was set, and role resolver got status changed.






## Example Playbooks in Ansible

- [Deploying a Laravel Website using Ansible on LEMP Stack](https://github.com/BINPIPE/ansible-laravel-demo)
- [Setting Netdata Monitoring Application](https://github.com/BINPIPE/ansible-netdata)
- [Setting a LAMP Stack & Installing Wordpress](https://www.digitalocean.com/community/tutorials/how-to-use-ansible-to-install-and-set-up-wordpress-with-lamp-on-ubuntu-18-04)
  * Steps: [Deploy LAMP Stack & Install Wordpress on Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-use-ansible-to-install-and-set-up-wordpress-with-lamp-on-ubuntu-18-04)
  * Repository: [https://github.com/do-community/ansible-playbooks](https://github.com/do-community/ansible-playbooks)




<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry.
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions.
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
