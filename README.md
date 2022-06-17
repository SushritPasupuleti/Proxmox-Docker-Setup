# Proxmox Docker Setup

Setup Docker on Proxmox.

## Docker Setup

Refer [Docker Setup](https://docs.docker.com/engine/install/debian/).

Start with updates:

```bash
apt update && apt dist-upgrade -y
```

Some prerequisites:

```bash
apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common
```

Run update again:

```bash
apt update
```

Add Docker's GPG Key:

```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

Setup Repo:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker:

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

Docker Setup completed 🎉!

---
