## Primero instalar ZSH: [[ZSH + complemento Oh-My-Zsh]]

# Como personalizar tu terminal utilizando oh-my-zsh con powerlevel10k 👨‍💻


Siempre llega el momento donde queremos personalizar nuestra terminal ya sea porque nos parece poco **atractiva** o queremos mayor **funcionalidad** para aumentar la productividad a la hora de utilizarla. Aunque el punto fuerte de las **Terminales** no sea su apartado estético ni las extensas utilidades. Pero eso no quiere decir, que no podamos hacer algo al respecto 🙋.

Para darle un **powerup** 💯 a la terminal solo necesitaremos los **siguientes requisitos**:

-   Equipo con **Sistema linux** 🐧
    -   Fedora
    -   Debian
    -   Ubuntu
    -   Arch Linux
    -   openSUSE
    -   Mint
    -   Etc...
-   **Git** 🗄️🌐

Distribución

Comando

Debian/Ubuntu

`apt-get install git`

Fedora

`yum install git` o `dnf install git`

Arch Linux

`pacman -S git`

openSUSE

`zypper install git`

FreeBSD

`pkg install git`

-   **Curl** 📂🌐

Distribución

Comando

Debian/Ubuntu

`apt-get install curl`

Fedora

`yum install curl`

Arch Linux

`pacman -Sy curl`

openSUSE

`zypper install curl`

Si ya cumples con todos los requisitos, puedes seguir con el tutorial.

---

## [](https://dev.to/christopherjael/como-personalizar-tu-terminal-utilizando-oh-my-zsh-con-powerlevel10k-4bdi#instalar-zsh)Instalar ZSH

Para instalar zsh solo tienes que abrir la terminal y escribir las siguientes líneas de comandos **(si no usas ubuntu/debian recuerda cambiar el comando para el administrador de paquetes de la distro que utilizas)**:

-   Instalar ZSH:

```
sudo apt install zsh
```

-   Comprobar la instalación de ZSH:

```
zsh --version

//zsh 5.8
```

-   Establecer ZSH como predeterminado:

```
chsh -s $(which zsh)
```

-   Cierre y vuelva abrir la terminal para verificar que ZSH este como predeterminado:

```
echo $SHELL

///usr/bin/zsh
```

Si todo va bien y no se han presentado errores, podemos seguir con el siguiente paso, instalar el administrador de **frameworks** de código abierto **Oh-my-zsh**.

---

## [](https://dev.to/christopherjael/como-personalizar-tu-terminal-utilizando-oh-my-zsh-con-powerlevel10k-4bdi#instalar-ohmyzsh)Instalar oh-my-zsh

Ejecute este comando para instalar oh-my-zsh:  

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Se mostrar la siguiente pantalla:  
[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--Ca6ktv1G--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vpq6ut4sopy0gl6mgp03.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--Ca6ktv1G--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vpq6ut4sopy0gl6mgp03.png)

Bueno ahora podemos hacer muchas cosas con oh-my-zsh instalado, una de ellas es cambiar el tema y instalar plugins.

-   Para acceder a la configuración de ZSH ejecutamos la siguiente línea de comando:

```
nano ~/.zshrc
```

-   Se abrirá el siguiente documento.

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--if_lERnq--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/v3ccgrhd8u3x2lkfueq1.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--if_lERnq--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/v3ccgrhd8u3x2lkfueq1.png)

-   Para cambiar el tema solo hay que cambiar el valor de `ZSH_THEME`, para saber la lista de temas puedes visitar el siguiente link [zsh-themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes). Solo tienes que copiar el nombre del tema y pegarlo. `ZSH_THEME = "[Nombre del tema]"`.

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--jX_cyqjV--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/04rsdcvb192xwkx5cxqe.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--jX_cyqjV--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/04rsdcvb192xwkx5cxqe.png)

-   La lista de los plugins está más abajo en el documento, por defecto solo trae el plugin de git, más adelante veremos cómo agregar más plugins.

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--724kC4yv--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/haqhmfv5wy04bqjfdzgm.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--724kC4yv--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/haqhmfv5wy04bqjfdzgm.png)

---

## [](https://dev.to/christopherjael/como-personalizar-tu-terminal-utilizando-oh-my-zsh-con-powerlevel10k-4bdi#descargar-powerlevel10k)Descargar Powerlevel10k

-   Ejecutar la siguiente línea de comandos:

```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

-   Para una buena experiencia utilizando `powerlevel10k` se recomienda la instalación de una fuente `font-nerd`, la más adecuada es la fuente `Meslo Nerd Font`. Para descargar la fuente entre a este link [Meslo-Nerd-Font](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/Meslo). Yo recomiendo descargar la fuente, Media, tipo regular, completa y compatible con sistemas windows y linux. La ruta en Github es: `nerd-fonts/patched fonts/Meslo/M/Regular/complete/`

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--ZIFfxHZS--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9uymwr2ha5s5ks9hl48q.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--ZIFfxHZS--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9uymwr2ha5s5ks9hl48q.png)

-   Para cambiar la fuente de la terminal a la nueva, Abra Terminal → Preferencias y haga clic en el perfil seleccionado en Perfiles . Marque Fuente personalizada en Apariencia del texto y seleccione `MesloLGS NF Regular`. **(Para ver algun cambio talvez tenga que reiniciar el equipo)**.

---

## [](https://dev.to/christopherjael/como-personalizar-tu-terminal-utilizando-oh-my-zsh-con-powerlevel10k-4bdi#configurar-powerlevel10k)Configurar Powerlevel10k

Hay dos formas de iniciar el proceso de configuración de `powerlevel10k`, la primera es escribiendo en la terminal `pk10 configure` y la segunda reiniciando el equipo y abriendo una terminal.

Cuando inicia con la configuración se mostrará una ventana como esta:

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--og2rGHyp--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ko6f0ve2k9khkj8e2761.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--og2rGHyp--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ko6f0ve2k9khkj8e2761.png)

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--RZscdIKJ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mn40c4g6powl36ufawl9.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--RZscdIKJ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mn40c4g6powl36ufawl9.png)

Solo tiene que seguir las instrucciones y continuar con la configuración. Escoja las opciones que desee y a disfrutar 😄.

Al final de todo le puede aparecer una terminal como esta pero no es necesario:

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--rOTdcnJK--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zubgkgu2ufi5iyq53nb5.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--rOTdcnJK--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zubgkgu2ufi5iyq53nb5.png)

A partir de ahora puede personalizar tando estetica como funcional su terminal. Recuerde que este es solo el comienzo de algo grande.

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--aDcimbRE--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sky9omaaoaptne7jtl3n.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--aDcimbRE--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sky9omaaoaptne7jtl3n.png)

---

## [](https://dev.to/christopherjael/como-personalizar-tu-terminal-utilizando-oh-my-zsh-con-powerlevel10k-4bdi#instalar-plugins-para-zsh)Instalar Plugins para ZSH

Para instalar plugins en ZSH primero hay que descargarlos e instalarlos, para ver la lista de plugins que hay disponibles visita el siguiente link [zsh-plugins](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins). Yo recomiendo instalar 2 plugins muy útiles: `zsh-syntax-highlighting` y `zsh-autosuggestions`.

### [](https://dev.to/christopherjael/como-personalizar-tu-terminal-utilizando-oh-my-zsh-con-powerlevel10k-4bdi#zshsyntaxhighlighting)zsh-syntax-highlighting

`zsh-syntax-highlighting` te muestra qué comandos están bien escritos o si existen y también los que están mal escritos o no existen.  

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--oSblI6ZT--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n6edb8in9c7lmjfl3rhd.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--oSblI6ZT--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n6edb8in9c7lmjfl3rhd.png)

### [](https://dev.to/christopherjael/como-personalizar-tu-terminal-utilizando-oh-my-zsh-con-powerlevel10k-4bdi#zshautosuggestions)zsh-autosuggestions

`zsh-autosuggestions` te muestra sugerencias y predice los que quieres hacer en base a los comandos más utilizados.  

```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--WV8lzAyQ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/anm4039oqgbq4f2km0ir.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--WV8lzAyQ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/anm4039oqgbq4f2km0ir.png)

-   Abra el documento de configuracion de ZSH:

```
nano ~/.zshrc
```

-   Añada el nombre del plugin a la lista.

```
plugins=( 
[plugins...]
zsh-syntax-highlighting
zsh-autosuggestions
)
```

[![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--NoBwKAER--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mmdmfrwlumra8vfxfg4p.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--NoBwKAER--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mmdmfrwlumra8vfxfg4p.png)

El mismo proceso se hace con la mayoría de plugins aunque hay algunos donde la instalación se realiza de otras maneras.

[[Comandos GIT]]