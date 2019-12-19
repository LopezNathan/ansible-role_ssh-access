# Ansible Role: ssh-access

- Authorized SSH Key Management
- CSF IP Whitelist Management

## Requirements

None

## Role Variables

#### SSH Key Management

Authorized Key File - File to be added to `authorized_keys`

```
authorized_key_file: ~/.ssh/id_rsa.pub
```

Authorized Key User - User to add key for

```
authorized_key_user: root
```

Authorized Key State - Ensure key is absent, or present

```
authorized_key_state: present
```

#### CSF Whitelist Management

Name - Meta name for specified IP

```
name: Example
```

IP Raw - Raw IP to verify if already whitelisted

```
ip_raw: '123.123.123.123'
```

IP Line - IP with comment to be whitelisted

```
ip_line: '123.123.123.123 # Example IP'
```

## Dependencies

None

## Example Playbook

```
---
- name: Configure SSH Access
  hosts: all
  become: yes
  roles: 
    - ssh-access
  vars:
    authorized_key_file: ~/.ssh/id_rsa.pub
    authorized_key_user: root
    ip_list:
      - name: Bob's Office IP
        ip_raw: '123.123.123.123'
        ip_line: '123.123.123.123 # Bobs Office'
```

## License

MIT

## Author Information

Created by Nathan Lopez