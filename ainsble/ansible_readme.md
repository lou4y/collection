# 🔐 SSH Setup Between Control Node and Target Hosts

Before running Ansible, ensure passwordless SSH access or use manual password entry.

## 📌 Option 1: Passwordless SSH Access (Recommended)

### 1. Generate SSH Key on Control Node (if not already):
```bash
ssh-keygen -t rsa -b 4096
```

Press Enter through all prompts to accept defaults.

### 2. Copy SSH Key to Target Host:
```bash
ssh-copy-id ubuntu@<TARGET_IP>
```

Replace `<TARGET_IP>` with your target Ubuntu server's IP address.

### 3. Test SSH Connection:
```bash
ssh ubuntu@<TARGET_IP>
```

You should connect without being prompted for a password.

---

## 🔐 Option 2: Manual SSH (with password)

If you prefer not to use SSH keys, you can use Ansible with password authentication:

### 1. Install SSH server on the target machine (if not already):
```bash
sudo apt update && sudo apt install openssh-server -y
```

### 2. Connect manually with:
```bash
ssh ubuntu@<TARGET_IP>
```

### 3. Use Ansible with password prompt:
```bash
ansible -i inventory.ini target -m ping --ask-pass
```

---

# 🔐 SSH Setup Between Control Node and Target Hosts

Before running Ansible, ensure passwordless SSH access between your control machine and the target host.

### 1. Generate SSH Key on Control Node (if not already):
```bash
ssh-keygen -t rsa -b 4096
```

Press Enter through all prompts to accept defaults.

### 2. Copy SSH Key to Target Host:
```bash
ssh-copy-id ubuntu@<TARGET_IP>
```

Replace `<TARGET_IP>` with your target Ubuntu server's IP address.

### 3. Test SSH Connection:
```bash
ssh ubuntu@<TARGET_IP>
```

You should connect without being prompted for a password.

---
# 🚀 Ansible Project: Automated Setup for DevOps Tools

This Ansible project installs and configures essential DevOps tools on an Ubuntu server.

## 📦 Tools Installed

- Java (for Jenkins)
- Docker
- Jenkins
- Maven
- Nexus
- Trivy (Security Scanner)
- OWASP Dependency-Check
- SonarQube
- Prometheus
- Grafana

## 🧱 Project Structure

```bash
ansible-setup/
├── inventory.ini         # Inventory file with list of target hosts
├── site.yml              # Main playbook that includes all roles
└── roles/
    ├── java/
    │   └── tasks/main.yml
    ├── docker/
    │   └── tasks/main.yml
    ├── jenkins/
    │   └── tasks/main.yml
    ├── maven/
    │   └── tasks/main.yml
    ├── nexus/
    │   └── tasks/main.yml
    ├── trivy/
    │   └── tasks/main.yml
    ├── owasp/
    │   └── tasks/main.yml
    ├── sonarqube/
    │   └── tasks/main.yml
    ├── prometheus/
    │   └── tasks/main.yml
    └── grafana/
        └── tasks/main.yml
```

## 📋 Usage

1. Edit the `inventory.ini` file to include the IPs of your target machines.

```ini
[target]
172.25.14.128 ansible_user=ubuntu
```

2. Run the playbook:

```bash
ansible-playbook -i inventory.ini site.yml
```

Use tags to run specific roles only:

```bash
ansible-playbook -i inventory.ini site.yml --tags docker
```

## ✅ Requirements

- Ubuntu-based target machines
- Control node with:
  - Ansible installed
  - SSH key set up with target machines
