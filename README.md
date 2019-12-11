###########################################################################
                 DYNAMIC INVENTORY FOR ANSIBLE IN GCP
###########################################################################

Prerequisites:
apache-libcloud
pycrypto
pip

################

Install Prerequisites:
yum install -y /usr/lib/python2.7/site-packages/pip
pip install apache-libcloud
yum install -y python2-crypto-2.6.1-16.el7.x86_64

###############

Create inventory dir and add the gce.py script and gce.ini files in it
mkdir /etc/ansible/inventory
Dir structure will look like:
/etc/ansible/inventory/gce.py
/etc/ansible/inventory/gce.ini
Modify gce.ini to your needs.

###############
If you want to call all hosts from a zone
ansible -i ansible/inventory europe-west2-a -m ping

If you want to filter your instances, you can add network tags.
Ex: webserver

Call the hosts with the tag in your adhoc command or playbook.
ansible -i inventory tag_webserver -m ping

When calling the tagged servers, append "tag" in front of the actual nametag.
In playbooks, use this for hosts.
EX: hosts: tag_webserver