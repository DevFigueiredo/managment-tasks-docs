---
sidebar_position: 2
---

# Arquitetura de Pastas

## Arquitetura de Pastas do Frontend

A estrutura de pastas do projeto frontend é projetada para proporcionar uma organização clara e eficiente, facilitando a manutenção e a escalabilidade do código. A seguir, uma visão geral das principais pastas e arquivos:

### Estrutura de Pastas

Abaixo está a estrutura de pastas do projeto, juntamente com a descrição da finalidade de cada pasta:

```plaintext
.
├── .github
│   └── workflows
│       └── develop.yaml        # Configurações de workflows do GitHub Actions para CI/CD.
├── .vscode
│   └── settings.json           # Configurações do Visual Studio Code para o projeto.
├── coverage                    # Relatórios de cobertura de testes.
├── dist                        # Arquivos compilados da aplicação.
├── node_modules                # Dependências do projeto gerenciadas pelo npm.
├── src
│   ├── modules                 # Módulos da aplicação, divididos por funcionalidades.
│   │   ├── project             # Módulo de gerenciamento de projetos.
│   │   │   ├── infra           # Infraestrutura relacionada ao módulo de projetos.
│   │   │   ├── use-cases       # Casos de uso do módulo de projetos.
│   │   │   │   ├── create-project
│   │   │   │   ├── delete-project
│   │   │   │   ├── get-detail-projects
│   │   │   │   ├── get-projects
│   │   │   │   │   ├── get-projects.use-case.dto.ts
│   │   │   │   │   ├── get-projects.use-case.spec.ts
│   │   │   │   │   ├── get-projects.use-case.ts
│   │   │   │   ├── update-project
│   │   │   └── project.module.ts # Configuração do módulo de projetos.
│   │   ├── status               # Módulo de gerenciamento de status.
│   │   ├── task                 # Módulo de gerenciamento de tarefas.
│   ├── shared                   # Código compartilhado entre os módulos.
│   │   ├── config               # Configurações gerais da aplicação.
│   │   ├── docs                 # Documentação da aplicação.
│   │   ├── domain               # Entidades de domínio.
│   │   ├── filters              # Filtros globais da aplicação.
│   │   ├── infra                # Infraestrutura compartilhada.
│   │   │   └── database
│   │   │       └── prisma       # Configuração e arquivos do Prisma ORM.
│   │   │           ├── migrations
│   │   │           ├── seeds
│   │   │           ├── dev.db
│   │   │           ├── index.ts
│   │   │           └── schema.prisma
│   │   ├── middlewares          # Middlewares globais.
│   │   └── utils                # Funções utilitárias.
│   │       ├── enums            # Definições de enums.
│   │       ├── calculate-percentage.spec.ts
│   │       ├── calculate-percentage.ts
│   │       ├── check-if-delayed.spec.ts
│   │       ├── check-if-delayed.ts
│   │       ├── create-server.ts
│   │       ├── date-now.spec.ts
│   │       ├── date-now.ts
│   │       ├── generate-uuid.spec.ts
│   │       ├── generate-uuid.ts
│   │       └── logger.ts
│   ├── app.module.ts            # Módulo raiz da aplicação.
│   └── main.ts                  # Arquivo de inicialização da aplicação.
├── test                         # Testes automatizados.
├── .env                         # Arquivo de configuração de ambiente.
├── .env.example                 # Exemplo de arquivo de configuração de ambiente.
├── .eslintrc.js                 # Configurações do ESLint.
├── .gitignore                   # Arquivos e pastas ignorados pelo Git.
├── .prettierrc                  # Configurações do Prettier.
├── Dockerfile                   # Dockerfile para criação da imagem Docker.
├── nest-cli.json                # Configurações do Nest CLI.
├── package-lock.json            # Arquivo de lock das dependências npm.
├── package.json                 # Dependências e scripts do projeto.
├── README.md                    # Documentação principal do projeto.
├── tsconfig.build.json          # Configurações de build do TypeScript.
└── tsconfig.json                # Configurações do TypeScript.
```
