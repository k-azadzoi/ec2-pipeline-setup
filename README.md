Please follow the live [document](https://docs.google.com/document/d/17OwlITE-yPWNj3Vi5RtQfz3ItvSkOfnbaVMnzlZyGTg)

## Per Scholas DevOps Case Study Information ##
This is a project aimed to build a working CI/CD pipeline with the following tools: Git, Jenkins, Docker, Kubernetes, and Ansible. 

## Installing and Configuring Jenkins on AWS  ##
**Step 1 : Set up Prerequisites (make sure to have ver JDK 1.8+)**

Follow the documentation below on how to setup an account and create an EC2 instance: <br>

1. Sign up for AWS and create and IAM user name and password <br>[https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html "Documentation") [https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html "IAM User Steps")

**Step 2 : Launch an EC2 Instance**
  
1. Launch a EC2 Instance to host Jenkins.
2. Create a Security Group [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/working-with-security-groups.html#creating-security-group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/working-with-security-groups.html#creating-security-group "create security group")

**Step 3 : Install and Configure Jenkins**

1. Check your version of java or install with:<br> `sudo yum install java-1.8.0`
2. Ensure your packages are up to date <br> `sudo yum update -y`
3. Download and Install Jenkins following the documentation here: <br> [https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos](https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos "jenkins installation docs")

4. Start the Jenkins service and check the status <br> `sudo service jenkins start` <br>  `sudo service jenkins status` <br> If there is an output similar to the image below then Jenkins is running!
![](https://i.imgur.com/zJ678Pl.png)

5. Now finally using the IP address of the instance followed by `8080` You should see the **Getting Started** screen for Jenkins. 










