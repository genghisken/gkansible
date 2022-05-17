# gkansible
A repository of Ansible roles. These currently include:

* Anaconda
* Cassandra 3
* Cassandra 4
* MySQL 5.7
* MariaDB/Galera/Maxscale (default version 10.6)
* SherlockDB - A sherlock database install - choose "empty", "lite", "test" or "full". ("empty" is default. "full" needs 5TB minimum partition size.)
* IRAF Legacy 32-bit requirements for the PESSTO pipeline
* IRAF Legacy Anaconda environment for PESSTO, SNID (Intel only)


Make sure you can login to any newly created nodes from the control node before running these deployments.

Deployment is fairly straightforward, though it requires Ansible 2.10+.

* Install the collection: `ansible-galaxy collection install git+https://github.com/genghisken/gkansible.git`
* Download and copy the ansible_example.cfg file to ansible.cfg.
* If necessary, replace the "remote_user" in ansible.cfg. (Default is "ubuntu".)
* Copy the hosts_example.yml file to hosts.yml
* Edit the hosts.yml file and add the correct IP addresses of the target machines under the relevant machine group - e.g. [mysqlnodes].
* Run the playbook - e.g. ansible-playbook install-mysql.yml

That's it.

Note that some work is still required to make the scripts fully idempotent, but they should work first time on a virgin OS install. The current Anaconda and Cassandra installs have been tested on both RedHat and Ubuntu. The MySQL and Sherlock installs are only fully tested on Ubuntu so far.  The Sherlock install also needs access to a filesystem that contains a snapshot of the Sherlock database.

Coming soon (for Ubuntu at least):

* PHP 7.4
* MediaWiki
* Apache proxy
* Django/Mod-WSGI webservers
