# Executando experimentos com o Docker, Tensorflow-GPU

Todos os passos abaixo foram realizados no Linux.

## Instalação do Docker

```
sudo apt update
sudo apt install docker
```

Em seguida, com o usuário administrador (root), adicione o seu nome de usuário para permitir que você roder os comandos docker sem o ```sudo```:

```
sudo groupadd docker
sudo usermod -aG docker $USER
```

Faça o login no novo grupo do docker para evitar de ter que logar/deslogar novamente:

```
newgrp docker
```

Verifique se o docker pode ser executado sem ser pelo usuário ```root```:

```
docker run hello-world
```


## Comandos básicos do Docker


## Baixando a imagem


## Criando o Dockerfile

Seja o arquivo ```script.py``` a ser executado para rodar os experimentos. Prepare o arquivo "Dockerfile" (sem formato) com o seguinte conteúdo:

```
FROM tensorflow/tensorflow:latest-gpu-py3

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Run app.py when the container launches
CMD ["python3", "script.py"]
```


