# Installation TexLive 2022 iso

1. Mounter l'iso (faites un clic droit et faites le choix approprié)

2. Ouvrir le terminal dans le repertoire où se trouve le fichier iso (texlive2022-20220321.iso) et installer perl-tk (nécessaire pour l'interface graphique de l'installateur)
> sudo apt install perl-tk
      
      * Créer le répertoire d'installation et modifier le propriétaire de ce dernier (ici taamangtchu devient proprietaire)

> sudo mkdir -p /usr/local/texlive/2022 && sudo chown -R taamangtchu /usr/local/texlive

## Installation en mode graphique
1. S'assurer que tk est installée 
> sudo apt install tk

> ./install-tl -gui

2. Configurer les packages à installer et lancer l'installation

## Installation en mode non graphique 
En mode rapide, utiliser un fichier profile
> ./install-tl --profile /CheminFichierProfile

Example
> ./install-tl --profile /media/nesg/NESG8GO/TEXLIVE/MyTL2022Linux.profile

## Configuration
1. Configurer la variable PATH
> gedit  ~/.bashrc

et ajouter
```bash
#>>>>>>>TexLive 2022>>>>>
PATH=/usr/local/texlive/2022/bin/x86_64-linux:>PATH; export PATH
MANPATH=/usr/local/texlive/2022/texmf-dist/doc/man:>MANPATH; export MANPATH
INFOPATH=/usr/local/texlive/2022/texmf-dist/doc/info:>INFOPATH; export INFOPATH
# <<<<<<TexLive 2022 <<<<<<<<
```

> gedit  ~/.profile

et ajouter
```bash
# >>>>>>>>>>>TeXlive>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
if [ -d "/usr/local/texlive/2022/bin/x86_64-linux" ] ; then
    PATH=">HOME/usr/local/texlive/2022/bin/x86_64-linux:>PATH"
    fi
if [ -d "/usr/local/texlive/2022/texmf-dist/doc/man" ] ; then
    MANPATH="/usr/local/texlive/2022/texmf-dist/doc/man:>MANPATH"
    fi
 if [ -d "/usr/local/texlive/2022/texmf-dist/doc/info" ] ; then
    INFOPATH="/usr/local/texlive/2022/texmf-dist/doc/info:>INFOPATH"
    fi
#<<<<<<<<<<TeXlive<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
```
Sauvegarder et fermer les fichiers.

2. Activer les changements
> source ~/.bashrc
> source ~/.profile

3. Verifier la prise en compte des changements
> echo >PATH

4. Editer `/etc/environment`

> sudo gedit /etc/environment

et ajouter
```bash
/usr/local/texlive/2022/bin/x86_64-linux:
```

Le contenu final du fichier devrait donc ressembler à cela :
```bash
PATH="/usr/local/texlive/2022/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```
5. Sauvegarder et fermer le fichier.

7. Activer les changements
> source /etc/environment

8.  Démonter l'iso en utilisant le clic droit

## Faire en sorte que Ubuntu sache que texlive est installé

> sudo apt install equivs --no-install-recommends freeglut3

> wget -O debian-equivs-2022-ex.txt https://www.tug.org/texlive/files/debian-equivs-2022-ex.txt

> equivs-build debian-equivs-2022-ex.txt

> sudo dpkg -i texlive-local_2022.99999999-1_all.deb && sudo apt install -f

* Vérifier la version de texlive installée
> tex --version

ou

> latex --version

ou
> whereis latex

et vous aurez
> latex: /usr/local/texlive/2022/bin/x86_64-linux/latex

* S'il arrive que lors de la commande pour activer TL Manager
> tlmgr --gui

affiche le message d'erreur " tlmgr: command not found", alors entrer

> sudo env PATH=">PATH" tlmgr --gui

* Pour liberer l'espace occupé par les fichiers qui s'accumulent dans le backup à la suite de diverses installations et mises à jour
> tlmgr backup --clean=0 --all

* Pour installer un package
> tlmgr install package


## Désintallation texlive2022 iso

> sudo rm -rf /usr/local/texlive/* && sudo rm -rf /usr/local/share/texmf && rm -rf ~/.texlive*


## Intallation et configuration de TeXstudio

1. Installation online
> sudo apt install texstudio

2. Installation par un fichier deb local
   * Ouvrir le terminal dans le repertoire contenant le fichier deb

   * Installer en activant les dépendances
   > sudo dpkg -i texstudioxxxxx.deb -y && sudo apt install -f -y && sudo dpkg -i texstudioxxxxx.deb -y

3. Configurer texstudio
* Indiquer le chemin où se trouve les fichiers bin de texlive. Pour cela entrer dans le terminal

> which latex

On obtient par exemple
> /usr/local/texlive/2022/bin/x86_64-linux/latex

* Demarrer TeXstudio

* Copier la sortie de "which latex", i.e. "/usr/local/texlive/2022/bin/x86_64-linux/latex" et inserer dans
`Options/Configurer TeXstudio/Production/Commandes (>PATH)`

* Continuer les configurations à sa convenance

## Configuration de LanguageTool

1. Si comme moi vous avez une version de languagetool téléchargée et contenu dans le repertoire "LanguageTool5.x" par exemple,

  * Copier ce repertoire dans `opt/`

  * Indiquer le chemin où se trouve le fichier "languagetool-server.jar"
  Pour celà, aller à "Options/Configurer TeXstudio/Contrôle la langue/Chemin LT" et insérer `opt/LanguageTool-5.x/languagetool-server.jar`.

  * Installer une distribution java, par exemple
  > sudo apt install opengdk-18-jre -y

2. Si vous devez faire plutôt une installation online, télécharger l'application en tapant
  > sudo snap install languagetool
    * Reprendre les procédures ci-dessus

3. Tester son installation de Latex dans TeXstudio
Cliquer "Aide/Verifier l'installation LaTeX"
Si tout va bien, et fichier "rapport-systeme.txt" sera créer et vous verrez "Processus terminé normalement"

4. Tester son installation de LanguageTool dans TeXstudio
Cliquer "Aide/Verifier LanguageTool"
Si tout va bien, vous verrez dans le fichier "Rapport LT.txt" et vous verrez "Processus terminé normalement"

