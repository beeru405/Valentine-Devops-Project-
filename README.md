# Valentine-Devops-Project-
![1 8426mE_0P35wQHDeg99olg](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/93ec35aa-fd48-438b-a630-a71ce1eb2c6a)
Hello readers!!!!

In this project, I utilized Docker to containerize my web application, ensuring consistency and portability across different environments. Leveraging Nginx as the web server allowed for efficient handling of web traffic, providing a reliable and scalable solution for serving web content.

Key highlights of the project include:

✅ Dockerizing the web application: Using a Dockerfile, I encapsulated the web server configuration along with my HTML and CSS files, ensuring easy deployment and management.

✅ Setting up Nginx: By configuring Nginx within the Docker container, I was able to efficiently serve static web content while ensuring optimal performance.

✅ Deploying on AWS EC2: Leveraging the power of AWS EC2 instances, I deployed my Dockerized web application, making it accessible over the internet.

So lets start making it…

First Go to your amazon account, then search bar and search ec2 instance.

After that click on Launch instance.

![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/d10faa18-cefe-4a64-96d4-446906655951)

Give your instance a name. Here i have gave Valantine project.

![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/804f8e16-cc00-4c33-81cc-bf9c527cbf88)


Select os image as Ubuntu and ami eligiable for free tier with t2.micro instance.

![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/fdfd2440-97e8-4f24-80ef-d3b438c6bfee)

Click on create new key pair. For best practice. Give key pair a name & download that file.
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/9535552c-234e-4e4c-bf7f-23aa2eb5f78f)

![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/79767f82-3445-4e06-90cb-ea0c38d8dee2)

Allow all trafic like http, https . Then click on Launch Instance.
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/cd400443-4bf9-451a-95a7-6abf3366eac9)

Your instance is ready. Now click on connect after selecting your instance & then again click on connect.
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/236cba9c-31cd-4976-91f9-10d35347cf47)
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/9ca69cf7-7c71-47c6-8d50-e0a45f62faa7)

Login as super user to install different dependencies.
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/d7580a7c-29dc-40ad-8db8-65989c871445)
Now run below command to install git. After that clone the follwoing github repoitory into your instance .

```
sudo apt install git -y
git clone https://github.com/beeru405/Valentine-Devops-Project-.git
```
Now we will install nginx server.

```
sudo apt install nginx -y
```
For check server & start server run below command :
```
systemctl start nginx
systemctl status nginx
```
Now install Docker into your instance by running following command :
```
sudo apt-get install docker.io -y
sudo usermod -aG docker $USER
newgrp docker
sudo chmod 777 /var/run/docker.sock
```
now that’s it. Run below command to make docker image by going inside the directory which we clone from github.
```
cd Valantine-devops-project-
docker build -t valantine-devops .
```
Run below commands to check images and make a container from image in which our server will run.
```
docker images
docker run -d --name devopsproject -p 8081:80 valantine-devops:latest
docker ps
```
To access go to your instance, into security, select security group, click on edit inbound rules.
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/a4191094-0324-41ac-9aec-e32763e0235c)
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/0e9e5615-8051-49b7-a4ad-1ae9c7449dda)

Now click on add rule & give your instance 8081 port access. Select myip for security reasons. even select custom too.
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/b86011ca-86c4-4443-b51a-4caa10221e83)
![image](https://github.com/beeru405/Valentine-Devops-Project-/assets/101712802/36efc167-2b91-4e62-ae67-dcd46c8d8192)

That’s it. Our web page is running on nginx server hosted on ec2 instance. Copy your instance public ip and go for below url:
```
http://<yourinstancepublicip>:8081/yes.html
```
