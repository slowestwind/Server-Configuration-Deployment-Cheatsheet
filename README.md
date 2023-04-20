# Server-Configuration-Deployment-Cheatsheet

## Create VPS & Firewall 
- Create account on any hosting server provider then create a vps (i.e droplets in case of DigitalOcean)
- Login into server using ssh command
`ssh root@user_name` and then password
- Create user with access
`adduser {username}`
`usermode -aG sudo {username}` 
- **Firewall setup**
`ufw allow openSSH`
`ufw enable`

## Transferring files, passwordless login
- **Transferring file via Filezilla**
login using user,password,port(22) 
- **Transferring file via Command**
local to server
`scp /path/to/local/file remote_user@remote_host:/path/to/remote/file`
`scp -r /path/to/local/folder remote_user@remote_host:/path/to/remote/folder` (user -r for folder transfer)
vise versa
`scp remote_user@remote_host:/path/to/remote/file /path/to/local/file`
`scp -r user@host:/path/folder /path/folder` (user -r for folder transfer)
**using .pem file**
`sudo scp -i ~/servers/your-key.pem ~/your-local-source-path/your-local-file.txt root@00.00.00.11:/you-server-destination-path/`
- Passwordless login
1. create a public-private key pair
`ssh-keygen -t rsa`
2. Deploy ssh key on your server
`scp home\.ssh\is_rsa.pub root@server_ip:~/.ssh/authorized_keys`
3. test your password login
`ssh user@ip-address`

