# MongoDB


L’installation de MongoDB sur **Ubuntu 22.04** peut se faire en suivant les étapes ci-dessous :

---

### Étape 1 : Importer la clé publique MongoDB
Commencez par ajouter la clé GPG pour vérifier les packages MongoDB.

```bash
curl -fsSL https://pgp.mongodb.com/server-6.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb-server-6.0.gpg
```

---

### Étape 2 : Ajouter le dépôt officiel MongoDB
Ajoutez le dépôt MongoDB au fichier des sources d'APT.

```bash
echo "deb [ arch=amd64 signed-by=/usr/share/keyrings/mongodb-server-6.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

---

### Étape 3 : Mettre à jour le cache APT
Actualisez les index des dépôts pour inclure le dépôt MongoDB.

```bash
sudo apt update
```

---

### Étape 4 : Installer MongoDB
Installez MongoDB avec la commande suivante :

```bash
sudo apt install -y mongodb-org
```

---

### Étape 5 : Vérifier la version installée
Assurez-vous que MongoDB est correctement installé en vérifiant sa version :

```bash
mongod --version
```

---

### Étape 6 : Démarrer le service MongoDB
Lancez MongoDB et configurez-le pour démarrer automatiquement au démarrage du système.

```bash
sudo systemctl start mongod
sudo systemctl enable mongod
```

---

### Étape 7 : Vérifier le statut du service
Assurez-vous que MongoDB est en cours d'exécution :

```bash
sudo systemctl status mongod
```

---

### Étape 8 : Tester MongoDB
Lancez le client MongoDB pour tester son fonctionnement :

```bash
mongosh
```

Si tout fonctionne, vous serez dans la console interactive `mongosh`.

---

### Désinstallation (si nécessaire)
Si vous devez désinstaller MongoDB, utilisez la commande suivante :

```bash
sudo apt purge mongodb-org*
sudo rm -r /var/log/mongodb
sudo rm -r /var/lib/mongodb
```

