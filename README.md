# CodeDeployGitHubDemo
This is a tutorial how to use AWS Code Deploy to deploy code from Github to a Apache webserver in an AWS EC2 instance

## Setup the target( An EC2 with Amazon Linux as OS)
1. Provision EC2 instance

2. Install Code Deploy Agent
```sh
sudo yum update
sudo yum install ruby
sudo yum install wget
```
