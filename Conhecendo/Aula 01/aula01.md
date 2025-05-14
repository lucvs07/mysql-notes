
# Iniciar MySQL pela CLI (Docker)

Encontrar o diretório do docker

```sh
cd ~/Documents/docker/containers
docker compose up -d
```

Se o comando `mysql` não está sendo reconhecido no terminal, você pode acessar o MySQL no container Docker diretamente. Siga os passos abaixo:

1. Liste os containers em execução para encontrar o nome ou ID do container:

    ```sh
    docker ps
    ```

2. Acesse o container com o comando `docker exec`:

    ```sh
    docker exec -it <container_name_or_id> mysql -u root -p
    ```

    Substitua `<container_name_or_id>` pelo nome ou ID do container exibido no comando anterior.

3. Insira a senha do usuário root quando solicitado.

Se o comando `mysql` não estiver instalado no host local e você quiser usá-lo fora do container, será necessário instalá-lo no seu sistema operacional.
