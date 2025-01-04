# AltSchool Second Semester Examination Cloud Project - Joseph Ibeh


## Introduction

Welcome to my Cloud Engineering Second Semester Examination documentation. In this project, I successfully provisioned a Linux server, installed a web server (Apache), deployed a simple HTML landing page, and configured networking to allow HTTP traffic. The project showcases my journey in creating a web application prototype and highlights key skills in server management and web deployment.



## Objective

The main objective of this project is to:

1. Provision a Linux server using AWS.
2. Install and configure a web server (Apache) to serve web content.
3.Create a simple HTML landing page that includes "your name, a project title such as Welcome to [Your Name] Landing Page, a brief description of your project, and your full bio with all the interesting information about you".
4. Configure networking to allow HTTP traffic (port 80) and optionally HTTPS traffic (port 443).
5. Provide a public IP address or domain name for external access to the web page.



## Tools and Technologies

- **Cloud Platform**: AWS (Amazon Web Services)
- **Linux Distribution**: Ubuntu
- **Web Server**: Apache
- **SSH**: For server management and connection
- **HTML**: For creating web content
- **Certbot**: For managing SSL certificates (Optional for HTTPS configuration)



## Server Provisioning

### Objective:
To set up a Linux server using AWS for a web application prototype.

### Steps:

1. **Sign in to AWS**:
   - Visit [AWS Management Console](https://aws.amazon.com/console/).
  
2. **Create a New Instance**:
   - Click on "EC2" in the AWS console.
   - Choose a Linux distribution (e.g., Ubuntu 22.04 ).
   - Configure instance settings, ensuring a public IP is assigned.

![Aws sign in ](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/aws-log-in.png)

![create instance](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/instance-launch-instance.png)

![server name](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/server-name.png)

![choose linux distribution, ubuntu AMI](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/AMI-Ubuntu.png)


3. **Configure Key Pair**:
   - Create a new key pair (download the private key for future SSH access).
  
![Key pair](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/key-pair.png)


4. **Create Security Group**:
   - Allow HTTP & HTTPS traffic on port 80, 443 and SSH on port 22.

![Network Security group](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/network-security-group.png)

5.  Launch Instance.

![Launch Instance](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/launch-instance.png)

![Instance running](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/instance-running.png)
   

6. **Connect to the Server**:
   - Use SSH to connect to the server using the private key:
     ```bash  
     ssh -i [path_to_private_key] ubuntu@[public_ip_address]  
     ```
![Connect](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/click-connect.png)

![connect](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/ssh-client.png)


## Web Server Setup

### Objective:
To set up a web server to serve web content.

### Steps:

- **ssh to your gitbash CLI**

 ```bash  
     ssh -i [path_to_private_key] ubuntu@[public_ip_address]  
 ```

  ![ssh CLI](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/terminal-ssh-in.png)

- **Switch to root user**

![root user](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/switch-to-sudoer.png)
  
1. **Update and Install Apache**:
   ```bash
   sudo apt update
   sudo apt install apache2 -y

   ```

2. **Start Apache Service**

  ```bash
   sudo systemctl start apache2
   sudo systemctl enable apache2
```

![update,  install, start apache2](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/sudo-apt-install-apache....png)

3. **Check Web Server:**

Open a web browser and visit the server’s public IP address to confirm Apache is working.


## HTML Page Deployment
Objective:
Create and deploy a simple HTML page on the server.

### Steps:
1. Create HTML File:

```bash
sudo vim /var/www/html/index.html
```


2. Add the HTML Content:

The content of HTML page

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Welcome to Joseph Ibeh Landing Page</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background-color: #f4f4f9;
        color: #333;
        line-height: 1.6;
      }
      header {
        background: #007bff;
        color: #fff;
        padding: 10px 0;
        text-align: center;
      }
      header h1 {
        margin: 0;
      }
      .container {
        padding: 20px;
        max-width: 800px;
        margin: 0 auto;
        background: #fff;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        border-radius: 8px;
      }
      h2 {
        color: #007bff;
      }
      p {
        margin: 10px 0;
      }
      footer {
        text-align: center;
        padding: 10px 0;
        margin-top: 20px;
        background: #f1f1f1;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Welcome to Joseph Ibeh Landing Page</h1>
    </header>
    <div class="container">
      <h2>Name</h2>
      <p>Joseph Ibeh</p>

      <h2>Project Title</h2>
      <p>Welcome to Joseph Ibeh Landing Page</p>

      <h2>Project Description</h2>
      <p>
        This project demonstrates my ability to provision a Linux server and
        deploy a web application to showcase my cloud engineering capabilities.
      </p>

      <h2>Biography</h2>
      <p>
        Joseph Ibeh, hailing proudly from the vibrant community of Ichida in
        Anambra State, is a relentless individual with a clear vision for his
        academic and professional journey. He holds a Bachelor's Degree from the
        University of Jos, and his Master's Degree at Nnamdi Azikiwe University
        where he graduated with a distinction of CGPA of 4.86. His journey
        epitomizes resilience, ambition, and an unyielding commitment to
        academic excellence. Never one to rest on his laurels, Joseph is also
        enrolled in Altschool Africa, diving deep into Cloud Engineering. This
        multifaceted pursuit not only highlights his adaptability but also his
        drive to stay at the forefront of technological advancements.
      </p>

      <p>
        In addition to his academic pursuits, Joseph serves as President of the
        School of Engineering at AltSchool Africa. In this role, he fosters a
        collaborative and supportive environment for students, promoting
        academic excellence and innovative thinking. Furthermore, he contributes
        as a Campus Ambassador for AltSchool Africa at Nnamdi Azikiwe
        University, where he engages with students to promote tech education,
        innovation, and leadership within the tech community.
      </p>

      <p>
        Joseph's technical journey has led him to explore various areas,
        including a passion for technical writing. As a guest blogger on
        <a href="https://dev.to/josephibehdev" target="_blank">Dev.to</a>, he
        creates insightful content aimed at demystifying Cloud & DevOps
        concepts, ensuring that they are accessible to a broad and diverse
        audience. Additionally, he's been featured on Coder Legion, where he
        contributes guest posts to their programming community, sharing
        knowledge and insights with aspiring developers.
      </p>

      <p>
        Joseph Ibeh joined AltSchool Africa because of his deep passion for
        technology. He has always been fascinated by how technology can
        transform lives and create endless possibilities. Altschool School of
        Engineering is the perfect platform for him to enhance his skills and
        knowledge in the tech industry. His goal for the School of Engineering
        is to become an excellent and exceptional Cloud & DevOps engineer in the
        nearest future, capable of solving complex problems and empowering the
        next generation by educating them about essential tech skills.
      </p>

      <p>
        With his growing expertise in Cloud & DevOps Engineering, Joseph aims to
        design scalable systems, optimize processes, and continue making
        meaningful contributions to the tech ecosystem.
      </p>
    </div>
    <footer>
      <p>&copy; 2024 Joseph Ibeh | Cloud & DevOps Engineer</p>
    </footer>
  </body>
</html>

![html content](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/html-content-sudo%20vim-var-www-html-index.html.png)

![html content contd](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/html-content-contd.png)


3. Open a web browser and visit http://52.90.54.214 to Confirm Server is Accessible:

![web content](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/landing-page-1-ns.png)

![web content contd](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/landing-page-2-ns.png)

![web content contd](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/landing-page-3-ns.png)


## Configuring HTTPS

Prerequisite
- Purchase a domain name:
- Purchased a domain name (e.g., josephibeh.me) from domain registrars like Namecheap or another trusted domain registrar.
- Update DNS Settings:
-  Log into your domain registrar’s dashboard.
-  Navigate to DNS settings.
- Add a new A record with your IP (Public IP Address from your server).

![dormain name namecheap](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/setting-up-DNS-namecheap.png)

### Steps:
1. Install Certbot:
```bash
   sudo apt install certbot python3-certbot-apache -y
```

2. Obtain SSL Certificate:

```bash
   sudo certbot --apache -d josephibeh.me -d www.josephibeh.me
```
![certbot ](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/sudo-cert-bot-certificate.png)

- **Open a web browser and visit https://josephibeh.me to Confirm Server is Accessible:**

![secured page 1 ](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/landing-page-1-sec.png)

![secured contd 3 ](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/landing-page-2-sec.png)

![secured contd 3 ](https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project/blob/main/images/landing-page-3-sec.png)

## Deliverables
  
- **secured dormain**: [https://josephibeh.me]
- **Git Repository**: [https://github.com/Joseph-Ibeh/AltSchool_Second_Semester_Cloud_Project]
- **Documentation with a snapshot as shown above.**
