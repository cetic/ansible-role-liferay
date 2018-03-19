# Ansible Role: Liferay

[![Build Status](https://travis-ci.org/cetic/ansible-role-alfresco.svg?branch=master)](https://travis-ci.org/cetic/ansible-role-liferay)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-_cetic.liferay-blue.svg)](https://galaxy.ansible.com/cetic/liferay/)

Installs Liferay on RHEL/CentOS servers with [ansible](http://www.ansible.com/home).

## Requirements

-

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### tomcat

	
### geerlingguy java

	java_home: '/lib/jvm/jre-1.8.0-openjdk'

## Dependencies

  - geerlingguy.java

## Example Playbook

```yaml
- hosts: liferay
  roles:
    - role: geerlingguy.java
    - role: cetic.liferay
      become: true
```

## Future improvements

*  
Feel free to contribute.

## License

[Gnu General Public License 3.0](https://www.gnu.org/licenses/gpl.html)

## Sources
* https://github.com/azzazzel/ansible-liferay
* https://github.com/silpion/ansible-liferay
