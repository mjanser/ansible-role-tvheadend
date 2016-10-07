# Ansible Role: tvheadend

An Ansible role that installs tvheadend on Fedora.

## Requirements

Nginx needs to be installed beforehand. To achieve this the following roles could be used:
- mjanser.nginx

## Role Variables

Available variables are listed below, along with default values:

    tvheadend_server_name: example.com
    tvheadend_port: 9090
    tvheadend_allowed_network: "{{ ansible_default_ipv4.network|default('192.168.1.0') }}/{{ ('192.168.1.0/' ~ ansible_default_ipv4.netmask|default('255.255.255.0'))|ipaddr('prefix') }}"

## Dependencies

None

## Example Playbook

    - hosts: all
      roles:
        - { role: mjanser.tvheadend }

## License

MIT
