# Project#1 w/ Ansible & Vagrant
### This project allows Vagrant to provision systems with Ansible by executing tasks locally on the target VM's. The 'Webservers' are configured with Nginx.

#### Steps:
1. Ensure that virtualenv is activated:
```
source venv/bin/activate
```

2. Deploy VM's (Should be roughly <5mins):
```
$ pip install -r requirements.txt
$ vagrant up
```

3. Once complete, confirm that both webserver pages load successfully by visiting the following url:
- [http://10.101.1.2]
- [http://10.101.1.3]

4. To destroy the VM's:
```
$ vagrant destroy -f
```

5. Troubleshooting:
- Ad-Hoc command to query for Ansible Facts (for index.html.j2)
```
$ ansible -i inventory/development <NAME OF VM> -m setup -u <USERNAME>
```
- To re-run your Ansbile Playbooks to deploy changes:
```
$ ansible-playbook -i inventory/deployment site.yml
```
- Alternatively, use this (Vagrant) if you need to update the VM
```
$ vagrant provision
```
- Note: If you don't have virtualenv (tool to create isolated Python environments) Just make sure you have Python/pip in your system
```
$ pip install virtualenv
```
- We normally don't need to include **---system-site-packages** in the following command but due to a bug with certain Ansible modules when running a Python env on CentOS7 hosts, this was the solution.
```
$ virtualenv -p /usr/bin/python --system-site-packages venv
```
