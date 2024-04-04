# Template Docker

Este é um template de como configurar o Docker de forma conveniente para o trabalho
prático de Sistemas Distribuídos e Paralelos (CCF 355), usado como material na monitoria.

## Passos

- No Linux:
    - Instalar a [Docker Engine](https://docs.docker.com/engine/install/) (**não o Docker Desktop**).
    - Por conveniência, siga os passos de [pós-instalação](https://docs.docker.com/engine/install/linux-postinstall/)
    para que você não precise usar `sudo` em cada comando:
```
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
$ shutdown --reboot now
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
- Para executar os containers deste template, execute:
```
$ docker compose build
$ docker compose up
```

> Observação: no Linux, pode ser que você precise executar o comando abaixo antes
> executar os containers para liberar o acesso do seu display ao Docker:
```
$ xhost +local:*
```

## Comandos úteis

- `docker compose up` cria e inicia os containers descritos no `docker-compose.yml`.
- `docker compose up -d` o mesmo que acima, porém faz isso em background,
liberando a janela do terminal.
- `docker compose up --build` faz o build das imagens antes de criar os containers.
Não é necessário fazer build mais de uma vez, desde que o conteúdo do `Dockerfile`
que criou aquela imagem não tenha mudado. Por exemplo, se você adicionar um novo
comando, ou uma nova dependência a ser instalada no `Dockerfile`, aí será necessário
fazer o `docker compose build` ou `docker compose up --build`. Por outro lado, se
você apenas alterou um arquivo `.py`, basta interromper e reiniciar os containers,
sem repetir o processo de build, que é demorado.
- `docker compose down` interrompe e destroi os containers descritos no `docker-compose.yml`.
Se você tiver feito alguma alteração no `docker-compose.yml`, é bom usar esse comando para
garantir que o container será recriado depois ao invés de usar alguma configuração antiga.
- `docker compose start` inicia containers já existentes.
- `docker compose stop` interromp containers sem destruí-los.
- `docker compose restart` reinicia os containers já existentes.
- `docker ps` lista os containers em execução. Exemplo:
```
$ docker ps
CONTAINER ID   IMAGE                                 COMMAND                  CREATED         STATUS         PORTS     NAMES
130b071427ac   ccf355-template-docker-server         "/bin/sh -c 'python3…"   6 minutes ago   Up 3 minutes             server
0d8dcc07299c   ccf355-template-docker-client-bob     "/bin/sh -c 'python …"   6 minutes ago   Up 3 minutes             client-bob
a55656664288   ccf355-template-docker-client-alice   "/bin/sh -c 'python …"   6 minutes ago   Up 3 minutes             client-alice
```
- `docker logs <nome-do-container>` printa os logs de um container. O nome do container
corresponde a um dos valores da última coluna do `docker ps`, que é o nome configurado
no `docker-compose.yml`, por exemplo, na linha `container_name: client-alice`.
- `docker logs <nome-do-container> --follow` printa os logs de um container e continua
acompanhando-os naquela janela do terminal. Use Ctrl+C para sair.
