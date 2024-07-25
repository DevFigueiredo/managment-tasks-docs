---
sidebar_position: 3
---

# Integração Contínua e Entrega Contínua (CI/CD) - Frontend

## Visão Geral

O fluxo de trabalho de Integração Contínua (CI) e Entrega Contínua (CD) para o frontend do projeto é automatizado usando GitHub Actions. Este processo garante que o código seja construído, testado e implantado de forma eficiente sempre que há um push para o branch `develop`.

### Workflow: `Build and Deploy - DEV`

Este workflow é projetado para compilar o projeto e fazer o deploy da versão mais recente para o ambiente de desenvolvimento. Ele é dividido em duas etapas principais: **Build and Test** e **Deploy**.

## Etapa 1: Build and Test

### Objetivo

Preparar o projeto para a implantação compilando o código-fonte e garantindo que ele esteja pronto para ser enviado ao ambiente de produção.

### Passos

1. **Check out code**

   ```yaml
   - name: Check out code
     uses: actions/checkout@v2
   ```

   Este passo faz o checkout do código-fonte do repositório para o ambiente de execução.

2. **Set up Node.js**

   ```yaml
   - name: Set up Node.js
     uses: actions/setup-node@v3
     with:
       node-version: "18"
   ```

   Configura o ambiente Node.js para a versão 18, que é a versão utilizada para construir o projeto.

3. **Install dependencies**

   ```yaml
   - name: Install dependencies
     run: npm install
   ```

   Instala todas as dependências necessárias para o projeto.

4. **Build project**
   ```yaml
   - name: Build project
     run: npm run build
   ```
   Compila o projeto, preparando-o para a implantação.

## Etapa 2: Deploy

### Objetivo

Construir e enviar a imagem Docker para o Docker Hub e realizar a implantação no ambiente de desenvolvimento.

### Passos

1. **Check out code**

   ```yaml
   - name: Check out code
     uses: actions/checkout@v2
   ```

   Faz o checkout do código-fonte novamente para a etapa de implantação.

2. **Set up Docker Buildx**

   ```yaml
   - name: Set up Docker Buildx
     uses: docker/setup-buildx-action@v1
   ```

   Configura o Docker Buildx para construir imagens multi-plataforma.

3. **Log in to Docker Hub**

   ```yaml
   - name: Log in to Docker Hub
     uses: docker/login-action@v1
     with:
       username: ${{ secrets.DOCKER_USERNAME }}
       password: ${{ secrets.DOCKER_PASSWORD }}
   ```

   Faz login no Docker Hub utilizando as credenciais armazenadas como segredos.

4. **Build and push Docker image**

   ```yaml
   - name: Build and push Docker image
     run: |
       docker build -t danielfigueiredo/managment-tasks-frontend:${{env.VERSION}} .
       docker push danielfigueiredo/managment-tasks-frontend:${{env.VERSION}}
   ```

   Constrói a imagem Docker do frontend e a envia para o Docker Hub.

5. **Deploy (Webhook Trigger - Render)**

   ```yaml
   - name: Deploy (Webhook Trigger - Render)
     if: github.ref == 'refs/heads/develop'
     env:
       deploy_url: ${{ secrets.RENDER_DEPLOY_HOOK_URL }}
     run: |
       curl "$deploy_url"
   ```

   Aciona o webhook de implantação na Render para atualizar o ambiente de desenvolvimento com a nova versão.

6. **Deploy URL**
   ```yaml
   - name: Deploy URL
     run: echo "https://managment-tasks-frontend-latest.onrender.com"
   ```
   Exibe a URL do ambiente de desenvolvimento atualizado.
