# AWS CLI in Docker

Containerized AWS CLI on alpine to avoid requiring the aws cli to be installed on CI machines.

## Build

```
docker build -t gendosu/aws-cli .
```

Automated build on Docker Hub

[![DockerHub Badge](http://dockeri.co/image/gendosu/aws-cli)](https://hub.docker.com/r/gendosu/aws-cli/)

## Usage

Configure:

```
export AWS_ACCESS_KEY_ID="<id>"
export AWS_SECRET_ACCESS_KEY="<key>"
export AWS_DEFAULT_REGION="<region>"

alias aws='docker run --rm -t $(tty &>/dev/null && echo "-i") -e "AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID}" -e "AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}" -e "AWS_DEFAULT_REGION=${AWS_DEFAULT_REGION}" -v "$(pwd):/awscli" gendosu/aws-cli'
```

## example

show s3 bucket list

```
aws s3 ls
```

## Maintenance

- The Docker image build & publish is automated by DockerHub for master commits.

## References

AWS CLI Docs: https://aws.amazon.com/documentation/cli/

# License

Copyright 2018-2018 gendosu.
Licensed under the MIT License;
