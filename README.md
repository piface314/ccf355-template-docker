# Template Docker

Este é um template de como configurar o Docker de forma conveniente para o trabalho
prático de Sistemas Distribuídos e Paralelos (CCF 355), usado como material na monitoria.

## Passos

- No Linux:
    - Instalar a [Docker Engine](https://docs.docker.com/engine/install/) (**não o Docker Desktop**).
    - Liberar o acesso ao gerenciador de janelas para os containers:
```
$ xhost +local:*
```
- No Windows:
    - Instalar o [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/).
    - É necessário instalar um X11 Display Server, como o [VcXsrv](https://sourceforge.net/projects/vcxsrv/).
    - Siga as instruções [deste artigo](https://medium.com/@saicoumar/running-linux-guis-in-a-docker-container-73fef186db30),
    na seção "X11 Display Server Configuration on Windows".
- Certificar que a instalação está funcionando com o comando:
```
$ docker run hello-world
```
