## Per Scholas DevOps Case Study Information ##
This is a project aimed to build a working CI/CD pipeline with the following tools: Git, Jenkins, Docker, Kubernetes, and Ansible. 

## Installing and Configuring Jenkins on AWS  ##
**Step 1 : Set up Prerequisites (make sure to have ver JDK 1.8+)**

Follow the documentation below on how to setup an account and create an EC2 instance: <br>

1. Sign up for AWS and create and IAM user name and password <br>[https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html "Documentation") [https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html "IAM User Steps")

**Step 2 : Launch an EC2 Instance**
  
1. Launch a EC2 Instance to host Jenkins.
2. Create a Security Group <br>[https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/working-with-security-groups.html#creating-security-group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/working-with-security-groups.html#creating-security-group "create security group")

**Step 3 : Install and Configure Jenkins**

1. Check your version of java or install with:<br> `sudo yum install java-1.8.0`
2. Ensure your packages are up to date <br> `sudo yum update -y`
3. Download and Install Jenkins following the documentation here: <br> [https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos](https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos "jenkins installation docs")

4. Start the Jenkins service and check the status <br> Run `sudo service jenkins start` and then `sudo service jenkins status` <br> If there is an output similar to the image below then Jenkins is running!
![](https://i.imgur.com/zJ678Pl.png)

5. Now finally using the IP address of the instance followed by `8080` You should see the **Getting Started** screen for Jenkins. 

**Note : Before running the Jenkins, make sure your 8080 port is available. Another option is running Jenkins on a different port. Inside the configuration file located /etc/sysconfig/jenkins just change JENKINS_PORT. (The location in Debian based linux is /var/default/jenkins)**

**Jenkins Integration with Github Webhooks**
-
Following the documentation here: [https://plugins.jenkins.io/github/](https://plugins.jenkins.io/github/ "webhook") and [https://medium.com/faun/triggering-jenkins-build-on-push-using-github-webhooks-52d4361542d4](https://medium.com/faun/triggering-jenkins-build-on-push-using-github-webhooks-52d4361542d4 "github webhooks")

1. Ensure Git is installed on the EC2 instance by running `sudo yum install git -y`  
2. From the **Github** repository go to Settings -> Webhooks -> Add webhook
3. In the 'Payload URL' field, past the Jenkins environment URL. At the end of the URL add `/github-webhook/`. In the 'Content type' select `application/json` and leave the 'Secret' field empty. 
4. Under 'Which events would you like to trigger this webhook?' choose 'Let me select individual events'. For this example I used 'Pull Requests' and 'Pushes'. Make sure 'Active' is checked at the bottom. 
5. From **Jenkins** create a new project and click on the Source Code Management tab.
6. Click on Git and paste in your Github repository URL in 'Repository URL' field. 
7. Click on the Build Triggers tab, then on the 'Github hook trigger for GITScm polling' and Save!