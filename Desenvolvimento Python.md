# Documentação para Desenvolvimento em Python

## Ambiente de Desenvolvimento

### 1. Editor de Código:

#### Visual Studio Code (VSCode)
O Visual Studio Code é um editor de código-fonte leve, poderoso e gratuito da Microsoft. Ele oferece suporte a Python por meio de extensões e fornece recursos como realce de sintaxe, depuração integrada, controle de versão e uma ampla variedade de extensões.

- **Instalação:**
  - Baixe e instale o VSCode a partir do [site oficial](https://code.visualstudio.com/).
  
- **Extensões Recomendadas para Python:**
  - **Python (Microsoft):** Fornece suporte básico para Python, incluindo realce de sintaxe, depuração e integração com ambientes virtuais.
  - **Pylance:** Melhora a experiência de autocompletar e análise estática de código em Python.
  - **Code Runner:** Permite executar código Python diretamente no editor.
  - **Jupyter (Microsoft):** Todas as extensões para uso de células interativas

### 2. Gerenciamento de Ambiente Virtual:

#### Virtualenv
Ambientes virtuais são uma prática essencial para isolar projetos Python, permitindo a gestão independente de bibliotecas e dependências. Isso evita conflitos entre diferentes projetos e garante que cada projeto possa ter suas próprias versões específicas de bibliotecas.
#### 2.1. Instalação e Criação do Ambiente Virtual

##### 2.1.1. Instalação do Ambiente Virtual

```bash
python -m venv nome_do_ambiente
```

##### 2.1.2. Ativar o Ambiente Virtual

- No Windows:

```bash
.\nome_do_ambiente\Scripts\activate
```

- No Unix ou MacOS:

```bash
source nome_do_ambiente/bin/activate
```

O ambiente virtual estará ativado quando o prompt de comando mostrar o nome do ambiente.

#### 2.2. Desativar o Ambiente Virtual

```bash
deactivate
```

Com o ambiente virtual ativado, todos os pacotes instalados serão específicos para esse ambiente.

### 3. Gerenciador de Pacotes:

#### Pip
O Pip é o gerenciador de pacotes para Python, usado para instalar e gerenciar bibliotecas e dependências.

- **Verificar a Versão do Pip:**
  ```bash
  pip --version
  ```

- **Instalar Pacotes:**
  ```bash
  pip install nome_do_pacote
  ```

- **Criar um Arquivo de Requisitos:**
  ```bash
  pip freeze > requirements.txt
  ```

- **Instalar Pacotes a partir de um Arquivo de Requisitos:**
  ```bash
  pip install -r requirements.txt
  ```