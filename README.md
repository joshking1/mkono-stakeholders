This is the dream
Ubuntu + Nginx Deployment (Dead Simple)
Step 1: Download the HTML file
Download mkono_20m_exit_roadmap.html from this conversation to your local computer.

Step 2: Upload to EC2
bashscp -i /path/to/your-key.pem mkono_20m_exit_roadmap.html ubuntu@your-ec2-public-ip:/home/ubuntu/
Replace:

/path/to/your-key.pem → Your EC2 SSH key path
your-ec2-public-ip → Your EC2 public IP


Step 3: SSH into EC2
bashssh -i /path/to/your-key.pem ubuntu@your-ec2-public-ip

Step 4: Install Nginx
bashsudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx

Step 5: Move file to web root
bashsudo mv mkono_20m_exit_roadmap.html /var/www/html/
sudo chmod 644 /var/www/html/mkono_20m_exit_roadmap.html
Optional: Make it your homepage
bashsudo cp /var/www/html/mkono_20m_exit_roadmap.html /var/www/html/index.html

Step 6: Access your site
Open browser:

Direct file: http://your-ec2-public-ip/mkono_20m_exit_roadmap.html
Homepage (if you ran optional command): http://your-ec2-public-ip


Security: Open Port 80
In AWS Console → EC2 → Security Groups → Your instance's security group:
Add Inbound Rule:

Type: HTTP
Port: 80
Source: 0.0.0.0/0
