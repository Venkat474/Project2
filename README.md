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
`CI-JOB` Any change in the github repository will trigger the job , Jenkins will pull the code from the github repository & it will build the artifact using the maven & it will push the artifact to the Ansible server ,on the Ansible server we are having the Docker installed & Ansible server will create the docker image using the artifact & then it will copy that Docker image to the Docker .
once CI job is completed it will automatically trigger the CD job 
`CD-JOB` Here we are having boost type server from where we will operate the Kubernetes it will pull the docker image from the docker hub & it will build the container over the Kubernetes which is our AWS EKS in this sceneraio .
Once our CI-CD Job is completed we have our application ready 

