# ansible-playbook
My ansible playbook for automated operation and maintenance, currently only support
ubuntu and debian. I use default hosts file location "/etc/ansible/hosts".

## Command.

### Common.

This block is common task for most servers. Including:

+ Update apt source.
+ Install necessary package via apt.
+ Install supervisor.

### Apt.

This block is used to install or purge package via apt. You can add installed or removed package name in
"roles/apt/vars/main.yml".

#### Usage

+ Install package

```
ansible-playbook site.yml --tags "install"
```

+ Purge package

```
ansible-playbook site.yml --tags "purge"
```

### User & Group.

This block is used to create a user to deploy apps, and create an admin group.
The name of user and the name of group are defined in "group_vars/all". And if you want to
remove a user or group, please change the variables in "roles/user/vars/main.yml".

#### Usage

+ Create a user.

```
ansible-playbook site.yml --tags "create_user" [--extra-vars "username=foo"]
```

+ Create a group.

```
ansible-playbook site.yml --tags "create_group" [--extra-vars "groupname=foo"]
```

+ Delete a group.

```
ansible-playbook site.yml --tags "delete_group" [--extra-vars "groupname=foo"]
```

+ Give a group sudo permission.

```
ansible-playbook site.yml --tags "add_sudo" [--extra-vars "groupname=foo"]
```

### File

Create app directories.

#### Usage

```
ansible-playbook site.yml --tags "create_app_dir"
```

### Supervisor

Initialize supervisor config.

#### Usage

```
ansible-playbook site.yml --tags "supervisor"
```
