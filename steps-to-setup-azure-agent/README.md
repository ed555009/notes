# Steps to setup Azure agent

## EC2 instance

- t3a.small
- 30G EBS GP3
- Amazon linux 2

yum update

```sh
sudo yum update -y
```

## Packages

### Git

```sh
sudo yum install git
```

### Docker

Install

```sh
sudo amazon-linux-extras install docker
```

Start service

```sh
sudo service docker start
```

Set as system service

```sh
sudo systemctl enable docker
```

Add ec2-user to docker group

```sh
sudo usermod -a -G docker ec2-user
sudo usermod -aG docker $USER
```

Check

```sh
docker info
```

### Java

```sh
sudo amazon-linux-extras install java-openjdk11
```

### Mono

```sh
sudo amazon-linux-extras install mono
```

Sync mono CA cert

```sh
curl https://curl.se/ca/cacert.pem > ~/cacert.pem && sudo cert-sync ~/cacert.pem
```

### Agent

Finally, follow the [official guide](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/v2-linux?view=azure-devops) to setup the agent.

## Extra Packages

### Node.js

Install node version manager (nvm)

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

Activate nvm

```sh
. ~/.nvm/nvm.sh
```

Use nvm to install the latest version of Node.js

```sh
nvm install --lts
```

*Amazon Linux 2 does not currently support the current LTS release (version 18.x) of Node.js. Use Node.js version 16.x with the following command instead.*

```sh
nvm install 16
```

Test that Node.js is installed and running correctly

```sh
node -e "console.log('Running Node.js ' + process.version)"
```

AWS Reference: [Tutorial: Setting Up Node.js on an Amazon EC2 Instance](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html)
