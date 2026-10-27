# Task 3: Infrastructure as Code (IaC) with Terraform

## 📌 Project Overview

This project demonstrates Infrastructure as Code (IaC) by using Terraform to provision and manage a Docker container.

Terraform manages the Docker image and container through the Docker provider. The Nginx container is configured to expose port `80` internally and port `8080` on the host.

## 🎯 Objectives

- Understand Infrastructure as Code (IaC).
- Configure the Terraform Docker provider.
- Provision a Docker image and container using Terraform.
- Inspect infrastructure changes using `terraform plan`.
- Manage infrastructure state using Terraform.
- Clean up resources using `terraform destroy`.

## 🛠️ Technologies Used

- Ubuntu Linux
- Terraform
- Docker
- Nginx
- Git and GitHub

## 📂 Project Structure

```text
devops-task-03-terraform-iac/
├── main.tf
├── .gitignore
├── .terraform.lock.hcl
├── README.md
├── terraform-plan.log
├── terraform-state.log
├── docker-containers.log
└── nginx-response.html
```

## ⚙️ Terraform Configuration

The `main.tf` file defines:

- **Docker provider:** Connects Terraform to Docker.
- **Docker image resource:** Manages the `nginx:alpine` image.
- **Docker container resource:** Creates a container named `terraform-nginx`.
- **Port mapping:** Maps host port `8080` to container port `80`.

## 🚀 Implementation Steps

### 1. Initialize Terraform

```bash
terraform init
```

Downloads the required provider and initializes the working directory.

### 2. Validate Configuration

```bash
terraform validate
```

Checks the Terraform configuration for syntax and structural errors.

### 3. Review the Execution Plan

```bash
terraform plan
```

Shows the proposed infrastructure changes before applying them.

### 4. Provision Infrastructure

```bash
terraform apply
```

Review the plan and type `yes` when prompted to create the resources.

### 5. Verify the Container

```bash
docker ps
```

### 6. Test the Nginx Application

```bash
curl http://localhost:8080
```

### 7. Inspect Terraform State

```bash
terraform state list
```

Expected managed resources:

```text
docker_container.web
docker_image.nginx
```

## 🧹 Cleanup

To remove the Terraform-managed resources when the project is complete:

```bash
terraform destroy
```

Review the proposed changes and type `yes` when prompted.

The Docker image is configured with `keep_locally = true`, so it is intended to remain locally after Terraform destroys the image resource.

## 🔐 Security

- Terraform state files are excluded from Git tracking.
- The `.terraform/` working directory is excluded from Git tracking.
- The `.terraform.lock.hcl` file should be committed to record the selected provider versions.
- Do not commit credentials, access tokens, or other secrets.

## 📚 Key Learnings

- Infrastructure can be defined and managed through code.
- Terraform providers connect Terraform to infrastructure platforms.
- `terraform plan` previews changes before execution.
- Terraform state records the resources managed by Terraform.
- Terraform can create and destroy infrastructure consistently.

## 👨‍💻 Author

DevOps Internship — Task 3
