# Deploying a Static Website using Docker and NGINX on a Cloud VM

In this project, I will be deploying a static site using containerized Nginx server.

## Prerequisites

- A cloud VM (AWS EC2, Azure VM, GCP VM, etc.)
- Docker installed on your virtual machine
- Basic understanding of Docker and Nginx

## Objectives

- Deploy a static website using Docker and Nginx on a cloud VM.
- Ensure the website is accessible via the VM's public IP address.

## Project Structure

```
ks-portfolio/
    ├── images
    ├── Dockerfile
    ├── index.html
    ├── Jenkinsfile
    ├── README.md
    ├── script.js
    └── styles.css
```

## Architecture

![static-site](./static-site.png)

## Steps to Run the Project

1. Choose the cloud provider
   - Start with free trial account
2. Create a VM
   - Ubuntu 24.04 LTS
   - 1–2 vCPU | 2–4 GB RAM
   - Allow HTTP (Port 80)
   - SSH into the VM
3. Install Docker on the VM
   - Update, upgrade packages and install Docker
   - Verify Docker version & service status
4. Clone the repository
   git clone https://github.com/ksubramanyeshwara/ks-portfolio.git
   cd ks-portfolio
5. Run docker container
   - > /usr/share/nginx/html: Nginx default directory to serve static files
   ```sh
   docker run -d \
   > --name ks-portfolio \
   > -p 80:80 \
   > -v /home/ubuntu/ks-portfolio:/usr/share/nginx/html \
   > nginx
   ```
6. Verify container status
   - `docker ps`
7. Access the static site
   http://<public-ip>

## Outcome

- The static website is successfully deployed and accessible via the VM's public IP address.

## Resources

- [Docker Documentation](https://docs.docker.com/)
- [Nginx Documentation](https://nginx.org/en/docs/)

### Author

- [K Subramanyeshwara](https://github.com/ksubramanyeshwara) - Devops and Cloud Engineer.
