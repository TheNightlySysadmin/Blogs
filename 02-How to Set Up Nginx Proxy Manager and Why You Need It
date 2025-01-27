# How to Set Up Nginx Proxy Manager and Why You Need It - The Nightly Sysadmin
In the world of self-hosting and web services, managing multiple applications while ensuring secure access can become a daunting task. This is where a reverse proxy like Nginx Proxy Manager (NPM) steps in to simplify the process. In this guide, we’ll cover what Nginx Proxy Manager is, why you should use it, and provide a step-by-step tutorial on setting it up.

* * *

### **What Is Nginx Proxy Manager?**

Nginx Proxy Manager is a user-friendly interface for managing Nginx, a powerful web server and reverse proxy. It allows you to:

1.  **Redirect Traffic:** Direct traffic to different services hosted on your server.
2.  **Secure Applications:** Use SSL certificates for HTTPS connections.
3.  **Easily Manage Subdomains:** Assign subdomains to your services.
4.  **Access Logs and Stats:** Monitor service usage and performance.

Unlike raw Nginx configuration files, NPM provides a clean graphical interface, making it an excellent choice for beginners and experienced sysadmins alike.

* * *

### **Why Set Up Nginx Proxy Manager?**

Setting up Nginx Proxy Manager offers multiple benefits:

1.  **Centralized Management:** Manage multiple services from a single interface.
2.  **HTTPS Made Simple:** Easily obtain and renew SSL certificates using Let’s Encrypt.
3.  **Domain-Based Access:** Configure subdomains to cleanly access different services (e.g., `nextcloud.example.com`, `plex.example.com`).
4.  **Improved Security:** Protect your services by hiding direct IP access and using HTTPS.
5.  **Convenient Port Forwarding:** Simplify service access even when running on non-standard ports.

For self-hosters running applications like Nextcloud, Jellyfin, or Home Assistant, NPM can streamline your setup and enhance security.

* * *

### **How to Set Up Nginx Proxy Manager**

#### **Prerequisites**

*   A server running Docker and Docker Compose (recommended).
*   A domain name for your services.
*   Basic knowledge of command-line tools.

#### **Step 1: Install Docker and Docker Compose**

1.  **Install Docker:**

```
   sudo apt update
   sudo apt install -y docker.io
   sudo systemctl start docker
   sudo systemctl enable docker
```


2.  **Install Docker Compose:**

```
   sudo apt install -y docker-compose
```


#### **Step 2: Set Up the Docker Container**

1.  **Create a Directory for NPM:**

```
   mkdir -p ~/nginx-proxy-manager
   cd ~/nginx-proxy-manager
```


2.  **Create a `docker-compose.yml` File:**

```
   version: '3'

   services:
     app:
       image: 'jc21/nginx-proxy-manager:latest'
       ports:
         - '80:80'   # HTTP
         - '81:81'   # NPM Dashboard
         - '443:443' # HTTPS
       volumes:
         - ./data:/data
         - ./letsencrypt:/etc/letsencrypt
       restart: always
```


3.  **Start the Container:**

```
   docker-compose up -d
```


#### **Step 3: Access the NPM Dashboard**

1.  Open your browser and navigate to `http://<server-ip>:81`.
2.  Log in using the default credentials:

*   **Username:** `[[email protected]](https://thenightlysysadmin.com/cdn-cgi/l/email-protection)`
*   **Password:** `changeme`

1.  Change the default credentials immediately for security.

#### **Step 4: Configure a Proxy Host**

1.  In the dashboard, go to **Proxy Hosts** > **Add Proxy Host**.
2.  Fill in the following details:

*   **Domain Names:** Enter the subdomain (e.g., `nextcloud.example.com`).
*   **Scheme:** Choose `http` or `https`.
*   **Forward Hostname / IP:** Enter the IP or hostname of the service.
*   **Forward Port:** Enter the port on which the service is running.

1.  Enable **Websockets Support** if needed.
2.  Go to the **SSL Tab** and select “Request a new SSL certificate” to enable HTTPS.
3.  Save the configuration.

#### **Step 5: Test Your Setup**

Visit the subdomain in your browser (e.g., `https://nextcloud.example.com`). If everything is configured correctly, you’ll be redirected to your service.

* * *

### **Best Practices for Using Nginx Proxy Manager**

1.  **Regularly Update NPM:** Keep your Docker image updated to patch security vulnerabilities.
2.  **Use Strong Passwords:** Secure the NPM dashboard with a robust password.
3.  **Monitor Logs:** Check logs periodically for unauthorized access attempts.
4.  **Secure Backups:** Backup your NPM configuration for quick recovery.

* * *

### **Conclusion**

Nginx Proxy Manager is a powerful tool that simplifies the process of managing web services and securing them with SSL. Its intuitive interface makes it accessible to both beginners and advanced users, ensuring your applications are always reachable and secure. Whether you’re running a single application or managing an entire suite of services, NPM is an invaluable addition to your setup.