# AWS Safe Access
*This tool can be used to grant access to public instances on AWS for your external IP address, or to quicly access instances via SSH.*

#### Grant/Revoke your External IP address access to instances:
- The scripts adds or removes a rule from the Instance's Security Group
- The script adds a description with the user name in it, so if the IP changes the old rule is detected and deleted, and a new rule is created with the current IP


#### SSH Access Sequence:
- The script starts the instance in case it's stopped
- Adds a rule to the instance's Security Group to allow your External IP address access via port 22 (or other specified port)
- If -d argument is used the rule is removed a few seconds after initial SSH connection - Safer than VPN


To refer to an instance you can write only partial data of: instance id, name, ip, state
If there are mulitiple matching instances, a choice will be presented

### Examples:
#### Access Granting/Revoking Examples:

|  Instance ID |  Instance Name | Public IP    |  State       |
| ------------ | ------------   | ------------ | ------------ |
|  i-ab123456  |  app-server    | 1.1.1.1      |  running     |


- Grant TCP 80 access to instance:
```
acc app tcp 80
acc i-ab tcp 80
acc 1.1.1 tcp 80
acc runn tcp 80
```
- Revoke UDP 53 access to instance : `acc serv udp 53 -r`

- Grant ANY access to instance: `acc app any`

#### SSH Access Examples:
- Access using OS username and id_rsa key: `acc -s app`
- Access using user Ubuntu and custom key: `acc -s ubuntu@app -i key.pem`
- Access using user Ubuntu and custom key: `acc -s app -u ubuntu -i key.pem`
- Access using user Ubuntu, custom port, and custom key: `acc -s ubuntu@1.1 -p 10443 -i key.pem`

