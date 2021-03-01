# Ansible Role: Valheim Server

Installs and configures a dedicated server instance of the game Valheim on linux

## Requirements
None, tested on Ubuntu 20.04

## Install
### Single Role

Execute shell

```yaml
$ ansible-galaxy install git+https://github.com/kgengler/ansible-role-valheim-server.git
```

### In Requirements file
Create a requirements.yml file

```yaml
---
- name: valheim-server
  src: git+https://github.com/kgengler/ansible-role-valheim-server.git
```

Execute shell

```yaml
$ ansible-galaxy install -r requirements.yml
```

## Usage
```
---
- name: Playbook Name
  roles:
    - name: valheim-server
      vars:
        server_name: Custom Name
        # Additional vars...
```

## Role Variables
### Server Information

Set Server name
```yaml
server_name: My server
```

Set Server World Name
```
server_world: Dedicated
```

Port Client will use to connect to server. Note: The valheim server
will bind to several ports on startup. This is used by the client
for the initial connection
```yaml
server_port: 2456
```

Password required by client to join server
```yaml
server_password: secret
```

### System Customization
Set the system user that will be created to run the server as
```yaml
service_user: valheim-server
```

Set the system directory that the server will be installed at
```
application_dir: /opt/valheim-server
```

The Steam app ID for the dedicated valheim server
```yaml
steam_app_id: 896660
```

### User Access Control
All user lists use SteamID64 values. This tool may be helpful
[https://steamidfinder.com](https://steamidfinder.com)

Set a list of user admins (SteamID64)
```yaml
user_adminlist: []
```

Set a list of banned users (SteamID64). Note that the banned
list and permitted list should not be used together.
```yaml
user_bannedlist: []
```

Set a list of permitted users (SteamID64). Note that the banned
list and permitted list should not be used together.
```yaml
user_permittedlist: []
```
