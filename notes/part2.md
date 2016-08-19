### Check YAML Syntax

```sh
$ python -c 'import yaml, sys; print yaml.load(sys.stdin)' < script.yml
```
or use this site: http://www.yamllint.com/

or 
```sh
$ ansible-playbook --syntax-check script.yml
```
### Ansible configuration
  - inventory = Location of the Ansible inventory file.
  - remote user = The remote user account used to establish connections to managed hosts.
  - become = Enables or disables privilege escalation for operations on managed hosts.
  - become_method = Defines the privilege escalation method on managed hosts.
  - become_user = The user account to escalate privileges to on managed hosts.
  - become_ask_pass = Defines whether privilege escalation on managed hosts should prompt for     a password

### Example privileged escalation 
```sh
[privilege_escalation] 
become=True
become_method=sudo
become_user=root
become_ask_pass=True
```
### List Hosts in the inventory
```sh
$ ansible <group-name> --list-hosts -v
```
### Ad-hoc options

* inventory = -i
* remote_user = -u 
* become = -b
* become-method = --become-method
* become_user = --become-user
* become_ask_pass = -K

### Input text in a file 
```sh
$ ansible <group-name -m copy -a 'content="Hi hello!" dest=/etc/foo' -u devops
```
### Example for become user
```sh
$ ansible <group-name -m copy -a 'content="Hi hello!" dest=/etc/foo' -u devops --become --become-user root
```
Still use the devops user to make the connection to the managed host, but perform the operation as the root user using the --become and --become-user so the required permissions are satisfied.

