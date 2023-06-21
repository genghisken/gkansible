# Ansible Collection - gkansible.gkservercollection

Collection for installation of servers that contain the following software:
* Anaconda
* Cassandra 3
* Cassandra 4
* MySQL 5.7
* MariaDB/Galera/Maxscale (default version 10.6)
* SherlockDB - A sherlock database install - choose "empty", "lite", "test" or "full". ("empty" is default. "full" needs 5TB minimum partition size.)
* IRAF Legacy 32-bit requirements for the PESSTO pipeline
* IRAF Legacy Anaconda environment for PESSTO, SNID (Intel only)
* Pan-STARRS and ATLAS (PSAT) ingester code.

NOTE: The code attempts to contact a Hashicorp Vault repository for various settings information.
If your settings are NOT stored there, please define the required variables (e.g. local_db_root_password)
in a "localsettings.yml" file, defined in your playbook directory. (See localsettings_example.yml)

Deployment is fairly straightforward, though it requires Ansible 2.10+.

* Install the collection: `ansible-galaxy collection install git+https://github.com/genghisken/gkansible.git`
* Download and copy the ansible_example.cfg file to ansible.cfg.
* If necessary, replace the "remote_user" in ansible.cfg. (Default is "ubuntu".)
* Copy the hosts_example.yml file to hosts.yml
* Edit the hosts.yml file and add the correct IP addresses of the target machines under the relevant machine group - e.g. [mysqlnodes].
* Run the playbook - e.g. ansible-playbook install-mysql.yml

