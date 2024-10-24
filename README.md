Here's the same solution with added emojis to make your README file more engaging:

---

# 🚀 Docker EXEC Operations: Apache2 Installation and Configuration 🐳

This guide demonstrates how to install and configure Apache2 inside a Docker container (`kkloud`) running on **App Server 3** in Stratos Datacenter. We'll configure Apache to listen on port **3002** instead of the default **port 80**.

---

## 🛠️ Prerequisites:

- Docker must be installed and running 🐋.
- The `kkloud` container should already be up and running on **App Server 3**.

---

## 📋 Step-by-Step Solution:

### 1️⃣ SSH into App Server 3 💻

Access the server where your Docker container is running:

```bash
ssh user@app_server_3_ip
```

---

### 2️⃣ Verify Docker Container Status 🔍

Check if the `kkloud` container is running by listing all the containers:

```bash
docker ps
```

Look for the **container ID** or **name** of `kkloud`.

---

### 3️⃣ Access the Running Container 🏗️

Enter the running container using `docker exec`:

```bash
docker exec -it kkloud sh
```

---

### 4️⃣ Update Package Lists in the Container 📝

Update the package lists to ensure the latest repositories are available:

```bash
apt update
```

---

### 5️⃣ Install Apache2 📦

Install Apache2 inside the container:

```bash
apt install apache2 -y
```

---

### 6️⃣ Configure Apache to Listen on Port 3002 🔧

**a. Update Apache Ports Configuration** 🔀

Navigate to the `apache2` directory and open the `ports.conf` file for editing:

```bash
cd /etc/apache2
vi ports.conf
```

Add port `3002` to the configuration:

```conf
Listen 80
Listen 3002
```

Save and exit the file.

---

**b. Update Apache Virtual Host Configuration** 🌐

Edit the `000-default.conf` file to make Apache listen on port **3002**:

```bash
cd sites-available
vi 000-default.conf
```

Change the port in the `<VirtualHost>` tag:

```conf
<VirtualHost *:3002>
```

Save and exit.

---

### 7️⃣ Restart Apache Service 🔄

Restart the Apache service to apply the changes:

```bash
service apache2 restart
```

---

### 8️⃣ Verify Apache is Running on Port 3002 ✅

Use `curl` to verify Apache is now listening on port `3002`:

```bash
curl http://localhost:3002
```

You should see the default Apache page!

---

### 9️⃣ Keep the Container Running 🏃‍♂️

Make sure the `kkloud` container stays up and running:

```bash
docker ps
```

---

## 🔗 Summary:

In this guide, we walked through installing and configuring Apache2 in a Docker container running on **App Server 3**. We modified Apache's configuration to listen on port **3002**, ensuring that the container and Apache service remain operational.

---

## ✨ GitHub Setup

To push this guide to your GitHub repository:

1. Create a `README.md` file in your project folder and add these steps.
2. Use Git to commit and push the changes:
