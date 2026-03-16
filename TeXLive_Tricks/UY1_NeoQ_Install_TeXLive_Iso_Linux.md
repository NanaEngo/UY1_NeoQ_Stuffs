# Installation de TeXLive 2022 (ISO) sur Linux

Guide complet pour installer TeXLive 2022 à partir d'une image ISO sur Linux.

---

## Table des matières

1. [Préparation](#préparation)
2. [Installation graphique](#installation-graphique)
3. [Installation en ligne de commande](#installation-en-ligne-de-commande)
4. [Configuration](#configuration)
5. [Vérification et gestion](#vérification-et-gestion)
6. [Installation de TeXstudio](#installation-de-texstudio)
7. [Configuration de LanguageTool](#configuration-de-languagetool)
8. [Désinstallation](#désinstallation)

---

## Préparation

### 1. Monter l'ISO

Faites un clic droit sur le fichier ISO et choisissez l'option de montage, ou utilisez :

```bash
sudo mount -o loop texlive2022-20220321.iso /mnt
```

### 2. Ouvrir le terminal dans le répertoire contenant le fichier ISO

```bash
cd /chemin/vers/répertoire/contenant/iso
```

### 3. Installer perl-tk (nécessaire pour l'interface graphique)

```bash
sudo apt install perl-tk
```

### 4. Créer le répertoire d'installation

```bash
sudo mkdir -p /usr/local/texlive/2022 && sudo chown -R $USER /usr/local/texlive
```

> 💡 Remplacez `$USER` par votre nom d'utilisateur si nécessaire.

---

## Installation graphique

### 1. Vérifier que tk est installée

```bash
sudo apt install tk
```

### 2. Lancer l'installateur

```bash
./install-tl -gui
```

### 3. Configurer et installer

- Sélectionnez les packages à installer
- Lancez l'installation

---

## Installation en ligne de commande

Pour une installation rapide, utilisez un fichier de profil :

```bash
./install-tl --profile /chemin/vers/fichier.profile
```

**Exemple :**

```bash
./install-tl --profile /media/nesg/NESG8GO/TEXLIVE/MyTL2022Linux.profile
```

---

## Configuration

### 1. Configurer la variable PATH

#### Éditer `~/.bashrc`

```bash
gedit ~/.bashrc
```

Ajoutez à la fin du fichier :

```bash
# >>>>>>> TexLive 2022 >>>>>>>
PATH=/usr/local/texlive/2022/bin/x86_64-linux:$PATH; export PATH
MANPATH=/usr/local/texlive/2022/texmf-dist/doc/man:$MANPATH; export MANPATH
INFOPATH=/usr/local/texlive/2022/texmf-dist/doc/info:$INFOPATH; export INFOPATH
# <<<<<< TexLive 2022 <<<<<<<<
```

#### Éditer `~/.profile`

```bash
gedit ~/.profile
```

Ajoutez :

```bash
# >>>>>>>> TeXlive >>>>>>>>
if [ -d "/usr/local/texlive/2022/bin/x86_64-linux" ] ; then
    PATH="$HOME/usr/local/texlive/2022/bin/x86_64-linux:$PATH"
fi
if [ -d "/usr/local/texlive/2022/texmf-dist/doc/man" ] ; then
    MANPATH="/usr/local/texlive/2022/texmf-dist/doc/man:$MANPATH"
fi
if [ -d "/usr/local/texlive/2022/texmf-dist/doc/info" ] ; then
    INFOPATH="/usr/local/texlive/2022/texmf-dist/doc/info:$INFOPATH"
fi
# <<<<<<<< TeXlive <<<<<<<<
```

Sauvegardez et fermez les fichiers.

### 2. Activer les changements

```bash
source ~/.bashrc
source ~/.profile
```

### 3. Vérifier la prise en compte des changements

```bash
echo $PATH
```

### 4. Éditer `/etc/environment`

```bash
sudo gedit /etc/environment
```

Ajoutez le chemin de TeXLive au début de `PATH` :

```bash
PATH="/usr/local/texlive/2022/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```

Sauvegardez et fermez le fichier.

### 5. Activer les changements

```bash
source /etc/environment
```

### 6. Démonter l'ISO

Utilisez le clic droit pour démonter, ou :

```bash
sudo umount /mnt
```

---

## Vérification et gestion

### 1. Faire reconnaître TeXLive par Ubuntu

```bash
sudo apt install equivs --no-install-recommends freeglut3
wget -O debian-equivs-2022-ex.txt https://www.tug.org/texlive/files/debian-equivs-2022-ex.txt
equivs-build debian-equivs-2022-ex.txt
sudo dpkg -i texlive-local_2022.99999999-1_all.deb && sudo apt install -f
```

### 2. Vérifier la version installée

```bash
tex --version
# ou
latex --version
# ou
whereis latex
```

Résultat attendu :

```
latex: /usr/local/texlive/2022/bin/x86_64-linux/latex
```

### 3. Lancer TeX Live Manager (TL Manager)

Si `tlmgr --gui` affiche `tlmgr: command not found`, utilisez :

```bash
sudo env PATH="$PATH" tlmgr --gui
```

### 4. Nettoyer l'espace de backup

Pour libérer l'espace occupé par les fichiers de backup :

```bash
tlmgr backup --clean=0 --all
```

### 5. Installer un package

```bash
tlmgr install <nom_du_package>
```

---

## Désinstallation de TeXLive 2022 (ISO)

```bash
sudo rm -rf /usr/local/texlive/*
sudo rm -rf /usr/local/share/texmf
rm -rf ~/.texlive*
```

---

## Installation et configuration de TeXstudio

### 1. Installation en ligne (via apt)

```bash
sudo apt install texstudio
```

### 2. Installation depuis un fichier `.deb` local

```bash
# Ouvrir le terminal dans le répertoire contenant le fichier .deb
sudo dpkg -i texstudioxxxxx.deb -y && sudo apt install -f -y && sudo dpkg -i texstudioxxxxx.deb -y
```

### 3. Configurer TeXstudio

1. Trouver le chemin des binaires TeXLive :

   ```bash
   which latex
   ```

   Exemple de sortie :

   ```
   /usr/local/texlive/2022/bin/x86_64-linux/latex
   ```

2. Démarrer TeXstudio

3. Aller dans `Options > Configurer TeXstudio > Commandes`

4. Coller le chemin obtenu (sans le nom de la commande) dans le champ PATH :

   ```
   /usr/local/texlive/2022/bin/x86_64-linux/
   ```

5. Continuer la configuration selon vos préférences

---

## Configuration de LanguageTool

### Option 1 : Installation locale

1. Copiez le répertoire `LanguageTool-5.x` dans `/opt/` :

   ```bash
   sudo cp -r ~/LanguageTool-5.x /opt/
   ```

2. Dans TeXstudio, allez dans :

   `Options > Configurer TeXstudio > Contrôle de la langue > Chemin LT`

   Indiquez le chemin :

   ```
   /opt/LanguageTool-5.x/languagetool-server.jar
   ```

3. Installez une distribution Java :

   ```bash
   sudo apt install openjdk-18-jre -y
   ```

### Option 2 : Installation en ligne (Snap)

```bash
sudo snap install languagetool
```

Reprenez ensuite les procédures ci-dessus pour indiquer le chemin.

---

## Vérification des installations

### 1. Vérifier l'installation LaTeX dans TeXstudio

Dans TeXstudio : `Aide > Vérifier l'installation LaTeX`

Si tout va bien, un fichier `rapport-systeme.txt` sera créé avec le message :

> **Processus terminé normalement**

### 2. Vérifier l'installation de LanguageTool dans TeXstudio

Dans TeXstudio : `Aide > Vérifier LanguageTool`

Si tout va bien, le fichier `Rapport LT.txt` affichera :

> **Processus terminé normalement**

---

## Ressources utiles

- [TeXLive Official Site](https://www.tug.org/texlive/)
- [TeXstudio Official Site](https://www.texstudio.org/)
- [LanguageTool Official Site](https://languagetool.org/)
