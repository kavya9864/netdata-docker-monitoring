<<<<<<< HEAD
# 🧠 TASK 7: Monitor System Resources Using Netdata

## 📌 Objective
Install and configure Netdata (via Docker) to visualize system and application performance metrics on an AWS EC2 instance.

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

---

### ✅ 2. Install Docker
```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

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

✅ 4. Access Netdata Dashboard

Go to:http://51.21.223.247:19999

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




=======
# netdata-docker-monitoring
>>>>>>> df103a59e33cede42c7f699de4a3515f9b19b38c
