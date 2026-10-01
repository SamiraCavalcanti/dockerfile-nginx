# NGINX ViaCEP

Aplicação web simples para consultar endereços a partir de um CEP. A página usa jQuery e a API ViaCEP, sendo servida por um servidor NGINX em um container Docker.

## Demonstração

![Aplicação NGINX ViaCEP](/viacep.png)

## Pré-requisitos

- Docker instalado e em execução.

## Construir a imagem

No diretório do projeto, onde estão o `Dockerfile` e o `index.html`, execute:

```bash
docker build -t nginx-viacep .
```

> Para executar localmente, não é necessário colocar seu usuário do Docker Hub no nome da imagem. O usuário só é necessário quando a imagem será publicada no Docker Hub.

## Rodar o container localmente

```bash
docker run -d --name nginx-viacep -p 80:80 nginx-viacep
```

Esse comando mapeia a porta 80 do container para a porta 80 da máquina local.

Se a porta 80 já estiver ocupada, use outra porta local, por exemplo:

```bash
docker run -d --name nginx-viacep -p 8080:80 nginx-viacep
```

## Acessar no navegador

Com o mapeamento padrão, acesse:

```text
http://localhost
```

Se tiver usado a porta alternativa, acesse:

```text
http://localhost:8080
```

## Publicar no Docker Hub

Para publicar a imagem, substitua `SEU_USUARIO` pelo seu usuário do Docker Hub:

```bash
docker login
docker tag nginx-viacep SEU_USUARIO/nginx-viacep:latest
docker push SEU_USUARIO/nginx-viacep:latest
```


## Parar e remover o container

```bash
docker stop nginx-viacep
docker rm nginx-viacep
```
