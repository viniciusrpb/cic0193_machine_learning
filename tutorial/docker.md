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


##  


