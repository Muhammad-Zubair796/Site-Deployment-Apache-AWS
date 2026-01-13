

```markdown
# AWS Static Website Deployment Demo

This project demonstrates how to host a high-performance static website using an **Apache Web Server** on an **AWS EC2 (Ubuntu)** instance. 

## 🚀 Live Demo
**Public IP:** [http://13.49.148.165](http://13.49.148.165)

## 🛠️ Project Architecture



The deployment follows a standard cloud architecture:
1.  **Provider:** Amazon Web Services (AWS)
2.  **Compute:** EC2 Instance (Ubuntu 24.04 LTS)
3.  **Web Server:** Apache2 (`httpd` equivalent)
4.  **Security:** Inbound Rules configured for Port 80 (HTTP)

```
## 📋 Steps Taken for Deployment
### 1. Repository Cleanup
* Renamed default branch to `main`.
* Force-pushed a clean "Initial Project Upload" to GitHub.

### 2. EC2 Environment Setup
Connected via SSH to the Ubuntu instance and prepared the environment:
```bash
sudo apt update
sudo apt install apache2 -y

```

### 3. Website Deployment

Moved the website files from the project directory to the Apache root:

### What is Apache?
Think of Apache as a receptionist for your computer.

Normally, your files just sit on your hard drive. If someone from the internet tries to visit your IP address, your computer doesn't know what to show them. Apache is a piece of software (a Web Server) that listens for incoming requests from the internet. When someone types in your IP address, Apache "wakes up," finds your website files, and sends them back to the visitor's browser.


### Why move the files to the "Apache Root" (/var/www/html)?
When you install Apache on Ubuntu, it is pre-configured to look in one specific "folder" for the website it needs to show. This folder is called the Document Root.

Here is why we move them:

Standardized Security: The folder /var/www/html is specially protected. Apache is given permission to read files from there, but not necessarily from your private user folder (/home/ubuntu/AWSDemo). If you keep your files in your home folder, Apache might get a "Permission Denied" error.

Configuration: By default, Apache is "pointing" at /var/www/html. If you want to keep your files in your home folder instead, you would have to manually edit complex configuration files (Virtual Hosts) to tell Apache to look somewhere else.

Automation: Most Linux tools and scripts expect web files to be in the standard /var/www directory.

```bash
# Remove default Apache index page
sudo rm /var/www/html/index.html

# Copy project files to web root
sudo cp -r ~/AWSDemo/* /var/www/html/

# Set correct permissions
sudo chown -R www-data:www-data /var/www/html
sudo chmod -R 755 /var/www/html

```

### 4. Infrastructure Configuration

* **Security Groups:** Configured Inbound Rules in the AWS Console to allow **HTTP (Port 80)** traffic from `0.0.0.0/0`.
* **Verification:** Used `curl -I localhost` to confirm the server status (200 OK).


## 📂 Project Structure

* `index.html` - Main entry point of the website.
* `/assets` - CSS and Javascript files.
* `/images` - Graphic assets for the UI.
* `/error` - Custom error pages.


## 👤 Author
**Muhammad Zubair**
* GitHub: [@Muhammad-Zubair796](https://www.google.com/search?q=https://github.com/Muhammad-Zubair796)



