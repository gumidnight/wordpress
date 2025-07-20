# Personal Resume Website with WordPress on AWS

This repository documents the setup and troubleshooting of my personal resume website running on WordPress hosted on an AWS EC2 instance.

---

## Overview

- WordPress is installed on an AWS EC2 Ubuntu instance.
- The website serves as my online CV/portfolio.
- This README contains setup steps, common issues, and fixes related to IP changes.

---

## Setup Highlights

- Use an Ubuntu EC2 instance with Apache and MySQL.
- Install WordPress in `/var/www/html`.
- Use WP-CLI for management and search-replace operations.
- Assign an Elastic IP or use a domain to avoid IP-change issues.

---

## Common Issue: IP Change Breaks Site

### What Happens?

- AWS EC2 public IP changes on instance stop/start.
- WordPress stores old IP in database, causing broken links and inaccessible admin panel.

### Quick Fix:

1. SSH into the server.
2. Navigate to WordPress directory:
   ```bash
   cd /var/www/html
