#!/bin/bash
# Update the system
yum update -y

# Install EPEL repository (required for stress or stress-ng)
yum install -y epel-release

# Install stress and httpd (Apache HTTP Server)
yum install -y stress httpd

# Start the httpd service
systemctl start httpd
systemctl enable httpd

# Get the hostname
HOSTNAME=$(hostname)

# Create an HTML file with the hostname and stress status
echo "<html><body><h1>EC2 Instance CPU Stress Test</h1><p>Hostname: $HOSTNAME</p><p>CPU Stress Test Running...</p></body></html>" > /var/www/html/index.html

# Stress the CPU by using 4 cores for 10 minutes (600 seconds)
stress --cpu 4 --timeout 600s &

# Optionally, stress-ng can be used instead of stress:
# yum install -y stress-ng
# stress-ng --cpu 4 --timeout 600s &

# Restart httpd to serve the new page
systemctl restart httpd
