Java
=========

Install an instance of java to the specified `JAVA_HOME` on the target host. The ansible role performs the following tasks:

* creates the java home parent directory ( java base )
* downloads and unpacks the specified jdk to the java base directory
* creates a symbolic link "java" to be used for JAVA_HOME
* optionally sets java alternatives link
* optionally installs the JCE policy jars

Requirements
------------

JDK binaries accessible from a remote file server

Role Variables
--------------

Role variables meant to be overridable are:

```
    java_work_dir: "/var/tmp/java"
    java_home: "/opt/java"
    java_base: "{{ java_home|dirname }}"
    java_update_alternatives: False
    java_user: '{{ ansible_user_id }}'
    java_group: '{{ ansible_user_id }}'
    java_jce: True
    java_update_java_alternatives: False
    fileserver: "https://files-ews-works.s3-us-west-2.amazonaws.com"
```


> **Supported jdk versions are**:
>
* hotspot-jdk-8u251-linux-x64

Dependencies
------------
Depends on a file server

Example Playbook
----------------

The following example installs jdk `hotspot-jdk-8u251` to the target system to `/opt/foo/java`

```
- hosts: servers
  roles:
    - role: ansible-role-java
      vars:
        java_home: /opt/foo/java
        jdk_vers: hotspot-jdk-8u251
```

License
-------

BSD

Author Information
------------------

