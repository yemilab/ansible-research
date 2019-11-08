# ansible-cup-devel

Ansible provisioning script for CUP development and analysis server.

## How to use Ansible playbook

Install `epel-release`, `git`, `ansible`.

```
$ sudo yum install epel-release git
$ sudo yum install ansible
```

Cloning.

```
$ git clone <ansible-cup-dev-url>
```

Update `hosts` file. For example,

```
[dev]
127.0.0.1
```

Make your own playbook,

```
- hosts: dev
  remote_user: cupadmin
  become: yes
  become_method: sudo
  roles:
    - basic
    - tcsh
    - build-root
```

Run ansible script

```
$ ansible-playbook -k -K -i hosts dev.yml
```

```
$ ansible-playbook -C -i hosts cluster.yml # -C: --check
$ ansible-playbook -k -i hosts cluster.yml # -k: --ask-pass, -K: --ask-become-pass
$ ansible-playbook -i hosts cluster.yml
```

## Roles

- `basic`: Install Emacs, Vim, Git, GCC

## Roles

- `dev-sqlite`: Runcatalog
