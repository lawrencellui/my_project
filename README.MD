# TeraData Code Challenge

This repo contains a cloudformation template that satisfies the requirements of the code challenge.

3 Web Servers (2 Apache, 1 NGINX) will be deployed in 3 different availability zones in us-west-2 behind a classic elastic load balancer with SSL termination.

*Note the SSL certificate is self-signed and is already uploaded to aws AMI.  A browser warning will pop-up when accessing the https endpoint on the loadbalancer*

### Prerequisites
Install aws cli and configure your client with your aws_access_key_id and aws_secret_access_key.

Please use the ssh key that was emailed from me to access the 3 instances.  The default name of the ssh key being used is "td-key"

*Note - Please enter in "us-west-2" for the default region when configuring*

```
pip install awscli
aws configure
```

### Deploying
The following command will deploy the webstack.

```
aws cloudformation create-stack --stack-name webstack --template-body file://webstack.json
```

Wait for the stack to be built (audible bell when finished).
```
aws cloudformation wait stack-create-complete --stack-name webstack && echo -e '\a'
```

To get the various DNS names and IP address of the resources deployed.
```
 aws cloudformation describe-stacks --stack-name webstack
```
*Note - It may take a few minutes for the DNS name of the ELB to propagate out.  The URL endpoints may not work immediately.*

## Authors

* **Lawrence Lui** - *lawrencellui@gmail.com*
