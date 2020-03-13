# IBM z/OS Management Facility Ansible collection
The IBM z/OS Management Facility (z/OSMF) Ansible collection, referred to as `ibm_zos_zosmf`, consists of modules and roles that you can use with z/OS.


## Technical overview
The sections that follow explain how to configure and use the `ibm_zos_zosmf` collection.

The collection intends to allow Ansible to drive z/OS operation and configuration by manipulating z/OS resources and data based on z/OSMF RESTful services, such as z/OSMF workflow services etc.

### Configure the target z/OS systems and z/OSMF server
The target z/OS systems should be configured as the target hosts (managed nodes) in your playbook. It is not necessary for a z/OSMF server to be installed on every target z/OS system. However, a z/OSMF server must be installed and active on *at least one* z/OS system in the same sysplex.

Information about the z/OSMF server must be configured in the `vars` file, such as the hostname, port number, and authentication info. Either username and password or client-certificate authorization can be used for authenticating with the z/OSMF server.  If both methods are specified, the system attempts to use client-certificate authentication.


## Contents
- [Manipulating z/OS workflows](docs/README_workflow.md)
    - modules:
        - [workflow](docs/README_workflow.md#Modules)
    - roles:
        - [complete_workflow](docs/README_workflow.md#Roles)


## Installation
The collection is distributed through [Ansible Galaxy](https://galaxy.ansible.com/). You can use the [ansible-galaxy](https://docs.ansible.com/ansible/latest/cli/ansible-galaxy.html) command to install the collection on your control node, as follows:

```
ansible-galaxy collection install ibm.ibm_zos_zosmf
```

By default, the collection is installed in `~/.ansible/collections`. The output looks like this:

```
Process install dependency map
Starting collection install process
Installing 'ibm.ibm_zos_zosmf:1.0.0' to '~/.ansible/collections/ansible_collections/ibm/ibm_zos_zosmf'
```

To specify the installation path, include the `-p` option with [ansible-galaxy](https://docs.ansible.com/ansible/latest/cli/ansible-galaxy.html) command:

```
ansible-galaxy collection install ibm.ibm_zos_zosmf -p /myAnsible/collections
```

### Local build and installation
For local build and installation, you can clone the Git repository, build the collection archive, and install the locally built collection without Galaxy.

1.  Clone the Git repository:

    ```
    git clone git@github.com:ibm/ibm_zos_zosmf.git
    ```

2.  Run a local build inside the collection:

    ```
    cd ibm_zos_zosmf
    ansible-galaxy collection build
    ```

    The example output looks like this:

    ```
    Created collection for ibm.ibm_zos_zosmf at /Users/user/git/ibm/ibm_zos_zosmf/ibm-ibm_zos_zosmf-1.0.0.tar.gz
    ```

3.  Install the locally built collection:

    ```
    ansible-galaxy collection install ibm-ibm_zos_zosmf-1.0.0.tar.gz
    ```

    The example output looks like this:
    
    ```
    Process install dependency map
    Starting collection install process
    Installing 'ibm.ibm_zos_zosmf:1.0.0' to '~/.ansible/collections/ansible_collections/ibm/ibm_zos_zosmf'
    ```


## Usage
The collection provides various sample playbooks to demonstrate the use of modules and roles in the directory [examples](examples/README.md).


## Contributions
See the section [Contributing In General](CONTRIBUTING.md).


## Copyright
© Copyright IBM Corporation 2020.


## License
Some portions of the collection are licensed under [GNU General Public License, Version 3.0](https://opensource.org/licenses/GPL-3.0), and other portions of the collection are licensed under [Apache License, Version 2.0](https://opensource.org/licenses/Apache-2.0). See individual files for applicable licenses.


## Author Information
This collection is maintained by the IBM z/OSMF development team. For more information about z/OSMF, see the following website: https://ibm.github.io/zOSMF/