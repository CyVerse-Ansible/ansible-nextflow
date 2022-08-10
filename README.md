CyVerse Ansible Nextflow
===================

This role will install nextflow and if desired Dolphinnext in a container.

Requirements
------------

This role only assumes that you are on a recent version of Ubuntu, and have k3s installed. It is ment to be installed on the k3s master.

Role Variables
--------------

The following table lists optional ansible variables along with the default values if not defined.

Variable Name | Default value if not defined | Description
------------- | ---------------------- | -----------
INSTALL_DOLPHINNEXT | false | installs dolphinnext in a container
PV_SPACE | 1Gi | the size of the PersistentVolume used by nextflow

Example Playbook
----------------

This is a sample playbook:
````
- hosts: k3s_cluster
  become: true
  roles:
    - ansible-nextflow
  vars:
    INSTALL_DOLPHINNEXT: true
````

Author Information
------------------
Ryan Schneider (rschneider@cyverse.org)
