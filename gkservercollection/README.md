# Ansible Collection - gkansible.gkservercollection

Collection for installation of servers that contain the following software:
* Anaconda
* Cassandra
* MySQL 5.7
* MariaDB/Galera/Maxscale
* SherlockDB - A sherlock full database install (needs 6TB minimum partition)
* IRAF Legacy 32-bit requirements for the PESSTO pipeline
* IRAF Legacy Anaconda environment for PESSTO, SNID (Intel only)

NOTE: The code attempts to contact a Hashicorp Vault repository for various settings information.
If your settings are NOT stored there, please define the required variables (e.g. local_db_root_password)
in a "localsettings.yml" file, defined in your playbook directory. (See localsettings_example.yml)
