# CodeDeployGitHubDemo
This is a tutorial how to use AWS Code Deploy to deploy code from Github to a Apache webserver in an AWS EC2 instance

## Setup the target( An EC2 with Amazon Linux as OS)
1. Provision EC2 instance

2. Take note of the region
![region]/image/ec2-aws-region.png

4. Install Code Deploy Agent
```sh
sudo yum update
sudo yum -y install ruby wget
```
