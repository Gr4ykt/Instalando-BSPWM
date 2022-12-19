# Instalando-BSPWM
Este es un tutorial de como instalar BSPWM con configuraciones de mi estacion de trabajo.

### nota --> COLOCAR "Instalando-BSPWM" EN EL DIRECTORIO "/home/USUARIO" para una instalacion a la par.

### PAQUETES ESCENCIALES
```shell
apt install build-essential git vim xcb libxcb-util0-dev libxcb-ewmh-dev libxcb-randr0-dev libxcb-icccm4-dev libxcb-keysyms1-dev libxcb-xinerama0-dev libasound2-dev libxcb-xtest0-dev libxcb-shape0-dev cmake cmake-data pkg-config python3-sphinx libcairo2-dev libxcb1-dev libxcb-util0-dev libxcb-randr0-dev libxcb-composite0-dev python3-xcbgen xcb-proto libxcb-image0-dev libxcb-ewmh-dev libxcb-icccm4-dev libxcb-xkb-dev libxcb-xrm-dev libxcb-cursor-dev libasound2-dev libpulse-dev libjsoncpp-dev libmpdclient-dev libuv1-dev libnl-genl-3-dev meson libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-xinerama0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev libpcre2-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev libxcb-glx0-dev imagemagick bspwm kitty rofi zsh-autosuggestions feh ranger
```
### Configuraciones e instalaciones
- [BSPWM Y SXHKD](#bspwm-y-sxhkd)
- [POLYBAR](#polybar)
- [PICOM](#picom)
- [KITTY](#kitty)
- [FEH](#feh)
- [HACKNERDFONTS](#hacknerdfonts)

# BSPWM Y SXHKD
BSPWM es la GUI que utilizaremos y SXHKD es el gestor de shortcouts que tendremos en la GUI, ejemplo abrir terminal, reiniciar BSPWM, etc.
### Instalacion

```shell
git clone https://github.com/baskerville/bspwm.git && cd bspwm && make && sudo make install
```
```shell
git clone https://github.com/baskerville/sxhkd.git && cd sxhkd && make && sudo make install
```

### Configuracion

```shell
mkdir ~/.config/bspwm && mkdir ~/.config/sxhkd
```
```shell
cp ~/Instalando-BSPWM/bspwmrc ~/.config/bspwm/bspwmrc
chmod +x ~/.config/bspmw/bspwmrc
```
```shell
cp ~/Instalando-BSPWM/sxhkdrc ~/.config/sxhkd/sxhkdrc
chmod +x ~/.config/sxhkd/sxhkdrc
```
```shell
mkdir ~/.config/bspwm/scripts/
cp ~/Instalando-BSPWM/bspwm_resize ~/.config/bspwm/scripts/
```

# POLYBAR
Barra de tareas que utilizare en BSPWM

```shell
git clone --recursive https://github.com/polybar/polybar && cd polybar
```
### Dentro de polybar descargado de github
```shell
mkdir build && cd build && cmake .. && make -j$(nproc) && sudo make install
```

# PICOM
Para la transparencia de la terminal, sombreados, etc.
```shell
git clone https://github.com/ibhagwan/picom.git && cd picom
```
### Dentro del directorio de picom de github
```shell
git submodule update --init --recursive
meson --buildtype=release . build
ninja -C build
sudo ninja -C build install
```
### Opcional --> Reiniciamos y vemos que tal va el BSPWM, pero aun nos queda configuracion de la kitty, asi que aprovechamos esto para aplicar cambios y que se creen archivos de conf.

# KITTY
```shell
cd ~/.config/kitty && cp ~/Instalando-BSPWM/kitty.conf . && cp ~/Instalando-BSPWM/color.ini .
```
# FEH
### Con feh es sencillo, ya que tan solo tendremos que colocar la wallpaper que queramos en la ruta "~/.config/bspwm/wallpaper" con el nombre "image.jpg", aunque si no es de tu gusto puedes cambiar en el archivo BSPWMRC la ruta, nombre, etc, en la cual se alojara tu wallpaper, pero esta es la predeterminada de esta conf.

# HACKNERDFONTS
### Descargamos
https://github.com/ryanoasis/nerd-fonts/releases/download/v2.2.2/Hack.zip

### Como root ejecutar lo siguiente para copiar las fonts descargadas
```shell
cd /usr/local/share/fonts && mv ~/Descargas/Hack.zip . && unzip Hack.zip && rm Hack.zip
```
