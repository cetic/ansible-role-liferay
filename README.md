# Ansible Role: Liferay

[![Build Status](https://travis-ci.org/cetic/ansible-role-liferay.svg?branch=master)](https://travis-ci.org/cetic/ansible-role-liferay)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-_cetic.liferay-blue.svg)](https://galaxy.ansible.com/cetic/liferay/)

Installs Liferay on RHEL/CentOS servers with [ansible](http://www.ansible.com/home).

## Requirements

--

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### liferay
	liferay_port: '8080'
	liferay_db_user: 'liferay'
	liferay_db_password: 'liferay'
	liferay_default_database_url: "jdbc:mysql://{{ ip_mysql }}/liferay?useUnicode=true&characterEncoding=UTF-8&useFastDateParsing=false"

	liferay_archive_url: 'http://sourceforge.net/projects/lportal/files/Liferay%20Portal/6.2.3%20GA4/liferay-portal-tomcat-6.2-ce-ga4-20150416163831865.zip'
	liferay_version: '6.2.ce'
	liferay_bundle_base_dir_name: 'liferay-portal-6.2-ce-ga4'

Liferay archive to be installed. If the file in `local` exists it will be used. 

	liferay_unpack_folder: '/opt'
	
The folder on the server whe the Liferay bundle will be unpacked

	liferay_home: '/opt/liferay'
	
Liferay's home folder.

	liferay_user: 'liferay'
	liferay_group: 'liferay'

The operating system user and group that will be used to run Liferay	
	
	liferay_dl_folder: '{{ liferay_home }}/data/document_library/'

A folder where files from Liferay's document library will be stored.

	liferay_bundle_tomcat_version: '7.0.42'
	liferay_tomcat_dir: '{{ liferay_home }}/tomcat-{{ liferay_bundle_tomcat_version }}'

The version of the Tomcat that is bundled in the current Liferay Portal server installation.
	
	liferay_autodeploy_dir: '{{liferay_home}}/deploy'
	liferay_enable_remote_debug: false
	liferay_cluster_autodetect: google.com:80

	liferay_db_host: '127.0.0.1'
	liferay_default_database_driver : 'com.mysql.jdbc.Driver'
	liferay_additional_databases: []
	
Liferay database informations.
	
### geerlingguy java

	java_home: '/lib/jvm/jre-1.8.0-openjdk'

## Dependencies

  - geerlingguy.java

## Example Playbook

```yaml
- hosts: liferay
  vars:
    mysql_databases:
      - name: liferay
    mysql_users:
      - name: liferay
        password: liferay
        priv: "liferay.*:ALL"
  become: true
  roles:
    - role: geerlingguy.java
      when: "ansible_os_family == 'RedHat'"
      java_packages:
        - java-1.8.0-openjdk
    - role: geerlingguy.mysql
    - role: cetic.liferay
```

## Tests

### testing locally with [Vagrant](https://www.vagrantup.com/)

You can test this ansible role by using `vagrant`. See the Vagrantfile.

### testing with Travis

See the playbook used for Travis CI tests (tests/test.yml).

## Future improvements

* Provide more recent version of Liferay
* Add Solr plugin
* Linux support

Feel free to contribute.

## License

MIT License

## Sources
* https://github.com/azzazzel/ansible-liferay
* https://github.com/silpion/ansible-liferay
