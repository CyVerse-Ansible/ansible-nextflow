CyVerse Ansible Nextflow
===================

This role will install nextflow and if desired Dolphinnext in a container.
If Dolphinnext is installed connect via http://localhost:8080/dolphinnext

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

Starting Dolphinnext
--------------------

1. Running the container:

docker run -m 10G -p 8080:80 -v /root/dolphinnext-studio/data:/export -ti ummsbiocore/dolphinnext-docker /bin/bash

2. After you start the container, you need to start the mysql and apache server using the command below:

startup

3. Verify that dolphinnext and mysql folders located inside of the /export folder:

ls /export

4. Now, you can open your browser to access dolphinnext using the url below:

http://localhost:8080/dolphinnext

Note: in dolphinnext container the config is at dolphinnext/config/.sec


Author Information
------------------
Ryan Schneider (rschneider@cyverse.org)
