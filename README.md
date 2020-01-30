# Ansible Role: Postfix

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-postfix.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-postfix)

Installs postfix on RedHat/CentOS or Debian/Ubuntu.

## Requirements

If you're using this as an SMTP relay server, you will need to do that on your own, and open TCP port 25 in your server firewall.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    postfix_config_file: /etc/postfix/main.cf

The path to the Postfix `main.cf` configuration file.

    postfix_service_state: started
    postfix_service_enabled: true

The state in which the Postfix service should be after this role runs, and whether to enable the service on startup.

    postfix_inet_interfaces: localhost
    postfix_inet_protocols: all

Options for values `inet_interfaces` and `inet_protocols` in the `main.cf` file.

    postfix_relayhost: [smp.google.com]:587
    postfix_relay_username: user
    postfix_relay_password: !vault | $ANSIBLE_VAULT;1.1;AES256...

Option to enable relaying to a remote host, optionally with smtp authentication. You will need to set Postfix smtp sasl
configuration values to ensure that the type of authentication you need is available and used.

Relay could also be MailHog on the localhost, port 1025. See [MailHog](https://github.com/geerlingguy/ansible-role-mailhog).

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - geerlingguy.postfix

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
