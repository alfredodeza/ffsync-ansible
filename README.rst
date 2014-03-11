Firefox Sync Playbook
=====================
These playbooks will allow you to setup a working Firefox Sync with Ansible.

To run with ansible directly (if a machine is up)::

    ansible-playbook -vvv -i playbooks/hosts playbooks/setup-devserver.yml

If you get an 'Invalid url' when adding your new server and you are using HTTPS
then it means that you probably have a self-signed certificate. You *fix* this
by navigating to that address on the client's browser and accepting the
certificate.
