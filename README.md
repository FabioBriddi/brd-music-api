# Sistema de Gerenciamento de APIs de Distribuição Musical

> Plataforma web full-stack para gerenciamento centralizado de APIs de distribuidoras musicais digitais (FUGA, The Orchard, Vydia)

[![Node.js](https://img.shields.io/badge/Node.js-18.x-green.svg)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18.2-blue.svg)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.3-blue.svg)](https://www.typescriptlang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📋 Índice

- [Resumo do Projeto](#-resumo-do-projeto)
- [Definição do Problema](#-definição-do-problema)
- [Objetivos](#-objetivos)
- [Stack Tecnológico](#-stack-tecnológico)
- [Descrição da Solução](#-descrição-da-solução)
- [Instalação](#-instalação)
- [Uso](#-uso)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Contribuindo](#-contribuindo)
- [Licença](#-licença)

## 🎵 Resumo do Projeto

O presente projeto consiste no desenvolvimento de um sistema web full-stack para gerenciamento centralizado de APIs de distribuidoras musicais digitais. A plataforma foi concebida para atender à crescente demanda da indústria fonográfica por uma solução integrada que permita artistas, gravadoras e agregadores gerenciarem suas distribuições musicais através de múltiplas plataformas de streaming simultaneamente.

A escolha deste tema fundamenta-se na complexidade atual do ecossistema de distribuição digital de música, onde artistas e profissionais da indústria precisam lidar com interfaces distintas, processos fragmentados e dados dispersos entre diferentes distribuidoras como FUGA, The Orchard e Vydia. O sistema proposto visa unificar essas interações em uma única interface intuitiva, proporcionando maior eficiência operacional, melhor visualização de dados consolidados e automação de processos repetitivos, permitindo que os usuários concentrem seus esforços em aspectos criativos e estratégicos de suas carreiras musicais.

## 🎯 Definição do Problema

No atual cenário da indústria musical digital, artistas independentes, gravadoras e agregadores enfrentam desafios significativos no gerenciamento de suas distribuições musicais. As principais distribuidoras digitais - FUGA, The Orchard e Vydia - operam de forma isolada, cada uma com sua própria API, padrões de dados, interfaces de usuário e processos operacionais distintos. Esta fragmentação resulta em diversos problemas práticos:

**Principais desafios:**

- Necessidade de acessar múltiplas plataformas separadamente, consumindo tempo considerável
- Ausência de visão consolidada que dificulta análise comparativa de performance
- Falta de recursos técnicos em pequenas gravadoras para desenvolver integrações customizadas
- Complexidade no gerenciamento de credenciais de acesso para múltiplas plataformas
- Barreiras técnicas significativas à entrada no mercado de distribuição digital

O contexto atual demanda uma solução que simplifique o acesso às APIs das distribuidoras, centralize o gerenciamento de credenciais, padronize a visualização de dados e automatize operações comuns, permitindo que usuários de diferentes níveis técnicos possam gerenciar eficientemente suas distribuições musicais através de uma única interface unificada.

## 🎯 Objetivos

### Objetivo Geral

Desenvolver uma plataforma web integrada que permita o gerenciamento centralizado de distribuições musicais através das APIs das principais distribuidoras digitais (FUGA, The Orchard e Vydia), proporcionando uma interface unificada para consulta, análise e administração de catálogos musicais.

### Objetivos Específicos

- ✅ Implementar sistema de autenticação robusto com JWT e controle de acesso granular
- ✅ Desenvolver módulos de integração com APIs das distribuidoras FUGA, The Orchard e Vydia
- ✅ Criar dashboards interativos com visualizações de dados consolidados
- ✅ Estabelecer sistema seguro de gerenciamento de credenciais API criptografadas
- ✅ Implementar rate limiting e controles de segurança contra abusos
- ✅ Desenvolver interface responsiva seguindo padrões modernos de UX/UI
- ✅ Estabelecer sistema de logs e auditoria para rastreabilidade
- ✅ Implementar arquitetura escalável com GCP e Firestore

## 🛠️ Stack Tecnológico

### Backend

- **Runtime:** Node.js 18.x
- **Framework:** Express.js 4.18
- **Linguagem:** TypeScript 5.3
- **Banco de Dados:** Google Cloud Firestore
- **Autenticação:** JSON Web Tokens (JWT), bcryptjs
- **Segurança:** Helmet, express-rate-limit, express-validator
- **Logging:** Winston 3.11, Morgan 1.10
- **Testes:** Jest 29.7, Supertest

### Frontend

- **Framework:** React 18.2
- **Linguagem:** TypeScript 5.3
- **UI Library:** Material-UI (MUI) 5.15
- **Formulários:** React Hook Form 7.48, Yup 1.3
- **Gráficos:** Chart.js 4.4, Recharts 2.10
- **HTTP Client:** Axios 1.6
- **Roteamento:** React Router DOM 6.21

### DevOps & Infraestrutura

- **Containerização:** Docker, Docker Compose
- **Cloud:** Google Cloud Platform
- **CI/CD:** Husky, lint-staged
- **Code Quality:** ESLint, Prettier
- **Monorepo:** Concurrently

## 💡 Descrição da Solução

A solução desenvolvida consiste em uma plataforma web full-stack que estabelece uma camada de abstração sobre as APIs das distribuidoras musicais, proporcionando interface unificada para gerenciamento de distribuições digitais.

### Arquitetura

**Backend - API RESTful em Camadas:**
- **Camada de Apresentação:** Endpoints organizados por domínios (auth, users, distributors, releases)
- **Camada de Serviços:** Orquestração de APIs externas e lógica de negócios
- **Camada de Persistência:** Repositórios especializados para Firestore

**Principais Funcionalidades:**

1. **Sistema de Autenticação**
   - Registro e login com hash de senhas (bcryptjs)
   - Tokens JWT com expiração configurável
   - Sistema de roles (master, admin, user)

2. **Gerenciamento de Credenciais**
   - Armazenamento seguro de chaves API
   - Validação em tempo real com distribuidoras
   - Criptografia adicional para campos sensíveis

3. **Integração com Distribuidoras**
   - Adaptadores específicos para cada API
   - Retry automático e rate limiting
   - Normalização de respostas para formato padronizado

4. **Consulta de Catálogos**
   - Busca avançada com múltiplos filtros
   - Agregação de dados de múltiplas distribuidoras
   - Paginação server-side e exportação

5. **Dashboards Analíticos**
   - Gráficos de evolução temporal
   - Métricas agregadas consolidadas
   - Drill-down e filtragem dinâmica

6. **Segurança em Profundidade**
   - Headers HTTP seguros (Helmet)
   - Rate limiting por IP
   - Validação rigorosa de entradas
   - Princípio de menor privilégio

## 📦 Instalação

### Pré-requisitos

- Node.js >= 18.0.0
- npm >= 9.0.0
- Conta Google Cloud com Firestore habilitado
- Credenciais das distribuidoras (FUGA, The Orchard, Vydia)

### Passo a Passo

1. **Clone o repositório:**
```bash
git clone https://github.com/seu-usuario/music-distribution-api.git
cd music-distribution-api
```

2. **Instale as dependências:**
```bash
npm run install:all
```

3. **Configure o Backend:**
```bash
cd backend
cp .env.example .env
# Edite o arquivo .env com suas configurações
```

Variáveis necessárias no `.env`:
```env
PORT=3001
NODE_ENV=development
JWT_SECRET=sua_chave_secreta_super_segura
JWT_EXPIRES_IN=7d
GOOGLE_APPLICATION_CREDENTIALS=./path/to/serviceAccountKey.json
```

4. **Configure o Firebase:**
- Baixe as credenciais do Firebase Admin SDK
- Coloque o arquivo JSON em `backend/config/`
- Atualize a variável `GOOGLE_APPLICATION_CREDENTIALS`

5. **Configure o Frontend:**
```bash
cd ../frontend
cp .env.example .env
# Edite com a URL da API
```

6. **Crie o usuário master:**
```bash
cd ../backend
npm run create-master
```

## 🚀 Uso

### Desenvolvimento

Execute backend e frontend simultaneamente:
```bash
npm run dev
```

Ou execute separadamente:
```bash
# Backend (porta 3001)
npm run dev:backend

# Frontend (porta 3000)
npm run dev:frontend
```

### Produção

1. **Build:**
```bash
npm run build
```

2. **Start:**
```bash
npm run start
```

### Testes

```bash
# Todos os testes
npm test

# Com coverage
npm run test:coverage

# Backend apenas
npm run test:backend

# Frontend apenas
npm run test:frontend
```

### Linting e Formatação

```bash
# Lint
npm run lint

# Fix automático
npm run lint:fix

# Format
npm run format
```

## 📁 Estrutura do Projeto

```
music-distribution-api/
├── backend/
│   ├── src/
│   │   ├── config/          # Configurações (Firebase, etc)
│   │   ├── controllers/     # Controllers das rotas
│   │   ├── middlewares/     # Auth, validation, error handling
│   │   ├── models/          # Interfaces e tipos
│   │   ├── routes/          # Definição de rotas
│   │   ├── services/        # Lógica de negócios
│   │   ├── utils/           # Utilitários e helpers
│   │   └── app.ts           # Entry point
│   ├── tests/               # Testes
│   └── package.json
├── frontend/
│   ├── public/              # Assets estáticos
│   ├── src/
│   │   ├── components/      # Componentes React
│   │   ├── contexts/        # Context API
│   │   ├── hooks/           # Custom hooks
│   │   ├── pages/           # Páginas/rotas
│   │   ├── services/        # API clients
│   │   ├── types/           # TypeScript types
│   │   ├── utils/           # Utilitários
│   │   └── App.tsx          # Root component
│   └── package.json
├── docker-compose.yml       # Orquestração Docker
├── .gitignore
├── package.json             # Root package
└── README.md
```

## 🤝 Contribuindo

Contribuições são bem-vindas! Por favor:

1. Faça fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👥 Autores

- **Seu Nome** - *Desenvolvimento Full Stack* - [seu-usuario](https://github.com/seu-usuario)

## 🙏 Agradecimentos

- Anthropic's Claude para assistência no desenvolvimento
- Comunidade open-source pelas excelentes bibliotecas
- Distribuidoras musicais pela disponibilização de APIs

---

**Desenvolvido com ❤️ para a comunidade musical**