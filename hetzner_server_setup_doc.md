# Hetzner Server Setup Documentation

## Server Info
- **Provider:** Hetzner
- **Server IP:**  primary IP (IPV4)
- **OS:** Ubuntu
- **Project:** DailyDoer Backend

---

## Step 1: Connect to Server via SSH

```bash
ssh root@<primary IP>
```

### or if new user created
```bash
ssh guram@178.104.31.243
```


## Step 2: Create a New User

```bash
adduser guram
usermod -aG sudo guram
su - guram
```

## Step 3: Install Docker

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y ca-certificates curl gnupg

sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

### Add Docker repository:
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker:
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

## Step 4: Add User to Docker Group

```bash
sudo usermod -aG docker guram
newgrp docker
```

## Step 5: Verify Installation

```bash
docker --version
docker compose version
```
