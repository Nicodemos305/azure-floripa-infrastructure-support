# Use uma imagem base do Ubuntu
FROM ubuntu:20.04

# Defina variáveis de ambiente para suprimir prompts interativos
ENV DEBIAN_FRONTEND=noninteractive

# Atualize o sistema e instale dependências básicas, incluindo o Vim
RUN apt-get update && apt-get install -y \
    curl \
    gnupg2 \
    lsb-release \
    software-properties-common \
    unzip \
    apt-transport-https \
    ca-certificates \
    vim \
    && rm -rf /var/lib/apt/lists/*

# Instale o Terraform
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - \
    && apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" \
    && apt-get update && apt-get install -y terraform

# Instale o Terragrunt
RUN curl -L https://github.com/gruntwork-io/terragrunt/releases/download/v0.50.4/terragrunt_linux_amd64 -o /usr/local/bin/terragrunt \
    && chmod +x /usr/local/bin/terragrunt

# Instale o Azure CLI
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# Defina o diretório de trabalho
WORKDIR /workspace

# Comando padrão para o container
CMD ["bash"]
