# AltSchool-Exam-Project

## **HOW I PROVISIONED A LINUX SERVER WITH AN HTML PAGE.**


### **Step-by-Step Guide to Setting Up My Server and Landing Page**
**Step 1: Getting the Server Ready**
1. **Log in to AWS**:


I started by logging into my AWS account and heading to the EC2 service.
Launch the EC2 Instance:


I clicked on Launch Instances and picked Ubuntu Server 22.04 LTS as my operating system.
For the instance type, I chose t2.micro, which is free-tier eligible.
Next, I added some storage and set up a security group to allow HTTP (port 80) and SSH (port 22) traffic.
After reviewing everything, I launched the instance and downloaded the private key (.pem file) for secure access.
Connect to the Server:


Using the terminal, I connected to the server with this command:
 ```ssh -i /path/to/your-key.pem ubuntu@<Public_IP_Address>```
I replaced /path/to/your-key.pem with the path to my downloaded key file and <Public_IP_Address> with the server's public IP address.

**Step 2: Setting Up the Web Server**
1. **Update and Install Apache**:


Once logged into the server, I ran these commands to update the system and install Apache:
 sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y

2. **Start Apache**:


To make sure Apache was running, I used:
```sudo systemctl start apache2```
```sudo systemctl enable apache2```

3.**Check Apache**:


I opened my browser and went to http://127.0.1.1 to confirm Apache was working, it was.

**Step 3: Adding My Custom HTML Page**
1. **Create the Page**:


I navigated to Apache's document root:
 ```cd /var/www/html```

Then, I created an index.html file:
```sudo nano index.html```

Inside the file, I added my content:


```<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to Odudu's Landing Page</title>
</head>
<body>
    <h1>Welcome to Odudu's Landing Page</h1>
    <p>This is a prototype for showcasing our startup capabilities.</p>
    <h2>Project Brief</h2>
    <p>The startup helps simplify the funeral process<p>
    <h2>About Me</h2>
    <p>Name: Odudu Udo-Inyang</p>
    <p>BSc in Business Management</p>
    <p>Experience: Banking, Hospitality, Cloud Computing</p>
    <p>Hobbies: Art, Music, Research, Writing</p>
    <h3>Contact</h3>
    <p>Email: martyns.odudu@gmail.com</p>
</body>
</html>
```

2. **Save and Check the Page**:


After saving the file, I refreshed http://127.0.1.1 and saw my custom landing page live!
