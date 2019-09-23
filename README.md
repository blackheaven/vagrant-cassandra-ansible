# Requirements
 * `ansible` => 2.5.1

# Requirements
An apt-based distribution with `openjdk-8-jdk` available.

# Configuration
[Configuring](http://cassandra.apache.org/doc/3.11/configuration/cassandra_config_file.html) can be done in `roles/cassandra-cluster/templates/cassandra.yaml.j2`.

# Launching the playbook
In order to execute the playbook, you have to launch this command:

```bash
$ ansible-playbook -i inventory.yml CassandraCluster.yml
```

You will have to configure the following parameters in the `inventory/inventory.yml` file:
* `ansible_ssh_user` is the user with root privileges on the VM
* `ansible_ssh_host` is the host of the VM
* `/path_to/private_key` is the path to the private key used to connect to the VMs declared in the inventory configuration file.

# Run tests
## Requirements
 * `libvirt` => 4.0.0
 * `openjdk-8-jdk` => 8u222
 * `virtualbox` => 5.2.32
 * `vagrant` => 2.0.2

## Running

```bash
$ vagrant up
$ ansible-playbook -i inventory-test.yml CassandraCluster.yml
```
