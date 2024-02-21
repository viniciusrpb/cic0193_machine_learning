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

Verificar todas as imagens:

```
docker image ls
```

Verificar todos os containers:

```
docker container ls
```

Limpeza do espaço em disco:

```
docker builder prune
```

## Criando o Dockerfile

Prepare um arquivo denominado "Dockerfile" em um editor de texto de sua preferência, sem formato e exatamente com esse nome, com o seguinte conteúdo:

```
FROM tensorflow/tensorflow:latest-gpu

RUN mkdir /app

WORKDIR /app

COPY . /app

# baixar o arquivo da versao Python 3.10
RUN wget https://www.python.org/ftp/python/3.10.2/Python-3.10.2.tgz && \
    tar -xzf Python-3.10.2.tgz && \
    cd Python-3.10.2 && \
    ./configure --enable-optimizations && \
    make install

# instalacao das APIs para deep learning

RUN pip install --upgrade pip

RUN pip install pandas

RUN pip install scikit-learn

RUN pip install matplotlib

RUN pip install tensorflow_addons

RUN pip install keras-tuner

RUN pip install opencv-python

RUN pip install opencv-python-headless

CMD [ "python", "arquivo.py"]
```

Observe que há uma atualização da versão do Python dentro do container Docker. Esse Dockerfile já emprega uma imagem de base do tensorflow com suporte para GPU. O arquivo ``arquivo.py'' é o arquivo Python a ser executado, e que deve ter os experimentos.

Deixe o Dockerfile dentro da pasta em que você quer rodar os experimentos. Em seguida, é hora de fazer o build da imagem. No Terminal do Linux, digite:

```
docker build -t NOME_CONTAINER .
```
Digite o comando

![Docker Images](imgs/docker_images.png)

Finalmente, para rodar o container Docker em modo *foreground*, utilize o comando:

```
docker run NOME_CONTAINER:TAG
```

Caso queira rodar o container Docker em modo *background*, utilize o comando:

```
docker run -d NOME_CONTAINER:TAG
```



