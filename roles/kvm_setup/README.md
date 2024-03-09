kvm-setup
=========

Role will setup a Ubuntu 23.04 server to be a kvm host

Requirements
------------

None

Role Variables
--------------

Currently the following variables are required and expected to be pass via the playbook that includes the role
```yaml
user: User account.
public_ssh_key_for_domains: Public ssh key that will be put into the domain images. Might move this to the provisioning role
interface: Real interface
bridge_interface: Bridge interface
addresses: ipv4 address in this format x.x.x.x/x so 192.168.1.5/24
macaddress: Mac address of interface
default_route: Default gateway
nameservers: dns servers
```

Dependencies
------------

None

Example Playbook
----------------
```yaml
  hosts: kvm
  gather_facts: true
  become: true
  vars:
    user: username
    public_ssh_key_for_domains: domains.pub
    interface: eth0
    bridge_interface: br0
    addresses: 192.168.1.5/24
    macaddress: 00:26:55:dd:ff:25
    default_route: 192.168.1.1
    nameservers: 8.8.8.8


  tasks:
    - name: KVM Setup Role
      include_role:
        name: kvm_setup
      vars:
        user: "{{ user }}"
        public_ssh_key_for_domains: "{{ public_ssh_key_for_domains }}"
        interface: "{{ interface }}"
        bridge_interface: "{{ bridge_interface }}"
        addresses: "{{ addresses }}"
        macaddress: "{{ macaddress }}"
        default_route: "{{ default_route }}"
        nameservers: "{{ nameservers }}"
```

License
-------

GPL-2.0-or-later

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
