# Project2
# CI-CD PIPELINE USING JENKINS TO DEPLOY ON KUBERNETES(AKS)
🚀 🔥 ✅ ⚠️
- [x] Completed
- [ ] Pending
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
<img width="417" height="232" alt="Capture" src="https://github.com/user-attachments/assets/c8643373-e737-4f44-a865-78917f2cdb94" />

---

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
**`Go to AWS`** ➡️ Launch Instances ➡️ [Name-JENKINS-SERVER] ➡️ [Application & OS Images- Amazon Linux(Amazon Linux 2 AMI(HVM)-Kernel 5.10,SSD Volume Type(Free Tier Eligible)] ➡️ [Instance type-t2.micro] ➡️ [keypair-create new one] ➡️ LaunchInstance(Copy PublicIPV4adresses)                                                                <br>**`Go to MobaXterm`** ➡️ Session ➡️ SSH ➡️ Remotehost-pasteIPV4 ➡️ [✔] Specify username-*ec2-user* ➡️ Advanced SSH Settings ➡️ [✔]Use private key-Provide private key from downloads ➡️ OK                                                                                                                                                 <br>**`Open Server`** - ($ sudo su) ($ cd ~) *Now we need to download & install jenkins using below .txt link* 🔗https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/                            <br> 📄[View JenkinsInstallation.txt](JenkinsInstallation.txt)
<br>*Now we need to change the hostname of the server using below link*
<br> 📄[view ChangeHostname.txt](ChangeHostname.txt)
<br>(**Actually jenkins works on the port 8080 so wee need to do the changes as shown below**)                                                                        <br>**`Go to EC2`** ➡️ Security ➡️ security groups ➡️ EditInboundrule ➡️ Add rule ➡️ Portrange-8080 ➡️ Source-AnywhereIPV4 ➡️ SaveRules                                    <br> 🚀 **`Jenkins setup on EC2 Instance`** Copy Public IPV4 address & paste it in new tab as shown [ 43.205.115.156:8080 ] now copy [var/lib..../initialAdminPassword] , Go to server [$ sudo su] [$ cat paste] now copy the password and paste in jenkins tab(Administrator password) → Continue ➡️ Customize Jenkins → Install suggested plugins ➡️ create admin user → Save and Continue ➡️ JenkinsURL → Save and Finish ➡️ Start using Jenkins.   
# 2.Install and Configure the Maven 
**`Go to remote terminal of my jenkins server`** 🔗https://maven.apache.org/download.cgi and go to this link [Binary tar.gz archive → apache-maven-3.9._-bin.tar.gz] Copy link address <br> 📄 [View MavenInstallation.txt](MavenInstallation.txt) 
# 3.Ansible Server Setup and Ansible Installation
**`Go to EC2`** ➡️ Launch Instances ➡️ [Name-Ansible-Server] ➡️ [Application & OS Images- Amazon Linux(Amazon Linux 2 AMI(HVM)-Kernel 5.10,SSD Volume Type(Free Tier Eligible)] ➡️ [Instance type-t2.micro] ➡️ [keypair-Select existing one] ➡️ LaunchInstance ➡️ Security ➡️ security groups ➡️ EditInboundrule ➡️ Add rule ➡️ Portrange-8080-8090 ➡️ Source-AnywhereIPV4 ➡️ SaveRules (Copy PublicIPV4adresses) 
<br>**`Go to MobaXterm`** ➡️ Session ➡️ SSH ➡️ Remotehost-pasteIPV4 ➡️ [✔] Specify username-*ec2-user* ➡️ Advanced SSH Settings ➡️ [✔]Use private key-Provide private key from downloads ➡️ OK    <br>*Now we need to change the hostname of the server using below link*  <br>📄 [view CHANGEHostname.txt](CHANGEHostname.txt)
