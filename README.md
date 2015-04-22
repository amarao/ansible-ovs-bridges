ovs-bridges
=========

Configure bridges for openvswitch

Requirements
------------

Ansible 1.4.
You'll need working OVS on target host (ovs-vsctl)

Role Variables
--------------

    ovs_bridges:
      - name: br_foo
        iface: eth1
      - name: br_bar
    ovs_timeout: 5

(iface and ovs_timeout are not mandatory)

Note: this role does not check if interface (iface) exists or not. It's perfectly valid (from OVS point of view) to add non-existing interface to the bridge.

Note2: You shoud be really careful with active interfaces. If you say name:br-ex iface:eth0, you will loose connectivity by high chance.

Note3: You need to bring iface up to allow traffic from bridge to outer network.

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      vars:
        ovs_bridges:
          - name: br-ex
            iface: eth1
          - name: br-test
          - name: br-test2 
      roles:
         - ovs_bridges

License
-------

BSD

Author Information
------------------

(c) George Shuklin, 2015
