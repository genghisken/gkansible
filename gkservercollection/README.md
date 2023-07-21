# Ansible Collection - gkansible.gkservercollection

Collection for installation of servers that contain the following software:
* Anaconda
* Cassandra 3 (now deprecated)
* Cassandra 4
* Cassandra keyspace and table deployment for the Lasair broker (ZTF and LSST)
* MySQL 8.0 
* MariaDB 10.6 (standalone)
* Cluster Control/MariaDB/Galera/Maxscale (default MariaDB version 10.6)
* SherlockDB - A sherlock database install - choose "empty" (default), "lite", "test" or "full". (The "full" deployment needs 5TB minimum partition size.) Should work with both MySQL and MariaDB.
* IRAF Legacy 32-bit requirements for the PESSTO pipeline
* IRAF Legacy Anaconda environment for PESSTO, SNID (Intel only)
* Pan-STARRS and ATLAS (PSAT) ingester code (first draft).

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

In case like me you're wondering where the `my.cnf` templates live for deployed Galera nodes, they live on the deployed Cluster Control server in `/usr/share/cmon/templates` (and Cluster Control ships them to the DB nodes, NOT Ansible). If we want to template the deployed `my.cnf` settings, we need to deploy Cluster Control and THEN modify the template in `/usr/share/cmon/templates` as part of the Ansible script, BEFORE running the actual database deploy script.
