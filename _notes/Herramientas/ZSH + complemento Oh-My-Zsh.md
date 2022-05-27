## Instalar ZSH en Ubuntu

Los paquetes Zsh están disponibles en los [repositorios apt predeterminados de Ubuntu.](https://noviello.it/come-usare-apt-command-su-linux) Entonces, primero, actualice el caché Apt en su sistema con los últimos paquetes disponibles:

```bash
sudo apt update
```


Luego escriba el siguiente comando para instalar los paquetes de shell zsh con las dependencias requeridas:

```bash
sudo apt install zsh
```


Una vez que se complete la instalación, verifiquemos la versión del shell Zsh instalado ejecutando el comando:

```bash
zsh --version
```


Debería ver un mensaje de salida similar al siguiente:

```output
zsh 5.8 (x86_64-ubuntu-linux-gnu)
```


## Instale el complemento Oh-My-Zsh

El [complemento On-My-Zsh](https://github.com/robbyrussell/oh-my-zsh/) proporciona una gran cantidad de personalizaciones para el shell Z. Por lo tanto, sin este complemento, el complemento Zsh está incompleto. Recomendamos instalar este complemento con el shell Zsh:

```bash
sudo apt install git-core curl fonts-powerline
```


Oh-My-Zsh proporciona un script de shell para la instalación en sistemas Linux. Ejecute el siguiente comando para instalar este complemento en su sistema:

```bash
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```


Esto le pedirá que configure Zsh como el conjunto predeterminado. Puede aceptar o rechazar, a su elección. Después de eso, la instalación se completará en segundos.

Puede elegir un tema para usar para el shell Zsh en esta [dirección](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) y luego editar el archivo `~/.zshrc`

```bash
sudo nano ~/.zshrc
```


Establezca el nombre del tema en la variable de entorno `ZSH_THEME`

```bash
# Set name of the theme to load --- if set to "random", it will
 # load a random theme each time oh-my-zsh is loaded, in which case,
 # to know which specific one was loaded, run: echo $RANDOM_THEME
 # See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

 ZSH_THEME="agnoster"
```



Guarde el archivo y ciérrelo. Luego, inicie un nuevo shell para aplicar los cambios.

## Iniciar Zsh Shell Terminal

Para iniciar un terminal de shell Zsh, simplemente escriba `zsh` desde el shell actual:

```bash
zsh
```

[[Comandos GIT]]