# WordPress IP Change Issue & Quick Fix

## Issue Summary
When running WordPress on a cloud server (e.g., AWS EC2) without a static IP or domain, the server’s public IP address may change after a stop/start or instance restart.  
Because WordPress stores the full site URL (including IP) in its database, this causes the site to break or load incorrectly when the IP changes.

---

## Why This Happens
- WordPress saves URLs (for site address, images, links, etc.) as **absolute URLs** inside the database.
- If the server’s IP changes but WordPress still references the old IP, the site breaks (missing resources, broken links, admin panel issues).
- Dynamic IPs are common on AWS EC2 instances unless you assign an Elastic IP or use a domain with DNS pointing to your server.

---

## How to Identify the Issue
- Site loads very slowly or not at all.
- Links, images, and CSS files fail to load.
- Admin dashboard appears broken or inaccessible.
- Apache and MySQL services are running normally on the server.
- Local `curl http://localhost` works, but accessing the site via public IP or domain fails.

---

## Step-by-Step Quick Fix

### 1. Verify Apache and MySQL Are Running
```bash
sudo systemctl status apache2
sudo systemctl status mysql


2. Navigate to the WordPress directory (usually /var/www/html)
bash
Copy
Edit
cd /var/www/html
3. Install WP-CLI (if not already installed)
bash
Copy
Edit
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
php wp-cli.phar --info
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
wp --info
4. Run Search & Replace to update old IP to new IP:
bash
Copy
Edit
wp search-replace 'http://OLD_IP' 'http://NEW_IP' --allow-root --path=/var/www/html
Replace OLD_IP and NEW_IP with your actual IP addresses.

5. Clear your browser cache and reload your site via the new IP.
Prevent Future Issues
Use a Static Elastic IP on AWS to prevent IP changes.

Use a domain name with DNS pointing to your server and configure WordPress to use the domain URL.
