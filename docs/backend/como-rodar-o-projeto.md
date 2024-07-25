---
sidebar_position: 1
---

# Como iniciar o projeto

# Gerenciador de Projetos e Atividades

Bem-vindo ao repositório do projeto **Gerenciador de Projetos e Atividades**. Este projeto é uma aplicação backend desenvolvida em NestJS para gerenciar projetos e atividades, utilizando Prisma para gerenciamento de banco de dados e seguindo boas práticas de desenvolvimento.

## Estrutura de Pastas

## Instalação

1. Clone o repositório:

   ```bash
   git clone https://github.com/seu-usuario/nome-do-repositorio.git
   ```

2. Entre na pasta do projeto:

   ```bash
   cd nome-do-repositorio
   ```

3. Instale as dependências:

   ```bash
   npm install
   ```

4. Configure as variáveis de ambiente:

   - Copie o arquivo `.env.example` e renomeie para `.env`.
   - Edite o arquivo `.env` com as configurações necessárias.

5. Execute as migrações do banco de dados:
   ```bash
   npx prisma migrate dev
   ```

## Uso

Para iniciar a aplicação em modo de desenvolvimento:

```bash
npm run start:dev
```

Para compilar a aplicação:

```bash
npm run build
```

Para iniciar a aplicação em modo de produção:

```bash
npm run start:prod
```

## Testes

Para rodar os testes:

```bash
npm run test
```

Para rodar os testes com cobertura:

```bash
npm run test:cov
```

### Com Docker

1. **Crie a Imagem Docker:**

   No diretório raiz do seu projeto, execute o seguinte comando:

   ```bash
   docker-compose build
   ```

2. **Execute o Contêiner:**

   Após a construção da imagem, inicie o contêiner com:

   ```bash
   docker-compose up
   ```

   O Nest.js estará disponível na porta `3333` do seu localhost. Acesse [http://localhost:3333](http://localhost:3333) para ver seu projeto em execução.

## Contribuição

Sinta-se à vontade para contribuir com o projeto. Abra uma issue ou envie um pull request no GitHub.

## Licença

Este projeto está licenciado sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

**Nota**: Certifique-se de atualizar os links e comandos conforme necessário para seu projeto específico.
