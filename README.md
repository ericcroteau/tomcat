tomcat_with_vg_and_lv v1.0.3
============================

This role is intended to install and upgrade a Tomcat version from an Infrastructure perspective. Although highly flexible, it is most suitable for SDDC environment.


Version History
---------------

Date        Initiator                           Version Number  Update

10/05/18    Eric Croteau                        v1.0.1          Initial Creation

10/24/18    Eric Croteau                        v1.0.2          Removed expiration on service user

11/22/18    Eric Croteau                        v1.0.3          Removed HTTP protocol and mapped IP address

11/23/18    Eric Croteau                        v1.0.4          Updated team members


Requirements
------------

- This script downloads Tomcat's binary directly from Apache's website; therefore external access is required.

- This role is meant to be installing/upgrade a single pool at a time on a single server, it is possible to create pool concurrently on multiple target servers.

- As this script is run with privileges, the remote_user must own the necessary permissions (sudo)


Role Variables
--------------

var_pool: mandatory, pool for which the new tomcat is to be installed (no default)

var_java_version: mandatory, specific java version to install (1.6.0 / 1.7.0 / 1.8.0)

var_tomcat_version: mandatory, version of tomcat to deploy (no default)

var_mapping_address: optional, IP address to map to Tomcat, useful to configure multiple Tomcat onto the same server (default= <target server IP>)

var_root_size: optional, size of the mountpoint where the Tomcat binaries and configuration will be installed (default= 10G)

var_logs_size: optional, size of the mountpoint where the Tomcat(s) logs (default= 20GB)

var_xmx: optional, maximum allowed heap of the JVM (default= 1024M)

var_xms: optional, initial heap of the JVM (default= <var_xmx>)


Example Playbook
----------------

- hosts: server1

  roles:
    - { role: tomcat_with_vg_and_lv, var_java_version: 1.8.0, var_pool: p0, var_tomcat_version: "9.0.8"}


Author Information
------------------

Eric Croteau
eric_croteau79@hotmail.com
