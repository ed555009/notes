# Steps to setup Azure agent using Ubuntu

## EC2 instance

- t4g.small for `ARM64`
- t3a.small for `x86_64`
- 30G EBS GP3
- Ubuntu 22.04 LTS

## Packages

### Git

Git is already installed in Ubuntu 22.04, so there is no need to install it.

### Docker

Prepare

```sh
sudo apt-get update

sudo apt-get install -y ca-certificates curl gnupg lsb-release

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install

```sh
sudo apt-get update

sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

Add `current user` to docker group

```sh
sudo usermod -aG docker $(whoami)
```

Check

```sh
docker info
```

### Java

```sh
sudo apt update

sudo apt install openjdk-11-jdk
```

From `sonarqube9.1`, Java `17` is required.

```sh
sudo apt update

sudo apt install openjdk-17-jdk
```

Check

```sh
java -version
```

### Mono

Prepare

```sh
sudo apt install ca-certificates gnupg

sudo gpg --homedir /tmp --no-default-keyring --keyring /usr/share/keyrings/mono-official-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF

echo "deb [signed-by=/usr/share/keyrings/mono-official-archive-keyring.gpg] https://download.mono-project.com/repo/ubuntu stable-focal main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
sudo apt update
```

Install

```sh
sudo apt update

sudo apt install mono-devel

sudo apt install mono-complete
```

### Agent

Finally, follow the [official guide](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/v2-linux?view=azure-devops) to setup the agent.

## Extra Packages

### AWS CLI

Install

```sh
snap install aws-cli --classic
```

Check

```sh
aws --version
```

### Delete dangling docker images (Cron job)

Create bash script at `/home/ubuntu/remove-dangling-docker-images.sh`

```sh
#!/bin/bash
/usr/bin/docker rmi -f $(/usr/bin/docker images -f "dangling=true" -q)
```

Make it executable

```sh
chmod +x /home/ubuntu/remove-dangling-docker-images.sh
```

Create cron job

```sh
crontab -e
```

Add the following line (daily at 00:00)

```sh
0 0 * * * /home/ubuntu/remove-dangling-docker-images.sh
```
