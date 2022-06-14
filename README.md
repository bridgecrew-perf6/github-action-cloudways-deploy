Configuration
Change the following in .github/workflows/deploy.yml
- uses: ./.github/actions/test_deploy-action 
folder name will be “repositoryName-action”

Also rename the folder testdeploy-action inside .github to your-repositoryname-action

1. SSH_PRIVATE_KEY [required]
Private key part of an SSH key pair. The public key part should be added to the authorized_keys file on the server that receives the deployment.

More info for SSH keys: https://www.ssh.com/ssh/public-key-authentication

The keys should be generated using the PEM format. You can use this command

ssh-keygen -m PEM -t rsa -b 4096

Install the generated public key to cloudways dashboard in

https://platform.cloudways.com/server/serverId/access_detail
in SSH PUBLIC KEYS



Then add your private key to GITHUB
settings/secrets/actions and name it SSH_KEY

2. SSH_HOST [required]
eg: ip address or host name

3. SSH_USERNAME [required]
eg: username for ssh

4. SSH_PORT (optional, default ‘22’)
eg: ‘59184’

5. ARGS (optional, default ‘-rltgoDzvO’)
For any initial/required rsync flags, eg: -avzr --delete

6. SOURCE (optional, default ‘’)
The source directory, path relative to $GITHUB_WORKSPACE root, eg: dist/

7. TARGET (optional, default ‘/home/REMOTE_USER/’)
The target directory

8. EXCLUDE (optional, default ‘’)
path to exclude separated by , ie: /dist/, /node_modules/