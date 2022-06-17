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

## Portainer Setup

Create directory for portainer data:

```bash
mkdir /portainer mkdir /portainer/data
```

Run Portainer:

```bash
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always --pull=always -v /var/run/docker.sock:/var/run/docker.sock -v /portainer/data:/data portainer/portainer-ce
```

---

## Access Portainer

Go to `http://<your-proxmox-url>:9000`

Use the GUI to setup your portainer account.

---
