# Grafana Docker Setup

This folder contains everything needed to run a **Grafana** instance using Docker Compose, with persistent storage, custom configuration, and HTTPS support.

## 📁 Folder Contents

- **grafana.ini**  
  Main Grafana configuration file (used for custom settings including HTTPS).
- **grafana.crt** / **grafana.key**  
  SSL certificate and private key for enabling HTTPS access to the Grafana web interface.
- *(Optional)*: Add any provisioning files, dashboards, or custom plugins here.