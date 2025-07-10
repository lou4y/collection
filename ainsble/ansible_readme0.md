
# DevOps Tools Provisioning with Ansible

This project uses **Ansible** to automate the installation and configuration of essential DevOps tools on Ubuntu-based servers. It follows a modular role-based architecture for easy maintenance and scalability.

---

## Tools Installed

- **Java OpenJDK 17** — Required for Jenkins, SonarQube, and Nexus  
- **Docker** — Container runtime engine  
- **Jenkins** — Continuous Integration server  
- **Maven** — Java build tool  
- **Nexus OSS** — Artifact repository manager  
- **Trivy** — Vulnerability scanner  
- **OWASP Dependency-Check** — Dependency vulnerability analysis  
- **SonarQube** — Static code analysis platform  
- **Prometheus** — Monitoring system and time series database  
- **Grafana** — Visualization and dashboard tool  

---

## Project Structure

```
ansible/
├── site.yml               # Main playbook
├── hosts                  # Inventory file
└── roles/
    ├── java/
    ├── docker/
    ├── jenkins/
    ├── maven/
    ├── nexus/
    ├── trivy/
    ├── owasp/
    ├── sonarqube/
    ├── prometheus/
    └── grafana/
```

Each role contains the tasks to install and configure the corresponding tool.

---

## Getting Started

### Prerequisites

- Ubuntu 20.04 or newer on target machines  
- Ansible installed on your control machine  
- SSH access to target machines  

### Inventory Setup

Edit the `hosts` file to define your target servers:

```ini
[devops]
your.server.ip ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
```

### Running the Playbook

To install all tools:

```bash
ansible-playbook -i hosts site.yml
```

To install specific tools by tags, use:

```bash
ansible-playbook -i hosts site.yml --tags <role_tag>
```

Example:

```bash
ansible-playbook -i hosts site.yml --tags jenkins,docker
```

---

## Customization

- Update variables such as Nexus or Dependency-Check versions in `site.yml`  
- Modify roles to tweak installation options or configurations  

---

## License

This project is licensed under the MIT License.

---
