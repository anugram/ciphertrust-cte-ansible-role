ciphertrust-cte-ansible-role
============================

This role allows the administrator to install CipherTrust Transparent Encryption agent on a target machine like Ubuntu as well as configure CipherTrust Manager to apply policies for the agent.

Install role -
```ansible-galaxy install anugram.ciphertrust-cte-ansible-role```

Requirements
------------

* Running instance of Thales CipherTrust Manager for which you may use the free-forever community edition available at https://ciphertrust.io
* CipherTrust Transparent Encryption Agent binary file
* Copy the above binary file in the files folder

Role Variables
--------------
Update the below variables in default/main.yml file.

| Variable Name | Description |
|---|---|
| this_node_address | IP or FQDN of thr CipherTrust Manager or CM |
| this_node_username | admin username of CM |
| this_node_password | password of the admin user |
| ca_id | Cm Local Certificate Authority ID to issue registration token |
| cert_duration | duration for the registration token keys |
| client_profile | Profile to be used for creating clients using the registration token |
| lifetime | lifetime of the token itself |
| max_clients | maximum number of clients using the token |
| name_prefix | client name prefix |
| agent_binary_name | common name to include in the certificate signing request |
| username | CM name for the CSR |
| key_name | Name of the key to be created for the CTE agent |
| key_algo | key algorithm |
| key_size | Key size depending on algorithm |
| resource_set_name | name of the resource set |
| cte_policy_name | CTE policy name to be created |
| guard_paths | Guard Paths to be protected by the CTE Agent |

Dependencies
------------
Download below tools -

* git
* ansible

Clone the CipherTrust CDSP Ansible collection -

```git clone https://github.com/ThalesGroup/CDSP-Orchestration.git```


Build and install ThalesGroup CipherTrust Ansible collection as below -

```
cd Ansible/thalesgroup/ciphertrust
ansible-galaxy collection build
ansible-galaxy collection install thalesgroup-ciphertrust-1.0.0.tar.gz
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      roles:
         - ciphertrust-cte-ansible-role

License
-------

MIT

Author Information
------------------

Anurag Jain, Developer Advocate at ThalesGroup
