# **🚀 Cloud-Based GitHub Monitoring with Grafana**

## **📌 Project Overview**


This project demonstrates how to set up Grafana on an AWS EC2 instance and use it to monitor GitHub repository metrics. By following these steps, you can visualize GitHub activity, repository insights, and contributions in real-time using Grafana’s GitHub data source integration.


## **🏗️ Steps to Set Up**

### 🔹 1. Launch an AWS EC2 Instance
- Log in to AWS Console and navigate to EC2.

- Click Launch Instance and configure the following:

    - Name: Grafana Monitoring
    - OS: Ubuntu
    - Instance Type: t2.medium
    - Key Pair: Create a new key pair or use an existing one.
    - Security Group:
        - Allow Inbound Rule for Port 3000 (Grafana runs on this port).
    - Storage: Add 2GB of extra storage.

Click Launch to start the instance.


### 🔹 2. Connect to the EC2 Instance via SSH

```sh
ssh -i <your-key-pair-name> ubuntu@<public-ip-address>
```
- Update packages:
```sh
sudo apt update
```
sudo apt update

### 🔹 3. Install Grafana
```sh
sudo apt-get install -y adduser libfontconfig1 musl
wget https://dl.grafana.com/enterprise/release/grafana-enterprise_11.5.1_amd64.deb
sudo dpkg -i grafana-enterprise_11.5.1_amd64.deb
```

### 🔹 4. Access Grafana

- Open your browser and enter:
```cpp
http://<public-ip-address>:3000
```
- Login using:
    - Username: admin
    - Password: admin (change it after login)


### **🔗 Connect Grafana with GitHub**

### 🔹 5. Generate a GitHub Personal Access Token

1. Go to GitHub → Settings → Developer Settings.
2. Click Personal Access Tokens → Tokens (Classic).
3. Click Generate new token and select the following permissions:

    ✅ Repo: Full access

    ✅ Admin:Org: Read access

    ✅ Admin:Repo_Hook: Read access

    ✅ User: Read access & email

    ✅ Admin:Enterprise: Read access

    ✅ Audit Log: Read access

    ✅ Projects: Read access

Click Generate Token and copy the token.

### 🔹 6. Configure GitHub as a Data Source in Grafana

- Go to Grafana Dashboard → Connections → Data Sources.
- Search for GitHub, click Install and then Add Data Source.
- Set a name for the data source.
- Paste the GitHub Personal Access Token and click Save & Test.


### 🔹 7. Import a GitHub Monitoring Dashboard
1. Search for "GitHub DataSource Dashboard Grafana" on Google.
2. Copy the Dashboard ID from the Grafana dashboard repository.
3. In Grafana, go to Dashboard → Import.
4. Paste the Dashboard ID and click Load.
5. Set a Dashboard Name and select your GitHub data source.
6. Click Import.


### 🔹 8. Configure GitHub Repository Metrics
- Set GitHub Organization Name (your GitHub username).
- Select a Repository to monitor.
- Choose a Branch (e.g., main).
- Set Time Range for data visualization.


## **🎯 Final Result**
🎉 Your GitHub repository dashboard is now live on Grafana!

You can now monitor repository activities such as:

- Commits & Pull Requests
- Issues & Stars
- Contributor Stats
- Repository Forks & Traffic


## 🛠️ Technologies Used
- AWS EC2 (Virtual Machine)
- Ubuntu (Operating System)
- Grafana (Monitoring Dashboard)
- GitHub API (Data Source)


## 📌 Future Improvements
- Integrate Prometheus for advanced monitoring.
- Automate the setup using Terraform or Ansible.
- Use Grafana Alerts for real-time notifications.




