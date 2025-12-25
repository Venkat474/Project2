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
**Go to AWS** - Launch Instances - [Name-______] - [Application & OS Images- Amazon Linux(Amazon Linux 2 AMI(HVM)-Kernel 5.10,SSD Volume Type(Free Tier Eligible)] - [Instance type-t2.micro] - [keypair-create new one] - LaunchInstance(Copy PublicIPV4adresses)                                                                                                           **Go to MobaXterm** - [Session] - [SSH] - [Remotehost-pasteIPV4] - [[✔] Specify username-*ec2-user*] - Advanced SSH Settings - [[✔]Use private key-Provide private key from downloads] - OK                                                          **Open Server** - (sudo su) (cd ~) *Now we need to download & install jenkins using below link*🔗[https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/]                                        [View main.txt](main.txt)


