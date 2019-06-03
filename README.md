# php-fpm

[![Build Status](https://travis-ci.com/iroquoisorg/ansible-role-php-fpm.svg?branch=master)](https://travis-ci.com/iroquoisorg/ansible-role-php-fpm)

Ansible role for php-fpm

This role was prepared and tested for Ubuntu 16.04.

# Installation

`$ ansible-galaxy install iroquoisorg.php_fpm`

# Default settings

```
php_fpm_version: "{{ php_version | default('7.2') }}"
php_fpm_socket: "/run/php/php{{ php_fpm_version }}-fpm.sock"
php_fpm_clear_env: 'yes'
php_fpm_env_file: "/etc/environment"
ci_build: false

```

# Development

Please check [development guide](DEVELOPMENT.md) for details about developing and testing this role.
