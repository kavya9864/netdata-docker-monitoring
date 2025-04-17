ELEVATE LABS TASK 7
# 🧠 TASK 7: Monitor System Resources Using Netdata

## 📌 Objective
Install and configure Netdata (via Docker) to visualize system and application performance metrics on an AWS EC2 instance.

---

## 🔧 Prerequisites
- AWS EC2 instance running Ubuntu (with open port 19999)
- SSH access via MobaXterm or terminal
- Docker installed on the server

---

## 🛠 Tools Used
- **Netdata** – Real-time monitoring tool
- **Docker** – Containerization platform
- **AWS EC2 (Ubuntu)** – Cloud-based Linux environment
- **MobaXterm** – SSH client for accessing the instance

---

## ⚙️ Installation & Setup Steps

### ✅ 1. Connect to AWS EC2 via MobaXterm
SSH into the Ubuntu server using your key pair.
![EC2](https://github.com/user-attachments/assets/9af10c66-3fc4-4fea-9070-87183126c9d8)


---

### ✅ 2. Install Docker
bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
![doc](https://github.com/user-attachments/assets/efa04c89-bbdb-46d5-8026-0a350045e261)
![doc (2)](https://github.com/user-attachments/assets/4e2a891d-c46b-4570-94a8-7399dee01306)


✅ 3. Run Netdata with Volume Mounts (Advanced Setup)

mkdir -p ~/netdata/etc
mkdir -p ~/netdata/var

docker run -d --name=netdata \
  -p 19999:19999 \
  -v ~/netdata/etc:/etc/netdata \
  -v ~/netdata/var:/var/lib/netdata \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  netdata/netdata
This setup persists configuration and monitoring data.
![net data](https://github.com/user-attachments/assets/75cd0dff-a6cb-4050-bf82-6798b3535195)


✅ 4. Access Netdata Dashboard

Go to:http://51.21.223.247:19999
![netdata](https://github.com/user-attachments/assets/8739c142-5bcb-4fce-98fe-4eceb65e53bf)


✅ 5. View Configuration Files
After running with volumes, Netdata’s configuration files are available here:
cd ~/netdata/etc
To edit alert settings:
cd ~/netdata/etc

To edit alert settings:
nano ~/netdata/etc/health_alarm_notify.conf



📊 Features Tested
Real-time metrics for CPU, memory, disk, and Docker containers

Persistent config + data storage using host-mounted volumes

Dashboard accessed via browser

Prepared for advanced alerting (Discord/Slack/etc.)

---

## 👩‍💻 Author

🌐 GitHub: @kavya9864



