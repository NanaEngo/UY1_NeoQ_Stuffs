# 🍃 MongoDB Installation Guide (Ubuntu 22.04)

> Complete guide for installing MongoDB on Ubuntu 22.04 LTS. Includes both French and English instructions.

---

## Table of Contents

1. [Quick Start (English)](#-quick-start-english)
2. [Guide Complet (Français)](#-guide-complet-français)
3. [Verification](#-verification)
4. [Uninstallation](#-uninstallation)

---

## 🚀 Quick Start (English)

### Step 1: Import MongoDB Public Key

```bash
curl -fsSL https://pgp.mongodb.com/server-6.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb-server-6.0.gpg
```

---

### Step 2: Add Official Repository

```bash
echo "deb [ arch=amd64 signed-by=/usr/share/keyrings/mongodb-server-6.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

---

### Step 3: Update Package Cache

```bash
sudo apt update
```

---

### Step 4: Install MongoDB

```bash
sudo apt install -y mongodb-org
```

---

### Step 5: Verify Installation

```bash
mongod --version
```

---

### Step 6: Start MongoDB Service

```bash
sudo systemctl start mongod
sudo systemctl enable mongod
```

---

### Step 7: Check Service Status

```bash
sudo systemctl status mongod
```

---

### Step 8: Test MongoDB

```bash
mongosh
```

> ✅ If successful, you'll enter the interactive `mongosh` console.

---

## 📋 Guide Complet (Français)

### Étape 1 : Importer la clé publique MongoDB

```bash
curl -fsSL https://pgp.mongodb.com/server-6.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb-server-6.0.gpg
```

> Ajoute la clé GPG pour vérifier les packages MongoDB.

---

### Étape 2 : Ajouter le dépôt officiel

```bash
echo "deb [ arch=amd64 signed-by=/usr/share/keyrings/mongodb-server-6.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

> Ajoute le dépôt MongoDB au fichier des sources d'APT.

---

### Étape 3 : Mettre à jour le cache APT

```bash
sudo apt update
```

> Actualise les index des dépôts pour inclure MongoDB.

---

### Étape 4 : Installer MongoDB

```bash
sudo apt install -y mongodb-org
```

---

### Étape 5 : Vérifier la version installée

```bash
mongod --version
```

---

### Étape 6 : Démarrer le service MongoDB

```bash
sudo systemctl start mongod
sudo systemctl enable mongod
```

> Lance MongoDB et le configure pour démarrer automatiquement.

---

### Étape 7 : Vérifier le statut du service

```bash
sudo systemctl status mongod
```

---

### Étape 8 : Tester MongoDB

```bash
mongosh
```

> Si tout fonctionne, vous serez dans la console interactive `mongosh`.

---

## ✅ Verification

### Check MongoDB is Running

```bash
systemctl is-active mongod
```

> Should return: `active`

### Check MongoDB Version

```bash
mongod --version
```

### Connect to MongoDB

```bash
mongosh
```

Expected output:
```
Current Mongosh Log ID: ...
Connecting to:          mongodb://127.0.0.1:27017
Using MongoDB:          6.0.x
```

---

## 🗑️ Uninstallation / Désinstallation

### Remove MongoDB Packages

```bash
sudo apt purge mongodb-org*
```

### Remove Data and Logs

```bash
sudo rm -r /var/log/mongodb
sudo rm -r /var/lib/mongodb
```

### Remove Repository

```bash
sudo rm /etc/apt/sources.list.d/mongodb-org-6.0.list
sudo rm /usr/share/keyrings/mongodb-server-6.0.gpg
```

---

## 📌 Quick Reference / Références Rapides

| Command | Description |
|---------|-------------|
| `sudo systemctl start mongod` | Start MongoDB |
| `sudo systemctl stop mongod` | Stop MongoDB |
| `sudo systemctl restart mongod` | Restart MongoDB |
| `sudo systemctl status mongod` | Check status |
| `mongosh` | Open MongoDB shell |

---

## 🔗 Useful Links / Liens Utiles

- [MongoDB Official Documentation](https://docs.mongodb.com/)
- [MongoDB University (Free Courses)](https://university.mongodb.com/)
- [MongoDB Shell Documentation](https://www.mongodb.com/docs/mongodb-shell/)

---

*UY1 Néo Quanticiens – Python Tricks Collection*
