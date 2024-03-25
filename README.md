# Template Docker

Este é um template de como configurar o Docker de forma conveniente para o trabalho
prático de Sistemas Distribuídos e Paralelos (CCF 355), usado como material na monitoria.

## Passos no Linux

- Instalar a [Docker Engine](https://docs.docker.com/engine/install/) (**não o Docker Desktop**).
- Certificar que a instalação está funcionando com o comando:
```
$ docker run hello-world
```
- No Linux, você deve liberar o acesso ao gerenciador de janelas para os containers:
```
$ xhost +local:*
```
- No Windows, é necessário ter um X-server, como o [VcXsrv](https://sourceforge.net/projects/vcxsrv/).
    - Siga as instruções [deste artigo](https://medium.com/@saicoumar/running-linux-guis-in-a-docker-container-73fef186db30),
    na seção "X11 Display Server Configuration on Windows".