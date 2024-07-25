---
sidebar_position: 2
---

# Arquitetura de Pastas

## Arquitetura de Pastas do Frontend

A estrutura de pastas do projeto frontend é projetada para proporcionar uma organização clara e eficiente, facilitando a manutenção e a escalabilidade do código. A seguir, uma visão geral das principais pastas e arquivos:

### Estrutura de Pastas

```plaintext
.
├── .github
│   └── workflows
│       └── develop.yaml        # Configurações dos workflows do GitHub Actions para CI/CD.
├── .next                        # Arquivos gerados pelo Next.js, como builds e cache.
├── .vscode                      # Configurações específicas do Visual Studio Code.
├── node_modules                 # Dependências do projeto gerenciadas pelo npm.
├── public                       # Arquivos estáticos públicos, como ícones e imagens.
├── src
│   ├── @core                    # Arquivos e configurações centrais do projeto.
│   ├── app                      # Estrutura principal do aplicativo Next.js.
│   │   ├── auth                 # Páginas e componentes relacionados à autenticação.
│   │   │   ├── home
│   │   │   │   └── page.tsx    # Página inicial da autenticação.
│   │   │   ├── project          # Componentes e páginas para gerenciamento de projetos.
│   │   │   └── layout.tsx       # Layout comum para as páginas de autenticação.
│   │   ├── favicon.ico           # Ícone do aplicativo.
│   │   ├── globals.css           # Estilos globais da aplicação.
│   │   ├── layout.tsx            # Layout principal da aplicação.
│   │   ├── not-found.tsx         # Página exibida quando uma página não é encontrada.
│   │   └── providers.tsx         # Provedores de contexto para o aplicativo.
│   ├── components               # Componentes reutilizáveis da aplicação.
│   │   ├── ControlledDate       # Componente para seleção de datas.
│   │   ├── ControlledInput      # Componente para inputs controlados.
│   │   ├── ControlledTextArea   # Componente para áreas de texto controladas.
│   │   ├── CreateProjectModal   # Modal para criação de projetos.
│   │   ├── CustomButton         # Botão personalizado.
│   │   ├── DeleteProjectModal   # Modal para exclusão de projetos.
│   │   ├── DetailTaskDrawer     # Componente para visualização detalhada de tarefas.
│   │   ├── EditableTask         # Componente para edição de tarefas.
│   │   ├── Header               # Cabeçalho da aplicação.
│   │   ├── NavItem              # Item de navegação.
│   │   ├── ProjectList          # Lista de projetos.
│   │   └── Sidebar              # Barra lateral de navegação.
│   ├── contexts                 # Contextos React para gerenciamento de estado global.
│   │   ├── ProjectContext.tsx   # Contexto para gerenciamento de projetos.
│   │   └── TaskContext.tsx      # Contexto para gerenciamento de tarefas.
│   ├── hooks                    # Hooks personalizados.
│   │   ├── useProject.ts        # Hook para funcionalidades relacionadas a projetos.
│   │   ├── useStatus.ts         # Hook para funcionalidades relacionadas a status.
│   │   └── useTask.ts           # Hook para funcionalidades relacionadas a tarefas.
│   ├── utils                    # Funções utilitárias e auxiliares.
│   │   ├── generate-uuid.ts     # Função para geração de UUIDs.
│   │   ├── logger.ts            # Função para logging.
│   │   ├── reorder.ts           # Função para reordenar itens.
│   │   ├── routes.ts            # Funções relacionadas às rotas da aplicação.
│   │   └── status.enum.ts       # Enum para status utilizados na aplicação.
│   ├── middleware.ts            # Middleware da aplicação Next.js.
├── .env                         # Arquivo de variáveis de ambiente para configuração local.
├── .env.example                 # Exemplo de arquivo de variáveis de ambiente.
├── .eslintrc.json               # Configurações do ESLint.
├── .gitignore                   # Arquivos e pastas a serem ignorados pelo Git.
├── docker-compose.yml           # Configuração para o Docker Compose.
├── Dockerfile                   # Dockerfile para construir a imagem do Docker.
├── next-env.d.ts                # Declarações de tipos para o Next.js.
├── next.config.mjs              # Configurações do Next.js.
├── package-lock.json            # Controle de versão das dependências do npm.
├── package.json                 # Gerenciamento das dependências do projeto.
├── postcss.config.mjs           # Configuração do PostCSS.
├── README.md                    # Documentação do projeto.
├── tailwind.config.ts           # Configuração do Tailwind CSS.
└── tsconfig.json                # Configurações do TypeScript.
```

### Explicação das Pastas e Arquivos

- **`@core`**: Contém arquivos e configurações centrais para a aplicação, como contextos e provedores globais.
- **`app`**: Estrutura principal do Next.js, incluindo páginas e layouts.
  - **`auth`**: Páginas e layouts relacionados à autenticação.
  - **`favicon.ico`**: Ícone do aplicativo.
  - **`globals.css`**: Estilos globais aplicados a toda a aplicação.
  - **`layout.tsx`**: Layout principal para a aplicação.
  - **`not-found.tsx`**: Página para rotas não encontradas.
  - **`providers.tsx`**: Fornecedores de contexto para a aplicação.
- **`components`**: Componentes reutilizáveis, como botões, modais e cabeçalhos.
- **`contexts`**: Contextos React para gerenciamento de estado global, como projetos e tarefas.
- **`hooks`**: Hooks personalizados para encapsular lógica reutilizável.
- **`utils`**: Funções utilitárias para diversas operações.
- **`middleware.ts`**: Middleware para interceptar e processar requisições.
- **`.env` e `.env.example`**: Arquivos de configuração de ambiente.
- **`docker-compose.yml` e `Dockerfile`**: Configurações para Docker e Docker Compose.

### Tecnologias

- **Tailwind CSS**: Utilizado para estilização rápida e eficiente, proporcionando uma abordagem utilitária para design.
- **Chakra UI**: Biblioteca de componentes UI para uma experiência de design acessível e moderna.

Esta arquitetura visa garantir uma separação clara de responsabilidades, facilitando a manutenção e a escalabilidade do projeto. Se você tiver dúvidas ou precisar de mais informações, consulte o arquivo `README.md` ou entre em contato.
