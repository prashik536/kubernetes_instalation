##  Install Docker on Ubuntu

Follow the steps below to install Docker using the official Docker repository.

###  Add Docker's Official GPG Key

```bash
sudo apt-get update
sudo apt-get install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

###  Add Docker Repository to Apt Sources

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo \"${UBUNTU_CODENAME:-$VERSION_CODENAME}\") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
```

###  Install Docker Engine, CLI, and Compose Plugin

```bash
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

###  Enable Docker Services

```bash
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```
### DOCKER AS NON ROOT USER
```bash
sudo usermod -aG docker $USER
newgrp docker
```
