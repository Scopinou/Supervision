# 📁 certs

This folder contains SSL/TLS certificates and private keys used by the monitoring stack (Prometheus, Grafana, Alertmanager, etc).

## Structure

certs/
├── monitoring.crt # Public certificate (PEM format)
├── monitoring.key # Private key (PEM format, keep secure!)


## Usage

- **monitoring.crt** and **monitoring.key** are mounted into your Docker containers to enable HTTPS for your monitoring services.
- All services sharing the same certificate should reference these files in their configuration.

## Security Notice

- **Never share your private key (`monitoring.key`) publicly.**
- Restrict permissions: ideally `chmod 600` on the key file.
- Certificates in this folder are for development or internal use. For production, use certificates from a trusted Certificate Authority (CA).

## Example Docker Compose usage

volumes:

    ./certs/monitoring.crt:/etc/service/monitoring.crt:ro

    ./certs/monitoring.key:/etc/service/monitoring.key:ro


## Regenerating Certificates

To generate a new self-signed certificate:

sudo openssl req -new -newkey rsa:2048 -days 365 -nodes -x509
-keyout certs/monitoring.key
-out certs/monitoring.crt
-subj "/C=FR/ST=France/L=Paris/O=MyOrg/OU=IT/CN=FRPONSUPERVISION-01"

---