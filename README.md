
williamyeh.nodejs for Ansible Galaxy
============

[![Build Status](https://travis-ci.org/William-Yeh/ansible-nodejs.svg?branch=master)](https://travis-ci.org/William-Yeh/ansible-nodejs) [![Circle CI](https://circleci.com/gh/William-Yeh/ansible-nodejs.svg?style=shield)](https://circleci.com/gh/William-Yeh/ansible-nodejs)


## Summary

Role name in Ansible Galaxy: **[williamyeh.nodejs](https://galaxy.ansible.com/williamyeh/nodejs/)**

This Ansible role has the following features for [Node.js](http://nodejs.org/):

 - Install specific version of Node.js ([io.js](https://iojs.org/) is only supported under Debian/Ubuntu).




## Role Variables

### Mandatory variables

None.



### Optional variables

Pick one version to install:

```yaml
# Node.js version; e.g., "5", "4.0", "0.12", "0.12.7"
# Both numeric and string forms are ok.
nodejs_version


# io.js version; e.g., "3.3"
# NOTE: only available under Debian/Ubuntu.
iojs_version
```

If neither `nodejs_version` nor `iojs_version` is defined, `nodejs_version` is defined automatically by `tasks/set-role-variables.yml` according to `defaults/main.yml` settings:

  - `nodejs_default_in_apt` for Debian/Ubuntu.
  - `nodejs_default_in_yum` for CentOS.



Other user-configurable defaults:

```yaml
# install tools for compiling native addons from npm?
nodejs_compile: True
```


## Usage


### Step 1: add role

Add role name `williamyeh.nodejs` to your playbook file.


### Step 2: add variables

Set vars in your playbook file.

Simple example:

```yaml
---
# file: simple-playbook.yml

- hosts: all
  become: True

  roles:
    - williamyeh.nodejs

  vars:
    nodejs_version: 4.0
```


## Dependencies

None.


## License

Licensed under the MIT License. See the [LICENSE file](LICENSE) for details.


## History


- 1.0 : Use Ansible 2.0 syntax; support up to Node.js 5.x.

- Initial commit (2015-05-08): From now on, the role installs Node.js from [NodeSource](https://github.com/nodesource/distributions) binary distributions.



Older versions are based on NVM:

- Rewritten from my pre-Galaxy version [server-config-template](https://github.com/William-Yeh/server-config-template) and Galaxy version [ansible-nvm-nodejs](https://github.com/William-Yeh/ansible-nvm-nodejs).

- During refactoring, some roles on Ansible Galaxy also inspired me:

  - [leonidas.nvm](https://galaxy.ansible.com/list#/roles/694) forks, especially [ahmednuaman.nvm-ahmed](https://galaxy.ansible.com/list#/roles/2298) and then [g-div/ansible-nvm](https://github.com/g-div/ansible-nvm)


