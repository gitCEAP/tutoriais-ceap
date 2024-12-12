# Documentação sobre o Padrão de **Conventional Commits**

## 1. Introdução ao Padrão de Conventional Commits

O padrão de **Conventional Commits** é uma especificação para criar mensagens de commit que são estruturadas de forma padronizada. Ele foi projetado para melhorar a legibilidade dos logs de commits, garantir consistência nas mensagens e facilitar a automação de ferramentas de versionamento, como a **geração automática de changelogs** e a **gestão de versões semânticas** (SemVer).

### 1.1 Objetivo

O objetivo principal do **Conventional Commits** é fornecer uma maneira clara e consistente de escrever mensagens de commit, o que traz benefícios para a comunicação e automação de fluxos de trabalho de desenvolvimento.

---

## 2. Estrutura de uma Mensagem de Commit

Uma mensagem de commit usando o padrão **Conventional Commits** é composta por 3 partes principais:

1. **Tipo** (Obrigatório)
2. **Escopo** (Opcional)
3. **Mensagem de descrição** (Obrigatório)
4. **Corpo da mensagem** (Opcional)
5. **Rodapé** (Opcional)

A estrutura básica é:

```
<tipo>(<escopo>): <descrição>

[corpo da mensagem]

[rodapé]
```

### 2.1 Componentes Detalhados

-   **Tipo**: Define o que o commit faz. Alguns tipos comuns incluem:
    -   `feat`: Novo recurso.
    -   `fix`: Correção de bug.
    -   `docs`: Alterações na documentação.
    -   `style`: Mudanças relacionadas a estilo (ex: formatação, vírgulas, etc.).
    -   `refactor`: Refatoração de código, sem mudança de funcionalidade.
    -   `test`: Adição ou modificação de testes.
    -   `chore`: Mudanças gerais no projeto que não afetam o código ou funcionalidade.
-   **Escopo**: (Opcional) Refere-se ao contexto do commit. Pode ser o nome de um módulo, componente ou funcionalidade específica. Por exemplo: `login`, `ui`, `api`, etc.
-   **Mensagem de descrição**: Uma descrição concisa do que o commit faz. Deve ser uma frase imperativa curta, como se fosse um comando. Exemplo: "adicionar" ou "corrigir", em vez de "adicionado" ou "corrigido".

-   **Corpo da mensagem**: (Opcional) Uma explicação mais detalhada do commit. Pode incluir justificativas, explicações ou contexto adicional sobre o que foi alterado e por que.

-   **Rodapé**: (Opcional) Geralmente usado para incluir informações como referências a tickets ou problemas relacionados, como `Closes #123`, `Fixes #456`, etc.

---

## 3. Tipos de Commits Comuns

Aqui estão os principais tipos de commits que você pode usar no padrão **Conventional Commits**:

-   `feat`: Introdução de um novo recurso.
    -   Exemplo: `feat(user-auth): add login functionality`
-   `fix`: Correção de um bug.
    -   Exemplo: `fix(button): resolve issue with click handler`
-   `docs`: Alterações na documentação.
    -   Exemplo: `docs(readme): update project setup instructions`
-   `style`: Mudanças relacionadas ao estilo (sem alteração na funcionalidade do código).
    -   Exemplo: `style(layout): fix padding issues in header`
-   `refactor`: Refatoração de código sem adicionar recursos ou corrigir bugs.
    -   Exemplo: `refactor(user-auth): clean up authentication middleware`
-   `test`: Adição ou modificação de testes.
    -   Exemplo: `test(api): add tests for user endpoint`
-   `chore`: Mudanças no projeto, mas sem impacto direto no código de produção.
    -   Exemplo: `chore(deps): update dependencies to latest versions`

---

## 4. Exemplos de Mensagens de Commit

### 4.1 Commits Simples

-   `feat(auth): add OAuth login`
-   `fix(ui): resolve button alignment issue`
-   `chore(build): update build configuration`

### 4.2 Commits com Escopo e Detalhes

-   `feat(user-profile): add ability to update user profile picture`
-   `fix(api): correct validation for user input`
-   `docs(api): update documentation with new endpoints`

### 4.3 Commits com Corpo e Rodapé

-   `feat(auth): implement multi-factor authentication`

    **Corpo**:

    ```
    Adiciona suporte à autenticação de dois fatores para melhorar a segurança.
    Isso permitirá que os usuários configurem a autenticação via SMS ou e-mail.
    ```

    **Rodapé**:

    ```
    Closes #102
    ```

-   `fix(tests): update test cases for new auth API`

    **Corpo**:

    ```
    Os testes para a API de autenticação foram atualizados para refletir
    as mudanças nas rotas e parâmetros.
    ```

    **Rodapé**:

    ```
    Fixes #105
    ```

---

## 5. Como Usar o Padrão no Fluxo de Trabalho

### 5.1 Integração com Git Hooks

Para garantir que todos os commits sigam o padrão de **Conventional Commits**, você pode integrar o uso de **Git Hooks** com ferramentas como **commitizen** e **cz-customizable**. Essas ferramentas ajudam a guiar o desenvolvedor ao escrever mensagens de commit no formato correto.

#### 5.1.1 Usando Commitizen

1. **Instalar o Commitizen**:

```bash
npm install -g commitizen
```

2. **Inicializar o Commitizen**:

```bash
commitizen init cz-conventional-changelog --save-dev --save-exact
```

Isso configura o Commitizen com o adaptador **cz-conventional-changelog**, que garante que os commits sigam o padrão de Conventional Commits.

3. **Fazer Commit**:

Em vez de usar `git commit` diretamente, use o seguinte comando para ser guiado na criação do commit:

```bash
git cz
```

Isso irá abrir um prompt interativo para você selecionar o tipo, escopo e descrição do commit.

---

## 6. Benefícios do Padrão de Conventional Commits

### 6.1 Automação de Versionamento Semântico (SemVer)

Com os commits estruturados, ferramentas podem ser configuradas para gerar versões automaticamente com base nas mudanças feitas no código:

-   `feat`: Adiciona um novo recurso, que pode gerar uma nova versão minor (ex: de `1.2.0` para `1.3.0`).
-   `fix`: Corrige um bug, o que pode gerar uma nova versão patch (ex: de `1.3.0` para `1.3.1`).
-   Commits com breaking changes, como `feat(auth): add new auth flow BREAKING CHANGE: changes to the API`, podem gerar uma versão major (ex: de `1.3.1` para `2.0.0`).

### 6.2 Geração Automática de Changelog

Com as mensagens de commit padronizadas, ferramentas como **Standard Version** ou **semantic-release** podem ser usadas para gerar changelogs automaticamente, detalhando as alterações feitas no código com base nos commits.

### 6.3 Melhor Comunicação na Equipe

Mensagens de commit claras e consistentes ajudam os membros da equipe a entender rapidamente o que foi alterado, sem precisar examinar os detalhes do código.
