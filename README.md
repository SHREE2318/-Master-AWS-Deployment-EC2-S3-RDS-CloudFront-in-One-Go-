# 🚀 Master AWS Deployment: EC2, S3, RDS & CloudFront in One Go!

This project demonstrates a full-stack deployment on AWS where you build and host a secure file upload system using:

✅ **Amazon EC2** (Web Server)  
✅ **Amazon S3** (File Storage)  
✅ **Amazon RDS** (Database)  
✅ **Amazon CloudFront** (Content Delivery)

---

## 🧠 Project Highlights

- 🖥️ **Web Form** hosted on EC2 using NGINX + PHP
- 📸 **Image Uploads** stored securely in S3
- 🔒 **Data Storage** using MySQL on Amazon RDS
- ⚡ **Optimized Delivery** with CloudFront Distribution
- 🔐 IAM credentials (recommended) used for secure access

---

## 🛠️ Step-by-Step Setup

### 1️⃣ Launch an EC2 Instance
- Choose AMI & instance type
- Configure security groups and key pairs

### 2️⃣ Install Packages
```bash
sudo yum install -y nginx php php-fpm mariadb-server
sudo systemctl start nginx php-fpm mariadb
sudo systemctl enable nginx php-fpm mariadb

3️⃣ **Create Upload Form**  
Place `form.html` in `/usr/share/nginx/html/` with file input.

4️⃣ **Uploads Directory**  
```bash
sudo mkdir /usr/share/nginx/html/uploads
sudo chmod 777 /usr/share/nginx/html/uploads
```

5️⃣ **Create `upload.php` Script**  
• Integrate S3 and CloudFront  
• Add RDS connection details  
• Upload image to S3, store URL in RDS

6️⃣ **RDS Setup**  
• MySQL DB (Free Tier)  
• Configure username/password  
• Allow EC2 access to DB via security groups

7️⃣ **MySQL Table**
```sql
CREATE DATABASE uploads;
USE uploads;
CREATE TABLE images (id INT AUTO_INCREMENT PRIMARY KEY, image_url VARCHAR(255));
```

8️⃣ **Create S3 Bucket**  
• Enable ACL and allow public access  
• Copy bucket name for use in PHP script

9️⃣ **Setup CloudFront**  
• Origin: Your S3 bucket  
• Get distribution URL and use in your app

🔟 **Install AWS SDK**  
```bash
cd /usr/share/nginx/html/
composer require aws/aws-sdk-php
```

## ✅ Test the App
Open in browser: `http://<EC2_IP>/form.html`  
→ Upload an image and confirm it's saved to S3 and shown using CloudFront.

## 📌 Result
You’ve deployed a full-stack cloud app using AWS best practices. Great to show during interviews or on your LinkedIn!

---

### 👨‍💻 Author: Shreehari Shelar
Cloud Intern @ Cravita Technologies  
📎 [LinkedIn](https://linkedin.com/in/shreehari-shelar) | 🐙 [GitHub](https://github.com/shreehari2003)

