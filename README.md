Chronos Role
=========

Configure and start Chronos (Mesos Framework) in a docker container using the image `indigodatacloud/chronos:latest`. 

This role has been specifically developed to be used for the deployment of Mesos in the framework of INDIGO-DataCloud project.

Role Variables
--------------

- `zookeeper_client_port` (default: 2181)
- `zookeeper_peers` (optional): list of zookeeper server nodes - alternatively, you can use a proper inventory file specifying the hosts group [zookeeper_servers]

- `chronos_version` (default: latest)
- `chronos_image` (default: indigodatacloud/chronos:{{chronos_version}}) 
- `chronos_framework_name` (default: chronos): name that will be used to register the framework on Mesos

SSL specific options:
- `generate_random_pass` (default: true): if set to true, the password used for creating the self-signed certificate are generated in a random way
- `chronos_key_password` (to be provided if `generate_random_pass`=false)
- `chronos_pkcs_password` (to be provided if `generate_random_pass`=false)
- `chronos_jks_password` (to be provided if `generate_random_pass`=false)


Dependencies
------------

- `indigo-dc.docker`

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: indigo-dc.chronos, zookeeper_peers: ["10.10.10.1", "10.10.10.2", "10.10.10.3" ] }

License
-------

Apache Licence v2 [1]

[1] http://www.apache.org/licenses/LICENSE-2.0

