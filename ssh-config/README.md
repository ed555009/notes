# SSH Config

## Open new config file
```sh
touch ~/.ssh/config
```

## Example
```
Host jumper
	Hostname IP_ADDRESS_OR_DOMAIN_NAME
	User USERNAME
	Port 22
	IdentityFile PATH_TO_PRIVATE_KEY
	StrictHostKeyChecking no
```

## Host that needs to be accessed through jumper
```
Host jumper
	Hostname IP_ADDRESS_OR_DOMAIN_NAME
	User USERNAME
	Port 22
	IdentityFile PATH_TO_PRIVATE_KEY
	StrictHostKeyChecking no

Host target
	Hostname PRIVATE_IP_ADDRESS_OR_DOMAIN_NAME
	User USERNAME
	IdentityFile PATH_TO_PRIVATE_KEY
	StrictHostKeyChecking no
	ForwardAgent yes
	ProxyJump jumper
```
