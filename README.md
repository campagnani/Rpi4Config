# Rpi4Config - Configurando Raspibarry PI 4 com Debian Minimalista

Você pode executar manualmente os comandos passo-a-passo para aprender, ou executar os scripts para agilizar o processo.

## Passos iniciais

Baixe o [Debian para Raspberry](https://raspi.debian.net/daily-images/).

Baixe e instale [Balena Etcher](https://github.com/balena-io/etcher/releases), e o use para colocar o Debian em um cartão de memória.

Use gparted (ou outro programa similar) **NO SEU COMPUTADOR** para redimencionar a partição no cartão de memoria para o tamanho máximo.

OBS: Para instalar o gparted digite:

~~~Debian/Ubuntu
    sudo apt install gparted
~~~

~~~Fedora
    sudo yum install gparted
~~~

~~~Mageia
    sudo urpmi gparted
~~~

~~~OpenSUSE
    sudo zypper install gparted
~~~

~~~Windows
    Se fodeu
~~~

## Primeiro Login - Configurações basicas

Coloque o cartão de memória no seu Raspberry.

Conecte o cabo de rede.

Logue como root (não tem senha ainda).

Defina uma senha para o root:
```
    passwd
```

Adicionar seu usuario e senha:
```
    adduser pi
```

Configurando arquivo de boot:
```
    nano /boot/firmware/config.txt
```
Adicione a configuração `disable_overscan=1`

Mude o nome da máquina:
```
    nano /etc/hostname
```

Adicione o nome da máquina no arquivo host:
```
    nano /etc/hosts
```

Escolha a versão do Debian:
```
    nano /etc/apt/sources.list
```

Atualize a lista de programas:
```
    apt update
```

Atualize os programas:
```
    apt upgrade -y
```

Instale o sudo:
```
    apt install sudo -y
```

Adicione seu usuario a lista de usuários com privilégios:
```
    sudo visudo
```

Desloque do usuário root:
```
    exit
```

## Segundo Login - Interface Gráfica

Logue com seu usuario e senha.

Instale a interface grafica:

Dica: A interface LXDE é a uma das mais leves em questão de processamento e consumo de memória.

Dica2: O metapacote lxde-core é a versão minimalista do LXDE, para versão completa use o pacote lxde.

```
    sudo apt install lxde-core -y
```

Reinicie o raspberry:
```
    sudo reboot
```

## Terceiro Login - Personalização básica

Instale o tema de icones do Deepin para personalizar a interface gráfica:
```
    sudo apt install deepin-icon-theme -y
```

Baixe o tema de desktop do deepin em https://www.gnome-look.org/p/1190867/ e/ou https://www.gnome-look.org/p/1177633/ para personalizar a interface gráfica. Descompacte o arquivo e execute:
```
    sudo mv deepin-dark /usr/share/themes/
```

Vá em personalizar -> Configurações de Aparência (ou a tradução em inglês). E selecione os temas adionados.

Instale um melhor gerenciador de rede:
```
    sudo apt install network-manager network-manager-gnome -y
```

Remova o gerenciar de rede antigo:
```
    sudo apt autoremove connman-gtk -y
```

Se você quiser instale o Chromium:
```
    sudo apt install chromium -y
```

E depois, se você quiser, remova o firefox:
```
    sudo apt autoremove firefox-esr -y
```

Se quise, instale um melhor editor de textos:
```
    sudo apt install gedit -y
```

E se quiser, remove o editor de textos antigos:
```
    sudo apt autoremove mousepad -y
```

Remova programas desnecessários:
```
    sudo apt autoremove lxmusic smplayer mpv deluge -y
```

Reinicie o raspberry, e depois estará pronto para ser usado:
```
    sudo reboot                                              
```

## Quarto Login - VNC Viewer
