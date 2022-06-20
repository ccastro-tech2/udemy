# Docker 
## Read Me - Daily 

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


- Type some Markdown on the left
- See HTML in the right
- ✨Magic ✨

## Comandos Tips

- sudo service docker start | status | restart
- Docker info
- Listando Containers ativos -> docker ps
- Listando todos os Containers inclusive as paradas -> docker ps -a
- docker images 
- docker pull ubuntu:10.04
- docker search wordpress

## Inspecionando Imagens
- docker inspect
- docker inspect --format '{{.id}}' CONTAINER_ID
- docker inspect --format '{{.NetworkSettingsIPAddress}}' CONTAINER_ID
- docker diff CONTAINER_ID
- docker logs CONTAINER_ID

## Exportando imagem en .tar
```sh
docker export -o /tmp/container_$NAME_$TAG.tar CONTAINER_ID
```

## importando imagem en .tar
```sh
cat /tmp/container_$NAME_$TAG.tar | docker import - $aula-ex01:v1
```
```sh
docker run -dt --name aula-ex01-b aula-ex01:v1 /bin/bash
```
As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's


text....

## Criando Containers
Obs.: Containers são baseados em images
docker run --name exemplo1 -d -t ubuntu
docker unpause exemplo1
docker cp exemplo6:/tmp/ .
Os parâmetros mais utilizados na execução do container são:

Parâmetro	Explicação
- [-d]..Execução do container em background
- [-i]..Modo interativo. Mantém o STDIN aberto mesmo sem console anexado
- [-t]..Aloca uma pseudo TTY
- [--rm]..Automaticamente remove o container após finalização (Não funciona com -d)
- [--name]..Nomear o container
- [-v]..Mapeamento de volume
- [-p]..Mapeamento de porta
- [-m]..imitar o uso de memória RAM
- [-c]..Balancear o uso de CPU
- [run] corre comando
- [name] - awesome web-based text editor
- 
- [-d] modo deamon. detache
- [-t] - great UI boilerplate for modern web apps
- [-i] iterativo
- [ubuntu] - evented I/O for the backend
- [/bin/bash] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
- to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Comandos dentro do container docker exec 

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
docker exec exemplo1 ps ax
docker exec exemplo2 kill -9 19
docker stop exemplo2.0 exemplo2.1
docker start exemplo3
```

## DockerFiles
```sh
FROM nginx
RUN sed -i 's/Welcome to nginx!/Bem vindo ao Exemplo 5 <br>via Dockerfile/g' /usr/share/nginx/html/index.html
```
```sh
docker build -t nginx_exemplo_5:v1 .
```
```sh
FROM nginx
RUN sed -i 's/Welcome to nginx!/Bem vindo ao Exemplo 5 <br>via Dockerfile/g' /usr/share/nginx/html/index.html
RUN ls '/tmp'
```
```sh
docker build -t nginx_exemplo_5:v2 .
```
Obs
> Com o build criado pode reutilizar a imagem ultilizada modificando o nome no FROM


## IMAGES
```sh
docker images
docker pull ubuntu:14.04
docker run --name exemplo3 -d -t -p80:80 nginx 1º80 é a local, 2º 80 port container
docker exec exemplo2 kill -9 19
```

## IMAGES RM

```sh
docker rm container_id
docker rmi name -force
docker run --name exemplo3 -d -t -p80:80 nginx 1º80 é a local, 2º 80 port container
docker exec exemplo2 kill -9 19
```
## Docker Ports
- [multi ports] 

```sh
docker run -dt --name exemplo01 -p 54-55:54-55/udp -p 192.168.0.110:100:101/tcp -p 86-89:91-99 ubuntu /bin/bash
```
## Volume -v
| exec | README |
| ------ | ------ |
| :ro | Read-only |
| aula_21 | RedMine + mysql + link + Containers + deploy |
| exec3 | [plugins/googledrive/README.md][PlGd] |
| exec4 | [plugins/onedrive/README.md][PlOd] |
| exec5 | [plugins/medium/README.md][PlMe] |
| exec5  | [plugins/googleanalytics/README.md][PlGa] |
```sh
docker run -dt --name exemplo02 -P nginx-emeplo02:v3 /bin/bash
```

```sh
docker run -dt --name exemplo02 -P nginx-emeplo02:v3 -v /Desktop/docker/volume:/tmp/docker/volumes /bin/bash
```

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
