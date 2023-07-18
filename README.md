ciphertrust-cte-ansible-role
============================

This role allows the administrator to install CipherTrust Transparent Encryption agent on a target machine like Ubuntu as well as configure CipherTrust Manager to apply policies for the agent.

Install role -
```ansible-galaxy install anugram.ciphertrust_cte_ansible_role```

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

* ansible

Install ThalesGroup CipherTrust Ansible collection as below -

```
ansible-galaxy collection install thalesgroup.ciphertrust
```

Example Playbook
----------------

Use the sample_playbook.yml as below
```
---

- hosts: cte-clients
  become: yes
  roles:
    - anugram.ciphertrust_cte_ansible_role
```

Run the sample playbook -
```
ansible-playbook -i tests/inventory sample_playbook.yml  -u <user_target_machine> --ask-become-pass -vvv
```
This role has to be executed with admin user for CTE to get installed. 

License
-------

MIT

Author Information
------------------

Anurag Jain, Developer Advocate at ThalesGroup
