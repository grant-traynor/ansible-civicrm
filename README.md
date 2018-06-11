Ansible Configuration For Deploying CiviCRM
===========================================

This configuration will deploy a fresh CiviCRM (Wordpress) install to a remote host.

This configuration was created for migration of the Australsaian Aikikai (https://australasianaikikai.com) site from AWS to Linode.

# Usage

## CiviCRM Extensions

## Provisioning
There is a role called 'provision'. Generally this would be used to restore an existing Wordpress and CiviCRM database
into the newly minted system, along with any media files (photos typically). Put the appropraite filenames into the 
group_vars/all file.

### Wordpress Database Restore
The wordpress database file will be installed into the wordpress database. It's assumed that this file was dumped
into SQL format using mysqldump or something else compatible with the ansible mysql_db module.

### CiviCRM Database Restore
The civicrm database file will be installed into the civicrm database. It's assumed that this file was dumped
into SQL format using mysqldump or something else compatible with the ansible mysql_db module.

### CiviCRM Media Files


## Manual Steps
There are a few manual steps that need to be performed.

### Wordpress Database Upgrade
### CiviCRM Database Upgrade
The CiviCRM database will likely need to be upgraded due to revision differences between the CiviCRM version
dumped from, and the version of CiviCRM we're dumping into. Need to go to the URL like:
- http://example.org/wp-admin/admin.php?page=CiviCRM&q=civicrm/upgrade&reset=1

Refer to instructions on: https://docs.civicrm.org/sysadmin/en/latest/upgrade/wordpress/


```
[user]
123.456.78.90
234.567.89.10
```

With your hosts file configured you can run the `ansible-playbook` command from the root of this repository like so:

```
ansible-playbook civicrm.yml -i hosts  --ask-sudo-pass
```

This will provision a LAMP stack on the remote host, install the latest wordpress, and grab the specified version of CiviCRM.

The file `group_vars/all` contains configuration values for specifying mysql version, CiviCRM version, and database credentials.
