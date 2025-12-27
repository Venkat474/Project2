# Project2
# 🔥CI-CD PIPELINE USING JENKINS TO DEPLOY ON KUBERNETES(AKS)
<img width="417" height="232" alt="Capture" src="https://github.com/user-attachments/assets/c8643373-e737-4f44-a865-78917f2cdb94" />


## CI Job

Any change in the **GitHub repository** will trigger the **Jenkins job**.

- Jenkins pulls the code from `GitHub`
- Builds the artifact using `Maven`
- Pushes the artifact to the **Ansible server**
- Ansible server has `Docker` installed
- Docker image is created using the artifact
- Docker image is pushed to `Docker Hub`

Once the **CI Job** is completed, it will **automatically trigger the CD Job**.
## CD Job
- A **Bastion (Jump) Server** is used to operate Kubernetes
- Kubernetes commands are executed from the Bastion server
- Docker image is pulled from `Docker Hub` & it will build the container over K8S which is ours AWS-EKS
- Container is deployed on **Kubernetes**
- Kubernetes cluster used is **AWS EKS**

---

## 🎯 Final Outcome
Once the **CI–CD pipeline** is completed:
- ✅ Application is built
- ✅ Docker image is created
- ✅ Application is deployed on **AWS EKS**
- ✅ Application is ready to use

---

# 1.Install and Configure the Jenkins
**`Go to AWS`** 
<br>➡️ Launch Instances 
<br>➡️ [Name-JENKINS-SERVER] 
<br>➡️ [Application & OS Images- Amazon Linux(Amazon Linux 2 AMI(HVM)-Kernel 5.10,SSD Volume Type(Free Tier Eligible)] 
<br>➡️ [Instance type-t2.micro] 
<br>➡️ [keypair-create new one] 
<br>➡️ LaunchInstance(Copy PublicIPV4adresses)                                                               
<br>**`Go to MobaXterm`** 
<br>➡️ Session 
<br>➡️ SSH 
<br>➡️ Remotehost-pasteIPV4 
<br>➡️ [✔] Specify username-*ec2-user* 
<br>➡️ Advanced SSH Settings 
<br>➡️ [✔]Use private key-Provide private key from downloads → OK                                                              
<br>**`Open Server`** - <br>$ sudo su <br>$ cd ~ <br>*Now we need to download & install jenkins using below .txt link* 🔗https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/  <br> 📄[View JenkinsInstallation.txt](JenkinsInstallation.txt)
## Jenkins Installation
1. Ensure that your software packages are up to date on your instance by using the following command to perform a quick software update: **[ec2-user ~]$** sudo yum update -y
2. Add the Jenkins repo using the following command:
<br> **[ec2-user ~]$** sudo wget -O /etc/yum.repos.d/jenkins.repo \
        https://pkg.jenkins.io/redhat-stable/jenkins.repo
3. Import a key file from Jenkins-CI to enable installation from the package:
   <br> **[ec2-user ~]$** sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
<br> **[ec2-user ~]$** sudo yum upgrade
4. This command enables the EPEL (Extra Packages for Enterprise Linux) repository on Amazon Linux to access and install extra software packages that are not available in the default repositories:
<br> **[ec2-user ~]$** amazon-linux-extras install epel
5. This command is used to install Java (OpenJDK 11) on Amazon Linux for running Java applications:
    <br> **[ec2-user ~]$** sudo amazon-linux-extras install java-openjdk11 -y  <br> ( amazon-linux-extras in above represents → Amazon Linux package manager )
6. Install Java:
**[ec2-user ~]$** sudo yum install java-11-amazon-corretto -y
7. Install Jenkins:
**[ec2-user ~]$** sudo yum install jenkins -y
8. This command enables Jenkins to automatically start on system reboot:
**[ec2-user ~]$** sudo systemctl enable jenkins
9. This command starts the Jenkins service so it begins running:
**[ec2-user ~]$** sudo systemctl start jenkins
10. Verify Java installation :- <br> Java runtime version: **[ec2-user ~]$** java -version
<br> Java compiler version: **[ec2-user ~]$** javac -version
11. This command shows whether Jenkins is running or not:  **[ec2-user ~]$** systemctl status jenkins

<br>*Now we need to change the hostname of the server using below link*
<br> 📄[view ChangeHostname.txt](ChangeHostname.txt)
<br>(**Actually jenkins works on the port 8080 so wee need to do the changes as shown below**)                                                                      
<br>**`Go to EC2`** 
<br>➡️ Security 
<br>➡️ security groups 
<br>➡️ EditInboundrule 
<br>➡️ Add rule 
<br>➡️ Portrange-8080 
<br>➡️ Source-AnywhereIPV4 → SaveRules
<br> 🚀 **`Jenkins setup on EC2 Instance`** Copy Public IPV4 address & paste it in new tab as shown [ 43.205.115.156:8080 ] now copy [var/lib..../initialAdminPassword] 
-`Go to server`  
<br>          $ sudo su 
<br>          $ cat paste (now copy the password and paste in jenkins tab(Administrator password)) -> Continue 
<br>➡️ Customize Jenkins → Install suggested plugins 
<br>➡️ create admin user → Save and Continue 
<br>➡️ JenkinsURL → Save and Finish → Start using Jenkins.   
# 2.Install and Configure the Maven 
**`Go to remote terminal of my jenkins server`** 🔗https://maven.apache.org/download.cgi and go to this link [Binary tar.gz archive → apache-maven-3.9._-bin.tar.gz] Copy link address <br> 📄 [View MavenInstallation.txt](MavenInstallation.txt) 
# 3.Ansible Server Setup and Ansible Installation
**`Go to EC2`** ➡️ Launch Instances ➡️ [Name-Ansible-Server] ➡️ [Application & OS Images- Amazon Linux(Amazon Linux 2 AMI(HVM)-Kernel 5.10,SSD Volume Type(Free Tier Eligible)] ➡️ [Instance type-t2.micro] ➡️ [keypair-Select existing one] ➡️ LaunchInstance ➡️ Security ➡️ security groups ➡️ EditInboundrule ➡️ Add rule ➡️ Portrange-8080-8090 ➡️ Source-AnywhereIPV4 ➡️ SaveRules (Copy PublicIPV4adresses) 
<br>**`Go to MobaXterm`** ➡️ Session ➡️ SSH ➡️ Remotehost-pasteIPV4 ➡️ [✔] Specify username-*ec2-user* ➡️ Advanced SSH Settings ➡️ [✔]Use private key-Provide private key from downloads ➡️ OK    <br>*Now we need to change the hostname of the server using below link*  <br>📄 [view CHANGEHostname.txt](CHANGEHostname.txt)

