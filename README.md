# CodeDeployGitHubDemo
This is a tutorial how to use AWS CodeDeploy to automate deployment of code from Github to an Apache webserver in an AWS EC2 instance.
![CodeDevploy](images/codedeploy_flow.jpg)

## 1. Setup the required Roles
i. MyCodeDeployServiceRole
   This is the role use by CodeDeploy to do its work
   1. Go to https://console.aws.amazon.com/iam/
   2. Access Management -> Roles -> Create role
   3. Trusted Entity Type = AWS Service , Common Use Cases = EC2, Use Cases For Other AWS Services = CodeDeploy-> Next
   4. Ensure the policy is AWSCodeDeployRole -> Next
   5. Enter Role Name = MyCodeDeployServiceRole -> Create Role

ii. CodeDeployInstanceRole
    This is the role use by EC2 instance to do its work


## 2. Setup the target( An EC2 with Amazon Linux as OS)
i. Setup EC Instance
1. Goto  https://console.aws.amazon.com/ec2/
2. Launch Instances -> Amazon Linux 2 AMI 64-bit(x86)
3. Next - > Configure Instance Details
4. 

2. Take note of the region

![region](images/aws-ec2-region.jpg)

3. Install Code Deploy Agent prerequisites
```sh
sudo yum update
sudo yum -y install ruby wget
```

5. Set the region. Get from step #2. In this example the region is *ap-southeast-1*
```sh
export MYREGION=ap-southeast-1 
```

6. Download the Code Deploy Agent
```sh
wget https://aws-codedeploy-$REGION.s3.$REGION.amazonaws.com/latest/install
```

7. Install the Code Deploy Agent
```sh
chmod +x install
sudo ./install auto
```

8. Check the Code Deply Agent status
```sh
sudo service codedeploy-agent status
```
You shoud get "The AWS CodeDeploy agent is running as PID <SOME PID Number>. If you get *error: No AWS CodeDeploy agent running*, you may start it manually.
```sh
sudo service codedeploy-agent start
```
If you need to check the Code Deploy agent log
```sh
less /var/log/aws/codedeploy-agent/codedeploy-agent.log
```

