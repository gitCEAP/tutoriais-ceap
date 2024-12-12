# Workflow Genérico de CI/CD

Este workflow é configurado usando **GitHub Actions** e pode ser adaptado para projetos de diferentes linguagens de programação, como Python, Java, Node.js, JavaScript, Ruby, Go, entre outras. Ele realiza as tarefas de **Integração Contínua (CI)** e **Entrega Contínua (CD)**, garantindo que o código seja testado, validado e implantado automaticamente.

## Estrutura do Workflow

1. **CI (Integração Contínua)**:

    - Acionar a execução de testes sempre que o código for alterado.
    - Garantir que o código seja validado antes de ser integrado.

2. **CD (Entrega Contínua)**:
    - Após a validação dos testes, a aplicação é implantada automaticamente em um ambiente de produção, staging ou outro destino.

---

## 1. Configuração do Workflow no GitHub Actions

Crie um arquivo de configuração para o workflow no diretório `.github/workflows/` do seu repositório. O arquivo de workflow será no formato YAML e pode ser nomeado como `ci-cd.yml`.

```yaml
name: CI/CD Workflow

# Define quando o workflow será executado
on:
    push:
        branches:
            - main # Execute quando houver um push na branch principal (ou outras branches especificadas)
    pull_request:
        branches:
            - main # Execute quando um pull request for aberto para a branch principal

jobs:
    # Job para integração contínua (CI)
    ci:
        runs-on: ubuntu-latest # Sistema operacional para rodar o job, pode ser Windows ou macOS também

        steps:
            # Passo 1: Checkout do código
            - name: Checkout code
              uses: actions/checkout@v2

            # Passo 2: Configuração do ambiente
            - name: Set up environment
              run: |
                  # Dependendo da linguagem, defina os passos para configurar o ambiente
                  # Exemplo para Node.js (modifique conforme sua linguagem)
                  curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
                  sudo apt-get install -y nodejs

            # Passo 3: Instalar dependências
            - name: Install dependencies
              run: |
                  # Instale dependências. Modifique conforme a linguagem
                  # Exemplo para Node.js
                  npm install
                  # Exemplo para Python
                  # pip install -r requirements.txt

            # Passo 4: Executar testes
            - name: Run tests
              run: |
                  # Execute os testes. Modifique conforme a linguagem
                  # Exemplo para Node.js (usando Jest)
                  npm test
                  # Exemplo para Python (usando pytest)
                  # pytest

    # Job para entrega contínua (CD)
    cd:
        runs-on: ubuntu-latest

        needs: ci # Este job depende do sucesso do job "ci"

        steps:
            # Passo 1: Checkout do código
            - name: Checkout code
              uses: actions/checkout@v2

            # Passo 2: Configuração de ambiente para deploy (exemplo com Docker)
            - name: Set up Docker
              run: |
                  # Instalar Docker, caso necessário
                  sudo apt-get update
                  sudo apt-get install docker-ce docker-ce-cli containerd.io

            # Passo 3: Build da aplicação (com Docker como exemplo)
            - name: Build Docker image
              run: |
                  docker build -t myapp .

            # Passo 4: Push da imagem Docker para um repositório (exemplo para Docker Hub)
            - name: Push Docker image
              run: |
                  docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
                  docker tag myapp mydockerhub/myapp:latest
                  docker push mydockerhub/myapp:latest

            # Passo 5: Implantação (Deploy) para produção ou staging
            - name: Deploy to production
              run: |
                  # Comandos para deploy, por exemplo, com SSH ou Kubernetes
                  ssh user@server 'docker pull mydockerhub/myapp:latest && docker run -d mydockerhub/myapp:latest'
```

---

## 2. Explicação do Workflow

### 2.1 Triggers (`on`)

Define quando o workflow será executado:

-   `push`: Quando há um _push_ na branch principal ou em outras configuradas.
-   `pull_request`: Quando um _pull request_ é criado ou atualizado para a branch principal.

### 2.2 Jobs

-   **CI Job**: Este job realiza o processo de Integração Contínua, que pode incluir as seguintes etapas:

    -   **Checkout do código**: Faz o download do código mais recente do repositório.
    -   **Configuração do ambiente**: Dependendo da linguagem de programação, instale o runtime, ferramentas ou dependências necessárias (exemplo: Python, Node.js, etc.).
    -   **Instalação de dependências**: Instala as dependências necessárias para o projeto.
    -   **Execução de testes**: Roda os testes automatizados usando o framework apropriado (exemplo: `npm test`, `pytest`, etc.).

-   **CD Job**: Este job executa o processo de Entrega Contínua. Ele realiza as etapas para garantir que a aplicação seja construída e implantada após a aprovação na CI:
    -   **Checkout do código**: Novamente, o código é baixado para o ambiente do job.
    -   **Configuração do ambiente para deploy**: Prepara o ambiente para o processo de deploy, como a instalação do Docker ou outros componentes necessários.
    -   **Build da aplicação**: Se for o caso, construa a imagem Docker da aplicação ou qualquer outra forma de empacotamento necessária.
    -   **Push da imagem Docker**: A imagem Docker construída é enviada para o repositório (por exemplo, Docker Hub, Amazon ECR, etc.).
    -   **Deploy para produção**: Comandos para fazer o deploy da aplicação para um servidor de produção ou ambiente de staging. Isso pode ser feito via SSH, Kubernetes, ou outros métodos.

---

## 3. Variáveis de Ambiente

Para garantir que dados sensíveis, como credenciais de Docker ou tokens de API, não sejam expostos no arquivo de workflow, utilize as **Secret variables** do GitHub.

1. No repositório GitHub, vá para **Settings** > **Secrets** > **New repository secret**.
2. Adicione as variáveis de ambiente necessárias, como:
    - `DOCKER_USERNAME`
    - `DOCKER_PASSWORD`
    - `AWS_ACCESS_KEY_ID`
    - `AWS_SECRET_ACCESS_KEY`
    - etc.

Essas variáveis podem ser usadas no workflow como mostrado no exemplo.

---

## 4. Conclusão

Este workflow genérico de CI/CD pode ser adaptado para qualquer projeto de software, independentemente da linguagem de programação. Ele garante que, sempre que houver mudanças no código, o processo de integração e entrega seja realizado automaticamente, com testes rigorosos e deploy eficiente.

A flexibilidade do GitHub Actions e das ferramentas como Docker permitem que o workflow seja configurado para diferentes cenários, proporcionando um pipeline de automação robusto e seguro.
