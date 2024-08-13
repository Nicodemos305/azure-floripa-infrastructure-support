# Implantação de Imagem Docker no Azure Container Registry (ACR)

Siga os passos abaixo para construir e enviar uma imagem Docker para o Azure Container Registry (ACR).

## Pré-requisitos

- **Azure CLI**: Instale [aqui](https://docs.microsoft.com/pt-br/cli/azure/install-azure-cli).
- **Docker**: Instale [aqui](https://docs.docker.com/get-docker/).

## Passos

1. **Login no Azure**:
    ```bash
    az login
    ```

2. **Login no ACR**:
    ```bash
    az acr login --name <acr-name>
    ```

3. **Navegar para o diretório do Dockerfile**:
    ```bash
    cd /caminho/para/o/diretorio/do/Dockerfile
    ```

4. **Construir a imagem Docker**:
    ```bash
    docker build -t <image-name>:<tag> .
    ```

5. **Taguear a imagem para o ACR**:
    ```bash
    docker tag <image-name>:<tag> <acr-name>.azurecr.io/<image-name>:<tag>
    ```

6. **Enviar a imagem para o ACR**:
    ```bash
    docker push <acr-name>.azurecr.io/<image-name>:<tag>
    ```

7. **Verificar a imagem no ACR**:
    ```bash
    az acr repository list --name <acr-name> --output table
    ```