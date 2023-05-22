# Custom AWS Fluentbit image for Nginx

## Prepare parse-nginx.conf file

```txt
[SERVICE]
    Parsers_File /fluent-bit/parsers/parsers.conf
    Flush 1
    Grace 30

[FILTER]
    Name parser
    Match *
    Key_Name log
    Parser nginx
    Reserve_Data True
```

## Build custom image

### Dockerfile

```dockerfile
FROM amazon/aws-for-fluent-bit:latest
# update packages
RUN yum -y update
WORKDIR /fluent-bit/configs
COPY parse-nginx.conf .
```

### Build image

```sh
docker build --no-cache -t aws-for-fluent-bit:nginx-latest .
```

### Tag image

```sh
docker tag aws-for-fluent-bit:nginx-latest ${ECR_URL}/aws-for-fluent-bit:nginx-latest
```

## Push image

### Get login

*Make sure aws cli is installed and aws credentials file is configured*

```sh
aws ecr get-login-password --region ${AWS_REGION} --profile ${AWS_CREDENTIAL_PROFILE} | docker login --username AWS --password-stdin ${ECR_URL}
```

### Push image

```sh
docker push ${ECR_URL}/aws-for-fluent-bit:nginx-latest
```
