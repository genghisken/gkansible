# gkansible
A repository of Ansible playbooks. These currently include:

* Anaconda
* Cassandra
* MySQL 5.7
* SherlockDB - A sherlock full database install (needs 6TB minimum partition)

Make sure you can login to any newly created nodes from the control node before running these deployments.

Deployment is fairly straightforward.

* Copy the ansible_example.cfg file to ansible.cfg.
* If necessary, replace the "remote_user" in ansible.cfg. (Default is "ubuntu".)
* Copy the hosts_example.yml file to hosts.yml
* Edit the hosts.yml file and add the correct IP addresses of the target machines under the relevant machine group - e.g. [mysqlnodes].
* Run the playbook - e.g. ansible-playbook install-mysql.yml

That's it.

Note that some work is still required to make the scripts fully idempotent, but they should work first time on a virgin OS install. The current Anaconda and Cassandra installs have been tested on both RedHat and Ubuntu. The MySQL and Sherlock installs are only fully tested on Ubuntu so far.  The Sherlock install also needs access to a filesystem that contains a snapshot of the Sherlock database.
