---
sidebar_position: 3
---

# Integração Contínua e Entrega Contínua (CI/CD)

## Visão Geral

O processo de Integração Contínua (CI) e Entrega Contínua (CD) é automatizado utilizando GitHub Actions para garantir que as alterações no código sejam construídas, testadas e implantadas de maneira eficiente e confiável. Este fluxo de trabalho é essencial para manter a qualidade e a estabilidade do código ao longo do ciclo de vida do desenvolvimento.

### Workflow: `Build, Test, and Deploy - DEV`

Este workflow é acionado quando há um push para o branch `develop`. Ele é dividido em duas principais etapas: **Build and Test** e **Deploy**.

## Etapa 1: Build and Test

### Objetivo

Compilar o projeto, executar testes unitários e preparar o projeto para a implantação.

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

   Configura o ambiente Node.js para a versão especificada (18 neste caso).

3. **Install dependencies**

   ```yaml
   - name: Install dependencies
     run: npm install
   ```

   Instala todas as dependências do projeto.

4. **Run unit tests**

   ```yaml
   - name: Run unit tests
     run: npm run test:cov
   ```

   Executa os testes unitários e gera um relatório de cobertura.

5. **Build project**
   ```yaml
   - name: Build project
     run: npm run build
   ```
   Compila o projeto para produção.

## Etapa 2: Deploy

### Objetivo

Construir e enviar a imagem Docker para o Docker Hub, executar migrações e sementes no banco de dados, e acionar a implantação.

### Passos

1. **Check out code**

   ```yaml
   - name: Check out code
     uses: actions/checkout@v2
   ```

   Novamente, faz o checkout do código-fonte para a etapa de implantação.

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

   Faz login no Docker Hub utilizando credenciais armazenadas como segredos.

4. **Build and push Docker image**

   ```yaml
   - name: Build and push Docker image
     run: |
       docker build -t danielfigueiredo/managment-tasks-backend:${{env.VERSION}} .
       docker push danielfigueiredo/managment-tasks-backend:${{env.VERSION}}
   ```

   Constrói a imagem Docker e a envia para o Docker Hub.

5. **Run database migrations**

   ```yaml
   - name: Run database migrations
     run: |
       docker run --rm \
         -e DATABASE_URL=${{ secrets.DATABASE_URL }} \
         danielfigueiredo/managment-tasks-backend:${{env.VERSION}} \
         npx prisma migrate deploy
   ```

   Executa as migrações do banco de dados usando o Prisma.

6. **Run database seeds**

   ```yaml
   - name: Run database seeds
     run: |
       docker run --rm \
         -e DATABASE_URL=${{ secrets.DATABASE_URL }} \
         danielfigueiredo/managment-tasks-backend:${{env.VERSION}} \
         npm run seed:run
   ```

   Executa os seeds no banco de dados.

7. **Deploy (Webhook Trigger - Render)**

   ```yaml
   - name: Deploy (Webhook Trigger - Render)
     if: github.ref == 'refs/heads/develop'
     env:
       deploy_url: ${{ secrets.RENDER_DEPLOY_HOOK_URL }}
     run: |
       curl "$deploy_url"
   ```

   Aciona o webhook de implantação na Render para atualizar o ambiente de produção.

8. **Deploy URL**
   ```yaml
   - name: Deploy URL
     run: echo "https://managment-tasks-backend-latest.onrender.com"
   ```
   Exibe a URL do ambiente de produção atualizado.
