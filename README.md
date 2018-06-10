Ansible Configuration For Deploying CiviCRM
===========================================

This configuration will deploy a fresh CiviCRM (Wordpress) install to a remote host.

This configuration was created for migration of the Australsaian Aikikai (https://australasianaikikai.com) site from AWS to Linode.

Usage
----- 
Deploying is easy. Configure the hosts file with your user/host combos.

```
[user]
123.456.78.90
234.567.89.10
```

With your hosts file configured you can run the `ansible-playbook` command from the root of this repository like so:

```
ansible-playbook civicrm.yml -i hosts 
```

This will provision a LAMP stack on the remote host, install the latest wordpress, and grab the specified version of CiviCRM.

The file `group_vars/all` contains configuration values for specifying mysql version, CiviCRM version, and database credentials.
