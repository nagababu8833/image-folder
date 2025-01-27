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

# Create a custom index.html file with server details
cat <<EOF | sudo tee /var/www/html/index.html
<h1>Server Details</h1>
<p><strong>Hostname:</strong> $(hostname)</p>
<p><strong>IP Address:</strong> $(curl -s http://169.254.169.254/latest/meta-data/local-ipv4)</p>
EOF

# Restart Apache2 to load the new configuration
sudo systemctl restart apache2

```
