FROM amazon/aws-for-fluent-bit:latest
RUN yum -y update
WORKDIR /fluent-bit/configs
COPY parse-nginx.conf .
