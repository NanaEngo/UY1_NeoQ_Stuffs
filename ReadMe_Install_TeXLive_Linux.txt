%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Installation TexLive 2022 iso
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

NB: Si vous êtes sous Ubuntu, utilisez l'éditeur de texte "gedit" (environment gnome) la place de "kate" (environment KDE) dans ce qui suit.


1. Créer le répertoire d'installation et modifier le propriétaire de ce dernier

$ sudo mkdir -p /usr/local/texlive/2022 && sudo chown -R taamangtchu /usr/local/texlive

2. Mounter l'iso 

$ mount -t iso9660 -o ro,loop,noauto /chemin/texlive2022-20220321.iso /mnt

Ou mounter l'iso à travers l'explorateur 

3. Installer en mode graphique S'assurer que tk est installée (sudo apt install tk)
$ cd /mnt
$ ./install-tl -gui

configurer les packages à installer et lancer l'installation

4. Configurer la variable PATH
$ kate  ~/.bashrc

et ajouter

#>>>>>>>TexLive 2022>>>>>
PATH=/usr/local/texlive/2022/bin/x86_64-linux:$PATH; export PATH
MANPATH=/usr/local/texlive/2022/texmf-dist/doc/man:$MANPATH; export MANPATH
INFOPATH=/usr/local/texlive/2022/texmf-dist/doc/info:$INFOPATH; export INFOPATH
# <<<<<<TexLive 2022 <<<<<<<<

$ kate  ~/.profile

et ajouter

# >>>>>>>>>>>TeXlive>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
if [ -d "/usr/local/texlive/2022/bin/x86_64-linux" ] ; then
    PATH="$HOME/usr/local/texlive/2022/bin/x86_64-linux:$PATH"
    fi
if [ -d "/usr/local/texlive/2022/texmf-dist/doc/man" ] ; then
    MANPATH="/usr/local/texlive/2022/texmf-dist/doc/man:$MANPATH"
    fi
 if [ -d "/usr/local/texlive/2022/texmf-dist/doc/info" ] ; then
    INFOPATH="/usr/local/texlive/2022/texmf-dist/doc/info:$INFOPATH"
    fi
#<<<<<<<<<<TeXlive<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

Sauvegarder et fermer les fichiers. 

5. Activer les changements
$ source ~/.bashrc
$ source ~/.profile

6. Verifier la prise en compte des changements
$ echo $PATH

7. Ajouter  

$ kate /etc/environment

Ajouter

/usr/local/texlive/2022/bin/x86_64-linux:

# Le contenu final du fichier devrait donc ressembler à cela :

PATH="/usr/local/texlive/2022/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"

8. Sauvegarder et fermer le fichier. 

9. Activer les changements
$ source /etc/environment

10. Démonter l'iso
$ cd ~
$ sudo umount /mnt

11. Faire en sorte que Ubuntu sache que texlive est installé
$ sudo apt install equivs --no-install-recommends freeglut3
$ wget -O debian-equivs-2022-ex.txt 
https://www.tug.org/texlive/files/debian-equivs-2022-ex.txt

$ equivs-build debian-equivs-2022-ex.txt
$ sudo dpkg -i texlive-local_2022.99999999-1_all.deb
$ sudo apt install -f

12. S'il arrive que lors de la commande pour activer TL Manager
$ tlmgr --gui

affiche le message d'erreur " tlmgr: command not found", alors entrer

$ sudo env PATH="$PATH" tlmgr --gui

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Désintallation texlive2022 iso
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

$ sudo rm -rf /usr/local/texlive/* && sudo rm -rf /usr/local/share/texmf && rm -rf ~/.texlive*

