# Supervision
Ce repos GitHub rassemble toute la partie correction du scénario du FYC.

![image](https://github.com/user-attachments/assets/e6887e20-8164-40dc-9c49-52240ff980c0)

Afin de pouvoir utiliser ce repo, il faut générer des certificats pour la sécurisation de la page WEB de Prometheus. Pour cela, nous allons taper ces commandes :

Pour générer la key et le crt :
```
sudo openssl req -new -newkey rsa:2048 -days 365 -nodes -x509 \
-keyout certs/monitoring.key \
-out certs/monitoring.crt \
-subj "/C=FR/ST=France/L=Paris/O=ESGI/OU=IT/CN=FRPONSUPERVISION-01"
```

Pour modifier les permissions afin que l'utilisateur root dans le conteneur, puisse lire la clé, sinon, il y aura une erreur de permission dans les logs :
sudo chmod 644 prometheus/prometheus.key


Il y a certaines valeurs qu'il faut remplacer manuellement dans les fichiers suivants (Les détails des changements sont illustrés dans notre scénario FYC) :

![image](https://github.com/user-attachments/assets/3b6e6fd6-e764-4099-9e33-52a71b116c0a)
![image](https://github.com/user-attachments/assets/cf2c0bd9-1967-40a3-bcbc-b25787b3bb70)
![image](https://github.com/user-attachments/assets/f226ad59-20bc-4f09-b67d-3850731d0d6e)
