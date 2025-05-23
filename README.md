
# AWS Full-Stack Infrastructure Provisioning with Terraform

This project provisions a complete cloud infrastructure using **Terraform** on AWS. It includes:
- EC2 instance setup with Apache, PHP, Git
- Security group configuration
- EBS volume creation and attachment
- Web app deployment from GitHub
- S3 bucket creation with public access and object upload
- CloudFront distribution to serve static assets globally
- HTML auto-generation with image embedding
- Local browser launch with the public webpage

## 🔧 Technologies Used

- AWS (EC2, S3, EBS, CloudFront, Security Groups)
- Terraform
- Apache + PHP (for web server setup)
- Git (for code cloning)

---

## 🛠️ Infrastructure Overview

### ✅ 1. Provider Configuration
```hcl
provider "aws" {
  profile = "jayanth"
  region  = "ap-south-1"
}
```

### ✅ 2. EC2 Instance & Security Group
- Launches a `t2.micro` EC2 instance with SSH and HTTP access.
- Automatically installs Apache, PHP, Git.
- Connects to instance using `.pem` key.

### ✅ 3. EBS Volume
- Attaches a 1GB EBS volume to the EC2 instance.
- Formats, mounts it, and clones a GitHub repo into `/var/www/html`.

### ✅ 4. S3 Bucket + Image Upload
- Creates an S3 bucket (`mybucket41`).
- Uploads an image (`hybrid.jpg`) to the bucket.

### ✅ 5. CloudFront
- Distributes S3-hosted image globally using CloudFront.
- Dynamically injects the image URL into an HTML file on the EC2 instance.

### ✅ 6. Automation
- Auto-opens the deployed webpage (`cloud.html`) in Chrome post-deployment.

---

## 📷 Demo Page Structure

HTML served on EC2 (`cloud.html`):

```html
<img src="https://<CloudFront-Domain>/hybrid.jpg" height="459" width="612">
```

---

## ✅ Outputs

- `bucketid`: S3 bucket name
- `myos_ip`: EC2 instance public IP
- `os_out`: Availability Zone

---

## 🚀 To Run This Project

1. Install [Terraform](https://developer.hashicorp.com/terraform/install)
2. Configure AWS CLI with a profile named `jayanth`
3. Place your `saikey.pem` key and `hybrid.jpg` in the specified path
4. Run the following commands:

```bash
terraform init
terraform apply -auto-approve
```

---

## 👨‍💼 Recruiter Note

This project showcases:
- Proficiency in **Infrastructure as Code (IaC)** with Terraform
- Strong grasp on **AWS cloud provisioning**
- **End-to-end automation** using `remote-exec`, `local-exec`, and shell scripting
- Hands-on with **real-world deployment**, web hosting, storage, and CDN distribution

---

## 📬 Author

**Sai Jayanth Rajamahendram**  
_Cloud | DevOps | Full Stack Engineer_
