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
