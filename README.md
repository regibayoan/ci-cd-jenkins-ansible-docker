# ci-cd-jenkins-ansible-docker
This pipeline consists of 3 separate EC2 instances 
1. Jenkins Server
2. Ansible Control Node
3. Docker Host

Workflow:
- Jenkins pulls the code from GitHub when there is a code commit
- Jenkins builds an artifact 
- This artifact is copied into Ansible Control Node
- Ansible Control Node runs two playbooks
- The first playbook is for building a Docker image  with the artifact and pushes the Docker image to Docker Hub. 
- The second playbook is deployed to target nodes to spin up a container with the new Docker image (Docker Host in this scenario)
- Docker Host spins up a container. This EC2 instance is where the application is accessed

Future Improvements:
- Add Kubernetes to the workflow to orchestrate containers to have a  highly available and fault tolerant application
- Add Terraform scripts to Jenkins pipeline to provision the architecture
