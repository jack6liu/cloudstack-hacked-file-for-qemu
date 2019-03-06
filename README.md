# cloudstack-hacked-file-for-qemu
hacked files only for qemu hosts, not compatible with KVM hosts!!!

Environment Tested:

- OS Version:

    ```bash
    cat /etc/redhat-release 
    CentOS Linux release 7.6.1810 (Core)
    ```

1. cloudstack-4.11.2.0.jar (cloudstack-management only) is hacked version for `/usr/share/cloudstack-management/lib/cloudstack-4.11.2.0.jar`
2. cloud_utils.py is hacked version for `/usr/lib64/python2.7/site-packages/cloud_utils.py`
3. utilities.py is hacked version for `/usr/lib64/python2.7/site-packages/cloudutils/utilities.py`
4. cloud-plugin-hypervisor-kvm-4.11.2.0.jar is hacked version for `/usr/share/cloudstack-agent/lib/cloud-plugin-hypervisor-kvm-4.11.2.0.jar`
    
Mini How-To:
- On cloudstack-management server
    - install cloudstack-management as official guide
    - run cloudstack-setup-database
    - run cloudstack-setup-management, wait and verify the cloudstack management server is working well!
    - then, stop cloudstack-management.service via `systemctl stop cloudstack-management.service`
    - backup `/usr/share/cloudstack-management/lib/cloudstack-4.11.2.0.jar` and replace with hacked version
    - backup `/usr/lib64/python2.7/site-packages/cloud_utils.py` and replace with hacked version
    - backup `/usr/lib64/python2.7/site-packages/cloudutils/utilities.py` and replace with hacked version
    - start cloudstack-management.service via `systemctl start cloudstack-management.service`
    - wait and verify the cloudstack management server is up and ready!

- On cloudstack-agent server (Qemu Host)
    - install cloudstack-agent as official guide
    - wait and verify the cloudstack-agent is working well, then
    - backup `/usr/share/cloudstack-agent/lib/cloud-plugin-hypervisor-kvm-4.11.2.0.jar` and replace with hacked version
    - restart cloudstack-agent.service via `systemctl restart cloudstack-agent.service`
    - wait and verify the cloudstack-agent is up and ready, then
    
- On cloudstack-management server (After hack)
    - login to cloudstack web UI, add the hacked Qemu host as new 'KVM' host

- Finished!
