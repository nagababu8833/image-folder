# image-folder
```
#!/bin/bash
# Update the package repository
sudo apt update -y

# Install Apache2
sudo apt install apache2 -y

# Enable and start the Apache2 service    
sudo systemctl enable apache2
sudo systemctl start apache2

# Fetch the server's IP address (works for most Linux environments)
IP_ADDRESS=$(hostname -I | awk '{print $1}')

# Create a custom index.html file with server details
cat <<EOF | sudo tee /var/www/html/index.html
<h1>Server Details</h1>
<p><strong>Hostname:</strong> $(hostname)</p>
<p><strong>IP Address:</strong> $IP_ADDRESS</p>
EOF

# Restart Apache2 to load the new configuration
sudo systemctl restart apache2

```

=======================================================
## To add an HTTP server (httpd) alongside the CPU stress test and include the hostname in the output, you can modify the User Data script as follows:

This script will:

Install httpd (Apache HTTP Server).
Start the httpd service.
Stress the CPU using the stress tool.
Output the hostname and the stress status to a simple web page served by the Apache server.
### User Data Script:

```

#!/bin/bash
# Update system packages
dnf update -y

# Install required packages (stress-ng and httpd)
dnf install -y stress-ng httpd

# Start and enable the Apache web server
systemctl start httpd
systemctl enable httpd

# Get the hostname
HOSTNAME=$(hostname)

# Create an HTML file displaying the hostname
echo "<html><body><h1>EC2 Instance CPU Stress Test</h1><p>Hostname: $HOSTNAME</p><p>CPU Stress Test Running...</p></body></html>" > /var/www/html/index.html

# Start CPU stress test using 4 CPU cores for 10 minutes
stress-ng --cpu 4 --timeout 600s &

# Restart httpd to ensure changes take effect
systemctl restart httpd


```

