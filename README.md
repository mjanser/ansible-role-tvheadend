# Ansible Role: tvheadend

An Ansible role that installs tvheadend on Fedora.
It uses the packages in the copr [dani/tvheadend](https://copr.fedorainfracloud.org/coprs/dani/tvheadend/).

This role currently disables ACL of tvheadend, but access is restricted to the configured network.

## Requirements

Nginx needs to be installed beforehand. To achieve this the following roles could be used:
- mjanser.nginx

## Role Variables

Available variables are listed below, along with default values:

    tvheadend_server_name: example.com
    tvheadend_port: 9090
    tvheadend_allowed_network: "{{ ansible_default_ipv4.network|default('192.168.1.0') }}/{{ ('192.168.1.0/' ~ ansible_default_ipv4.netmask|default('255.255.255.0'))|ipaddr('prefix') }}"

    tvheadend_recordings: /home/tvheadend/recordings

### Server name and port

This is the hostname for accessing tvheadend. It's used as `server_name` in the nginx virtual host.

The port is where tvheadend will listen on. This will also be configured for the upstream in nginx.

### Allowed network

The parameter `tvheadend_allowed_network` can be used to restrict access to the nginx virtual host.
This defaults to the entire network of the main network interface.

### Recordings

The path in the parameter `tvheadend_recordings` will be created with the correct permissions to store recordings.
You still have to configure tvheadend to actually use this directory.

## Dependencies

None

## Example Playbook

    - hosts: all
      roles:
        - { role: mjanser.tvheadend }

## License

MIT
