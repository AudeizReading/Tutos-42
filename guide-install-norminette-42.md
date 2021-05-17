Guide d'installation de la norminette
=========================

Mise à disposition par 42School à l'url <https://github.com/42School/norminette>
-----------------------------------------------------------------------------------------------

Attention ce guide est à l'intention des utilisateurs de la WSL Debian/Ubuntu
(Appli Ubuntu sours Windows 10), sans doute transposable pour les purs Linuxiens
sous Debian. Pour ceux sous Mac, vous m'en voyez navrée... Mais démerdez-vous !!!!

+ Choisir le répertoire de destination :
```shell
mkdir REP_DEST
```
+ Récupérer le dépôt git (3 possibilités):
    1. Download le zip mis à dispo sur github.
    2. git clone le repo en https
    3. git clone le repo en ssh
Perso, je clone en ssh, mais vous retrouvez facilement la procédure sur github
pour se mettre en ssh ou https. Le plus simple est de download le zip et de `tar -xvf repo.tar REP_DEST`
```shell
git clone git@github.com:42School/norminette.git REP_DEST
cd REP_DEST
```
+ Suive la procédure donnée sur le compte git de 42School
Attention, il se peut que le module `pip` de python3 ne soit pas installé par
défaut sous WSL :

```shell
sudo apt-get install python3-pip
```
Une autre solution pour récupérer `pip` (mais n'a pas fonctionné dans mon cas):
```shell
python -m ensurepip --default-pip
```
Procédure d'installation:
```shell
python3 -m pip install --upgrade pip setuptools [testresources]
python3 -m pip install norminette
```

Le paquet `testresources` est entre crochets pour noter le caractère facultatif du
paramètre, perso il a fallu que je rajoute ce module car il était manquant sur ma
distro, mais tout le monde ne sera pas concerné, ne le rajouter que si on vous
le demande.

+ Ensuite python demande à ce que le répertoire $HOME/.local/bin soit ajouté à la
variable $PATH. Le programme `norminette` se trouve dans `$HOME/.local/bin`. 2
solutions sont possibles :
    1. Editer sa variable `$PATH` dans son fichier de configuration `.bashrc` (à la
       racine du répertoire `$HOME` ou `~`, si vous utilisez zsh, alors c'est le
       fichier `.zshrc` qu'il faut éditer, voire créer si inexistant)
    ```shell
    export PATH="$HOME/.local/bin:$PATH"
    ```
    2. Ou alors, on créé un lien symbolique de `$HOME/.local/bin` vers un
       répertoire déjà inclus dans le $PATH, `/usr/bin` par exemple :
    ```shell
    sudo ln -s ~/.local/bin /usr/bin
    ```
+ Relancer le terminal. Normalement, c'est bon vous pouvez utiliser la
  **norminette** peut importe où vous vous situez dans votre arborescence.
  Normalement, vous connaissez déjà l'utilisation d'un exécutable, depuis son
  répertoire, de cette façon :
  ```shell
  ./norminette
  ```
  Ici, vous n'aurez qu'à faire :
  ```shell
  norminette
  ```
  Et ce depuis n'importe quel répertoire où vous vous situez !

  Enjoy norminette !