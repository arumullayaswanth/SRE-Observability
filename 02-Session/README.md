# Metries(Monitoring Stacks)

### 🔹 Instance 1: **Grafana and Prometheus**

1. Log in to [AWS Management Console](https://console.aws.amazon.com/).
2. Go to **EC2 → Instances → Launch instances**.
3. **Name**:
    - Enter `grefana-prometheus`.

4. **Application and OS Images (AMI)**:
    - Select **Ubuntu Server 22.04 LTS (HVM)** (or latest Ubuntu LTS).

5. **Instance type**:
    - Choose `t2.micro` (free-tier eligible) or larger if needed.

6. **Key pair (login)**:
    - Select an existing SSH key pair (or create a new one).

7. **Network settings**:
    - Choose your VPC + Subnet.
    - Select/Create a **Security Group** with at least:
        - SSH (22)
        - HTTP (80)
        - HTTPS (443)
        - Custom TCP 3000 (Grafana)
        - Custom TCP 9090 (Prometheus)

8. **Storage**: Leave default (8–10 GB is fine).  
9. Click **Launch Instance**.

---

## 🔹 Step 1: Create an IAM Role

1. Go to **AWS Console → IAM → Roles → Create Role**.
2. Choose **Trusted Entity** = **AWS service**.
3. Choose **Use Case** = **EC2**.
4. Click **Next**.
5. Attach permissions policies (depending on what your Prometheus/Grafana EC2 needs):
    - Example:
        - `CloudWatchReadOnlyAccess` (if Grafana needs CloudWatch metrics)
        - `AmazonEC2ReadOnlyAccess` (if Prometheus scrapes EC2 metadata)
        - Or create a **custom policy** if only limited access is needed.
6. Click **Next**, then give the role a name (e.g., `PrometheusGrafanaRole`).
7. Click **Create Role**.

---

## 🔹 Step 2: Attach the IAM Role to Your EC2 Instance

1. Go to **EC2 → Instances**.
2. Select your instance: `grefana-prometheus`.
3. In the **Instance details**, Actions → Security → **Modify IAM role**.
4. Choose the IAM role you created (`PrometheusGrafanaRole`).
5. Click **Update IAM role**.

---

### 🔹 Instance 2: **Node-1**

1. Go to **Launch instances**.
2. **Name**:
    - Enter `node-server`.

3. **AMI**:
    - Choose **Ubuntu Server 22.04 LTS**.

4. **Instance type**: `t2.micro`.
5. **Key pair**: same as above.
6. **Network settings**:
    - Use same VPC/Subnet.
    - Security Group can allow just **SSH (22)** + any needed ports (e.g., if you’ll run exporters).

7. **Storage**: leave default.
8. Click **Launch Instance**.

---

### 🔹 How to Start a Free Trial on PagerDuty

1. Go to [PagerDuty Free Trial](https://www.pagerduty.com/).
2. Enter your details:
    - **Work Email:** `yash@gmail.com`
    - **First Name & Last Name:** fill as you prefer
    - **Company Name:** personal/project name if needed
    - **Password:** Create a strong one.
3. Click **Start Free Trial**.
4. Verify your account via the email received at `yash@yash.com`.
5. Log in to start using PagerDuty.

---

## 🔹 Service Directory in PagerDuty

- Found in the UI: **Services → Service Directory**.

Copy the integration info:



Here’s a properly formatted `.md` version of your content that preserves all code blocks and structure:

````markdown
Integration Name  
Prometheus

Integration Key  
661813e1777d480ed0606acb28e5bd81

Integration URL  
https://events.pagerduty.com/generic/2010-04-15/create_event.json

---

## 🔹 1. Connect to your grefana-prometheus EC2

## 🔹 2. Switch to root
```bash
sudo -i
````

## 🔹 3. Create/Edit the `app.sh` file

```bash
vim app.sh
```

Inside vim:

* Press `i` to go into **insert mode**.
* Paste your script content (whatever you want the server to run). Example:

```bash
code
```

* Press `Esc` → type `:wq` → press `Enter` to save and quit.

## 🔹 4. Run the script

```bash
sh app.sh
```

---

## 3. Access Grafana in Browser

* Open a browser and go to:

```
http://<EC2-Public-IP>:3000
```

* Default login:

  * **Username:** `admin`
  * **Password:** `admin` (you’ll be prompted to change it)

---

## 🔹 4. Access Prometheus Web UI

* Open a browser and go to:

```
http://<EC2-Public-IP>:9090
```

* You should see the **Prometheus dashboard** with alerts.
* Check Alerts (see if one instance is down).

> Note: Now go to PagerDuty → Activity → see if any issue is triggered.

---

## 🔹 1. Connect to your node-server EC2

## 🔹 2. Switch to root

```bash
sudo -i
```

## 🔹 3. Create/Edit the `app.sh` file

```bash
vim app.sh
```

Inside vim:

* Press `i` to go into **insert mode**.
* Paste your script content (whatever you want the server to run). Example:

```bash
code
```

* Press `Esc` → type `:wq` → press `Enter` to save and quit.

## 🔹 4. Run the script

```bash
sh app.sh
```

---

> Now check again if the issue is resolved.

---

### Node-server: Stress commands

```bash
sudo apt-get install stress-ng -y  # Ubuntu/Debian
stress-ng --cpu 2 --timeout 300
```

```

If you want, I can also combine **Grafana, Prometheus, and node-server steps** into a single clean `.md` guide for easier copy-pasting.  

Do you want me to do that?
```
