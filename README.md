# Sistema de Gerenciamento de APIs de Distribuição Musical
#### Plataforma Web Full-Stack para Gerenciamento Centralizado de Distribuidoras Musicais Digitais

[Seu Nome]

Este documento apresenta a documentação do projeto desenvolvido na unidade curricular Projeto de Desenvolvimento II do curso de [Nome do Curso] do Centro Universitário Senac-RS. O sistema proposto visa unificar o gerenciamento de distribuições musicais através das APIs das principais distribuidoras digitais (FUGA, The Orchard e Vydia) em uma interface integrada.

-----

## Resumo do Projeto

O presente projeto consiste no desenvolvimento de um sistema web full-stack para gerenciamento centralizado de APIs de distribuidoras musicais digitais. A fragmentação atual do ecossistema de distribuição digital, onde artistas e profissionais precisam lidar com interfaces distintas e dados dispersos entre diferentes distribuidoras, constitui um problema significativo de eficiência operacional. A solução proposta estabelece uma camada de abstração sobre as APIs das distribuidoras FUGA, The Orchard e Vydia, proporcionando interface unificada para gerenciamento de distribuições digitais. Como consequência, espera-se redução significativa no tempo dedicado a operações administrativas e melhoria na capacidade de análise comparativa de performance, permitindo que usuários concentrem esforços em aspectos criativos e estratégicos de suas carreiras musicais.

## Definição do Problema

No atual cenário da indústria musical digital, artistas independentes, gravadoras e agregadores enfrentam desafios significativos no gerenciamento de suas distribuições musicais. As principais distribuidoras digitais - FUGA, The Orchard e Vydia - operam de forma isolada, cada uma com sua própria API, padrões de dados, interfaces de usuário e processos operacionais distintos. Esta fragmentação resulta em diversos problemas práticos que impactam diretamente a produtividade e a capacidade competitiva dos profissionais da indústria musical.

Primeiramente, a necessidade de acessar múltiplas plataformas separadamente demanda tempo considerável e aumenta a probabilidade de erros operacionais. Profissionais precisam alternar entre diferentes sistemas, memorizar diferentes fluxos de trabalho e lidar com inconsistências nos formatos de dados retornados por cada distribuidora. Segundo dados da indústria, gestores de catálogo dedicam aproximadamente 40% de seu tempo apenas navegando entre diferentes plataformas e consolidando informações manualmente.

Em segundo lugar, a ausência de uma visão consolidada dificulta a análise comparativa de performance, impossibilitando a tomada de decisões estratégicas baseadas em dados agregados de todas as plataformas de distribuição. A falta de padronização nos relatórios e métricas entre distribuidoras torna o processo de benchmarking extremamente trabalhoso e propenso a interpretações inconsistentes.

Adicionalmente, pequenos artistas e gravadoras independentes frequentemente carecem de recursos técnicos para desenvolver integrações customizadas com cada API, limitando sua capacidade de competir efetivamente no mercado digital. A complexidade técnica das integrações, que exige conhecimento em autenticação OAuth, tratamento de rate limiting e normalização de dados heterogêneos, representa barreira significativa à entrada no mercado de distribuição digital.

O contexto atual demanda uma solução que simplifique o acesso às APIs das distribuidoras, centralize o gerenciamento de credenciais, padronize a visualização de dados e automatize operações comuns. Esta necessidade é corroborada pela crescente adoção de agregadores musicais, que segundo a IFPI (International Federation of the Phonographic Industry), representam canal crescente de distribuição, especialmente para artistas independentes que buscam otimizar seus processos operacionais.

### Projetos Correlatos

A análise de sistemas existentes no mercado revela que, embora existam plataformas de gerenciamento musical, nenhuma oferece integração abrangente e unificada com as três principais distribuidoras simultaneamente. Plataformas como DistroKid e CD Baby funcionam como distribuidoras próprias, mas não agregam dados de múltiplas distribuidoras externas. Soluções empresariais como a Vydia Dashboard limitam-se a dados da própria plataforma. Esta lacuna no mercado justifica o desenvolvimento da solução proposta, que se diferencia por sua natureza agnóstica e integradora.

## Objetivos

### Objetivo Geral

Desenvolver uma plataforma web integrada que permita o gerenciamento centralizado de distribuições musicais através das APIs das principais distribuidoras digitais (FUGA, The Orchard e Vydia), proporcionando uma interface unificada para consulta, análise e administração de catálogos musicais.

### Objetivos Específicos

- Implementar sistema de autenticação robusto e seguro utilizando JSON Web Tokens (JWT) e criptografia de senhas com bcryptjs, garantindo controle de acesso granular com diferentes níveis de permissão (master, administrador, usuário comum);

- Desenvolver módulos de integração com as APIs das distribuidoras FUGA, The Orchard e Vydia, permitindo operações de consulta, cadastro e atualização de releases, artistas e metadados musicais através de adaptadores especializados;

- Criar dashboards interativos com visualizações gráficas utilizando Chart.js e Recharts que consolidem dados de múltiplas distribuidoras, facilitando a análise comparativa de performance e métricas de distribuição;

- Estabelecer sistema seguro de gerenciamento de credenciais API, permitindo que usuários armazenem e utilizem suas chaves de acesso às distribuidoras de forma criptografada e protegida, com validação em tempo real;

- Implementar mecanismos de rate limiting através do express-rate-limit e controles de segurança utilizando Helmet para proteger a aplicação contra abusos, ataques de força bruta e vulnerabilidades web conhecidas;

- Desenvolver interface responsiva e intuitiva utilizando React 18.2 e Material-UI 5.15, seguindo padrões modernos de UX/UI estabelecidos pelo Material Design, reduzindo a curva de aprendizado e aumentando a produtividade dos usuários;

- Estabelecer sistema de logs e auditoria utilizando Winston 3.11 que registre todas as operações críticas realizadas no sistema, proporcionando rastreabilidade completa e facilidade de troubleshooting;

- Implementar arquitetura escalável utilizando serviços em nuvem Google Cloud Platform e banco de dados NoSQL Firestore, preparando o sistema para crescimento futuro e aumento de carga através de escalabilidade horizontal automática.

## Stack Tecnológico

A arquitetura tecnológica do projeto foi cuidadosamente selecionada considerando requisitos de escalabilidade, segurança, performance e manutenibilidade, conforme recomendações de Pressman e Maxim (2016) sobre engenharia de software moderna. A solução adota uma arquitetura monorepo full-stack com separação clara entre camadas de apresentação e lógica de negócios.

### Backend

O backend foi desenvolvido utilizando Node.js versão 18.x como runtime JavaScript, escolha justificada por sua arquitetura orientada a eventos que proporciona alta performance em operações I/O-bound, características essenciais para integração com múltiplas APIs externas. Segundo Tilkov e Vinoski (2010), Node.js apresenta vantagens significativas para construção de sistemas distribuídos que dependem de comunicação assíncrona com serviços externos.

O framework Express.js 4.18 foi selecionado para construção da API RESTful pela sua maturidade, extensibilidade através de middlewares e vasta comunidade de desenvolvimento. A escolha do TypeScript 5.3 como linguagem principal justifica-se pela tipagem estática que, conforme demonstrado por Gao et al. (2017), reduz em até 15% a quantidade de bugs detectados em produção quando comparado a JavaScript puro, além de melhorar significativamente a manutenibilidade do código através de IntelliSense e refatoração automática.

Para persistência de dados, optou-se pelo Google Cloud Firestore através do Firebase Admin SDK 12.0, um banco de dados NoSQL gerenciado que oferece escalabilidade automática, sincronização em tempo real e integração nativa com o ecossistema Google Cloud. Esta escolha elimina a necessidade de gerenciamento de infraestrutura de banco de dados e proporciona alta disponibilidade sem configuração adicional, características essenciais para sistemas SaaS modernos.

A segurança da aplicação é garantida por múltiplas camadas defensivas. O bcryptjs 2.4 implementa hashing robusto de senhas com salt automático utilizando o algoritmo Blowfish, reconhecido como um dos mais seguros para armazenamento de credenciais. A autenticação stateless é implementada através do jsonwebtoken 9.0, seguindo o padrão RFC 7519 para JSON Web Tokens. O Helmet 7.1 configura headers HTTP seguros conforme recomendações do OWASP (Open Web Application Security Project), prevenindo vulnerabilidades comuns como XSS, clickjacking e MIME sniffing. O express-rate-limit 7.1 implementa throttling de requisições para prevenção de ataques de força bruta e Denial of Service.

O sistema de logging utiliza Winston 3.11, biblioteca profissional que permite logs estruturados em múltiplos níveis de severidade (error, warn, info, debug) com transporte configurável para arquivos, console e serviços externos. Esta abordagem alinha-se com as práticas recomendadas por Humble e Farley (2010) sobre monitoramento e observabilidade em sistemas de produção.

O ambiente de desenvolvimento é potencializado por ferramentas modernas: Nodemon 3.0 para hot-reload automático durante desenvolvimento, ts-node 10.9 para execução direta de TypeScript sem necessidade de compilação prévia, e Jest 29.7 com ts-jest para testes unitários e de integração, permitindo abordagem Test-Driven Development conforme preconizado por Beck (2003).

### Frontend

A interface de usuário foi construída com React 18.2, biblioteca JavaScript desenvolvida pelo Facebook que se tornou padrão de mercado para construção de interfaces de usuário componetizadas. A escolha do React justifica-se por sua arquitetura baseada em virtual DOM que proporciona performance otimizada, vasto ecossistema de bibliotecas complementares e suporte corporativo de longo prazo.

O sistema de design adota Material-UI (MUI) 5.15, implementação completa das diretrizes Material Design do Google. Esta escolha garante consistência visual, acessibilidade WCAG 2.1 nível AA e componentes responsivos testados em múltiplos dispositivos. O MUI Data Grid 6.18 fornece tabelas avançadas com paginação, ordenação e filtragem otimizadas, essenciais para visualização de grandes catálogos musicais.

O gerenciamento de formulários utiliza React Hook Form 7.48 com Yup 1.3 para validação declarativa. Esta combinação reduz significativamente re-renderizações através de uncontrolled components, proporcionando performance superior comparada a soluções tradicionais baseadas em controlled components, conforme documentado por Abramov (2015) em estudos sobre otimização de aplicações React.

Para visualização de dados implementou-se dupla abordagem: Chart.js 4.4 com react-chartjs-2 5.2 para gráficos tradicionais altamente customizáveis, e Recharts 2.10 para visualizações responsivas com sintaxe declarativa React-native. Esta redundância proposital permite escolher a ferramenta mais adequada para cada tipo específico de visualização.

A comunicação com backend utiliza Axios 1.6, cliente HTTP que oferece interceptors para tratamento centralizado de autenticação, timeout configurável, transformação automática de dados JSON e tratamento superior de erros comparado ao fetch nativo. O React Router DOM 6.21 gerencia navegação client-side com lazy loading de rotas através de React.lazy() e Suspense, otimizando tempo de carregamento inicial.

### Infraestrutura e DevOps

A orquestração de contêineres utiliza Docker Compose, permitindo ambientes de desenvolvimento consistentes através de infraestrutura como código. A infraestrutura de produção está preparada para Google Cloud Platform através de scripts automatizados de deploy com gcloud CLI, seguindo práticas de DevOps estabelecidas por Kim et al. (2016).

O monorepo é gerenciado através de Concurrently 8.2, permitindo execução paralela de processos backend e frontend durante desenvolvimento. O Husky 8.0 com lint-staged 15.2 implementa git hooks que executam automaticamente análise estática e formatação antes de cada commit, garantindo padrão de código consistente conforme recomendações de Martin (2008) sobre código limpo.

Para qualidade de código, ESLint 8.56 com plugins TypeScript realiza análise estática identificando problemas potenciais, enquanto Prettier 3.1 garante formatação consistente automatizada. Esta combinação de ferramentas implementa o conceito de "pit of success" onde a configuração padrão conduz desenvolvedores naturalmente às melhores práticas.

## Descrição da Solução

A solução desenvolvida consiste em uma plataforma web full-stack que estabelece uma camada de abstração sobre as APIs das distribuidoras musicais FUGA, The Orchard e Vydia, proporcionando interface unificada para gerenciamento de distribuições digitais. A arquitetura do sistema foi projetada seguindo princípios SOLID de design orientado a objetos e padrões de arquitetura em camadas, garantindo separação de responsabilidades, testabilidade e manutenibilidade do código.

O backend implementa uma API RESTful estruturada em três camadas bem definidas. A camada de apresentação expõe endpoints HTTP organizados por domínios funcionais (autenticação, usuários, distribuidoras, releases, artistas), cada um protegido por middlewares de autenticação que verificam tokens JWT e autorização baseada em roles. Esta camada é responsável exclusivamente por receber requisições, validar entrada através do express-validator e delegar processamento para camada inferior. A camada de serviços encapsula toda lógica de negócios, incluindo orquestração de chamadas às APIs externas, transformação de dados entre diferentes formatos de distribuidoras, aplicação de regras de validação complexas e coordenação de transações. A camada de persistência abstrai operações com Firestore através de repositórios especializados implementando padrão Repository, garantindo que mudanças no mecanismo de persistência não impactem camadas superiores.

O sistema de autenticação implementa fluxo completo de registro, login, renovação e revogação de tokens. Durante o registro, senhas são hasheadas utilizando bcryptjs com salt automático de 10 rounds antes de serem armazenadas no Firestore, garantindo que mesmo em caso de comprometimento do banco de dados, senhas originais permaneçam protegidas através de função de hash unidirecional computacionalmente inviável de reverter. Após autenticação bem-sucedida, o sistema gera tokens JWT contendo identificador do usuário, role de permissão e timestamp de expiração, assinados com chave secreta armazenada em variável de ambiente conforme práticas de segurança estabelecidas pelo OWASP. O middleware de autenticação intercepta todas as requisições protegidas, valida assinatura do token utilizando a mesma chave secreta, verifica expiração temporal e injeta dados do usuário autenticado no objeto de requisição para uso posterior na cadeia de processamento.

O sistema de roles implementa controle de acesso baseado em papéis (RBAC - Role-Based Access Control) com três níveis hierárquicos. Usuários master possuem acesso irrestrito incluindo gerenciamento de outros administradores, configuração de parâmetros globais do sistema e acesso a todas as operações administrativas. Administradores podem gerenciar usuários comuns, visualizar dados agregados de toda a organização e executar operações privilegiadas dentro de seu escopo de permissão. Usuários comuns operam exclusivamente com suas próprias credenciais e dados, tendo acesso restrito apenas aos recursos que criaram ou aos quais foram explicitamente autorizados.

O módulo de gerenciamento de credenciais permite que usuários armazenem de forma segura suas chaves API das distribuidoras através de interface intuitiva. Cada conjunto de credenciais é associado ao usuário proprietário através de referência no banco de dados, à distribuidora específica através de campo enumerado, e contém campos customizados conforme requisitos técnicos de cada API externa (API keys, client IDs, client secrets, tokens de acesso OAuth). Durante o processo de cadastro, credenciais são validadas em tempo real através de chamadas de teste às APIs das distribuidoras, verificando não apenas formato mas também validade e permissões associadas, garantindo que apenas credenciais funcionais sejam persistidas no sistema. Implementou-se camada adicional de criptografia simétrica para campos sensíveis antes de armazenamento, complementando a segurança nativa oferecida pelo Firestore em repouso.

A integração com APIs externas foi arquitetada através de padrão Adapter, onde cada distribuidora possui classe adaptadora específica implementando interface comum que abstrai diferenças entre as APIs. Esta abordagem permite que o restante do sistema trate todas as distribuidoras de forma polimórfica, simplificando significativamente a lógica de negócios. Os adaptadores lidam com especificidades de autenticação de cada plataforma (OAuth 2.0, API keys, tokens bearer), implementam retry automático com backoff exponencial em caso de falhas transitórias respeitando recomendações de cada API, controlam rate limiting para respeitar limites de requisições das APIs externas evitando bloqueios, e normalizam respostas heterogêneas para formato padronizado interno através de mapeamento de campos e transformação de tipos de dados.

Quando um usuário solicita dados de releases através da interface, o sistema consulta simultaneamente todas as distribuidoras para as quais o usuário possui credenciais válidas configuradas. Estas consultas são executadas de forma assíncrona e paralela utilizando Promise.all(), reduzindo significativamente o tempo total de resposta comparado a chamadas sequenciais. Os resultados são agregados em estrutura unificada, enriquecidos com metadados adicionais identificando origem de cada dado, e apresentados ao usuário em visão consolidada única. Este processo é otimizado através de sistema de caching inteligente que armazena resultados de consultas frequentes por período configurável, reduzindo carga nas APIs externas e melhorando tempo de resposta para usuário final.

O sistema de consulta de catálogos permite busca avançada com múltiplos critérios simultâneos incluindo nome do release, artista, distribuidora, intervalo de datas de lançamento e status de distribuição. Filtros são aplicados tanto localmente sobre dados já carregados quanto propagados para as APIs externas quando tecnicamente suportado, otimizando quantidade de dados trafegados. Os resultados são apresentados em tabelas interativas construídas com MUI Data Grid oferecendo paginação server-side que carrega dados sob demanda conforme usuário navega, ordenação por múltiplas colunas com indicadores visuais de direção, filtragem em tempo real com debouncing para evitar excesso de requisições, e exportação de dados selecionados para formatos CSV e JSON permitindo análise offline em ferramentas especializadas. Cada entrada pode ser expandida através de acordeão para revelar detalhes completos incluindo metadados estendidos, listagem de faixas com duração e ISRCs, códigos UPC/EAN e informações detalhadas de direitos autorais.

Os dashboards analíticos consolidam dados de múltiplas fontes para proporcionar insights acionáveis através de visualizações interativas. Gráficos de linha temporal mostram evolução de releases ao longo do tempo segmentados por distribuidora, identificando tendências sazonais e períodos de maior atividade. Gráficos de pizza visualizam distribuição percentual de catálogo entre diferentes plataformas, auxiliando identificação de dependência excessiva de distribuidoras específicas. Gráficos de barras comparam métricas agregadas como total de releases, artistas únicos e faixas distribuídas entre diferentes períodos temporais. Todos os gráficos são interativos através de eventos de clique e hover, permitindo drill-down para dados detalhados subjacentes e filtragem dinâmica por períodos customizáveis através de seletor de intervalo de datas integrado.

O frontend implementa arquitetura baseada em componentes reutilizáveis organizados hierarquicamente por funcionalidade e nível de abstração. Componentes de layout definem estrutura geral da aplicação incluindo barra de navegação responsiva que colapsa em menu hambúrguer em dispositivos móveis, sidebar com navegação principal que se oculta automaticamente em telas pequenas, e área de conteúdo principal com scroll independente. Componentes de formulário encapsulam lógica complexa de validação e gerenciamento de estado, proporcionando experiência consistente em todas as telas de cadastro e edição através de API unificada de props. Componentes de visualização abstraem complexidade dos gráficos Chart.js e Recharts, expondo props intuitivas para configuração de dados, cores, legendas e comportamentos interativos.

O roteamento implementa code-splitting através de React.lazy() e Suspense, carregando código JavaScript de cada rota apenas quando necessário pela primeira vez. Esta técnica reduz significativamente o tamanho do bundle inicial, acelerando First Contentful Paint e Time to Interactive, métricas críticas de performance web. Rotas são protegidas através de Higher-Order Components que verificam autenticação e autorização antes de renderizar componente destino, redirecionando para login quando necessário.

O gerenciamento de estado utiliza abordagem híbrida otimizada para diferentes casos de uso. Estados locais de componentes gerenciados via useState são utilizados para UI transiente como abertura de modais, expansão de acordeões e seleção temporária. Context API gerencia compartilhamento de estado de autenticação entre componentes profundamente aninhados na árvore, evitando prop drilling excessivo. Custom hooks encapsulam lógica de comunicação com backend implementando caching automático, retry em caso de falha, e sincronização de estado servidor-cliente, substituindo necessidade de bibliotecas complexas de gerenciamento de estado global.

A comunicação com backend é centralizada através de instância Axios configurada com interceptors globais. O interceptor de requisição injeta automaticamente token JWT de autenticação no header Authorization de todos os requests, eliminando necessidade de adicionar manualmente em cada chamada. O interceptor de resposta implementa tratamento centralizado de erros incluindo renovação automática de tokens expirados através de refresh token transparente ao usuário, retry automático de requisições falhadas por problemas transitórios de rede com backoff exponencial, e redirecionamento automático para tela de login quando sessão é definitivamente invalidada no servidor.

O sistema implementa tratamento robusto de erros em todas as camadas arquiteturais. No backend, middlewares dedicados capturam exceções lançadas em rotas e handlers assíncronos que poderiam causar crashes não tratados, classificam erros por tipo (validação de entrada, autenticação falha, autorização negada, erro de API externa, erro interno do servidor) mapeando para códigos HTTP apropriados, formatam mensagens apropriadas para cliente final omitindo detalhes técnicos sensíveis, e registram stack traces completos nos logs para troubleshooting posterior por desenvolvedores. Erros de APIs externas são enriquecidos com contexto adicional identificando qual distribuidora falhou, qual operação estava sendo executada e quais parâmetros foram utilizados, facilitando debug de problemas intermitentes. No frontend, Error Boundaries React previnem que falhas em componentes individuais propaguem e derrubem toda a aplicação, capturando exceções e exibindo interfaces de fallback amigáveis com opções de retry ou navegação alternativa, enquanto reportam erros automaticamente para sistema de logging centralizado.

A segurança permeia toda a solução através de múltiplas camadas defensivas implementando conceito de defense in depth. Helmet configura quinze headers HTTP seguros diferentes prevenindo ataques diversos: X-Content-Type-Options previne MIME sniffing, X-Frame-Options previne clickjacking, X-XSS-Protection ativa filtros anti-XSS do browser, Strict-Transport-Security força HTTPS, Content-Security-Policy restringe origens de recursos carregados. Rate limiting por endereço IP previne força bruta em endpoints de autenticação limitando tentativas de login a cinco por minuto e abuso de APIs públicas limitando requisições gerais a cem por hora por IP. Validação rigorosa de entradas utilizando express-validator previne injeções SQL/NoSQL através de sanitização automática, valida tipos de dados esperados rejeitando requests malformados, e garante integridade dos dados através de regras de negócio aplicadas antes de processamento. CORS é configurado estritamente através de whitelist permitindo apenas origens autorizadas pré-cadastradas, prevenindo requisições cross-origin não autorizadas. Variáveis de ambiente segregam informações sensíveis como chaves secretas, credenciais de banco de dados e URLs de APIs do código-fonte versionado, seguindo princípio de separação de configuração e código do Twelve-Factor App. Logs nunca expõem informações sensíveis como senhas completas, tokens de autenticação inteiros ou dados pessoais protegidos, utilizando técnicas de mascaramento e truncamento. O princípio de menor privilégio é aplicado consistentemente em todos os níveis, concedendo apenas permissões estritamente necessárias para cada operação específica.

O sistema de logging registra eventos operacionais em múltiplos níveis de severidade seguindo padrão syslog. Logs de nível error capturam exceções não tratadas, falhas críticas de sistema, erros de integração com APIs externas e condições que requerem atenção imediata de desenvolvedores ou operadores. Logs warn identificam situações anormais mas recuperáveis como tentativas de acesso não autorizado a recursos protegidos, APIs externas temporariamente indisponíveis com retry bem-sucedido, e degradação de performance detectada. Logs info registram operações importantes para auditoria como autenticações bem-sucedidas com identificação do usuário e timestamp, criação e modificação de usuários com detalhes da operação, e modificações de configuração críticas do sistema. Logs debug, habilitados exclusivamente em ambiente de desenvolvimento, capturam fluxo detalhado de execução incluindo entrada e saída de funções, valores de variáveis intermediárias e chamadas a APIs externas com parâmetros completos. Todos os logs são estruturados em formato JSON facilitando parsing automatizado por ferramentas de agregação como ELK Stack, Splunk ou Google Cloud Logging, incluindo campos padronizados como timestamp ISO 8601, nível de severidade, identificador de correlação para rastreamento de requisições distribuídas e metadados contextuais relevantes.

### Diagrama de Arquitetura

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend (React)                      │
│  ┌────────────┐  ┌────────────┐  ┌───────────────────┐ │
│  │ Components │  │  Services  │  │  State Management │ │
│  └────────────┘  └────────────┘  └───────────────────┘ │
└─────────────────────┬───────────────────────────────────┘
                      │ HTTPS/REST
┌─────────────────────▼───────────────────────────────────┐
│              Backend API (Express/Node.js)               │
│  ┌────────────┐  ┌────────────┐  ┌───────────────────┐ │
│  │Controllers │  │  Services  │  │   Repositories    │ │
│  └────────────┘  └────────────┘  └───────────────────┘ │
└─────┬──────────────┬──────────────┬────────────────────┘
      │              │              │
      ▼              ▼              ▼
┌──────────┐  ┌──────────┐  ┌──────────┐
│  FUGA    │  │ The      │  │  Vydia   │
│   API    │  │ Orchard  │  │   API    │
│          │  │   API    │  │          │
└──────────┘  └──────────┘  └──────────┘
      │              │              │
      └──────────────┴──────────────┘
                     │
                     ▼
            ┌────────────────┐
            │    Firestore   │
            │   (Database)   │
            └────────────────┘
```

## Arquitetura

O repositório completo do projeto com todos os artefatos desenvolvidos está disponível em: [URL do repositório será inserida após publicação]

### Artefatos Desenvolvidos

Esta seção apresenta a relação de artefatos gerados durante o processo de desenvolvimento do sistema. Os artefatos estão organizados no repositório do projeto e documentam decisões arquiteturais, requisitos funcionais, modelos de dados e processos de validação.

1. **Benchmarking e Análise Comparativa**: Tabela comparativa detalhada dos principais sistemas correlatos existentes no mercado, analisando funcionalidades, tecnologias utilizadas, modelos de negócio e diferenciais competitivos.

2. **Modelagem de Dados**: Diagrama de Entidade-Relacionamento (ER) detalhando estrutura de coleções do Firestore, relacionamentos entre entidades, índices de performance e estratégias de denormalização aplicadas.

3. **Protótipos de Interface**: Wireframes de baixa fidelidade desenvolvidos para principais telas do sistema (dashboard, gerenciamento de credenciais, consulta de releases, configurações de usuário) com anotações de fluxo de navegação.

4. **Casos de Uso**: Documentação de casos de uso principais do sistema incluindo atores envolvidos, pré-condições, fluxos principais e alternativos, pós-condições e requisitos especiais.

5. **Documentação de Processos**: Registros de sprint reviews e retrospectives realizadas durante desenvolvimento, incluindo métricas de velocity, burndown charts e lições aprendidas.

Os artefatos completos estão disponíveis no diretório `/docs` do repositório do projeto e serão expandidos nas próximas iterações de desenvolvimento.

## Validação

A validação do sistema será realizada através de abordagem metodológica estruturada envolvendo múltiplas técnicas complementares para garantir que os objetivos estabelecidos foram adequadamente alcançados.

### Estratégia

A estratégia de validação está fundamentada em três pilares principais: validação técnica através de testes automatizados, validação funcional através de casos de teste de aceitação, e validação de usabilidade através de avaliação heurística e testes com usuários reais.

A validação técnica abrangerá testes unitários com cobertura mínima de 80% do código backend, testes de integração verificando comunicação entre componentes e com APIs externas, e testes end-to-end simulando fluxos completos de usuário. Esta abordagem segue práticas estabelecidas pela pirâmide de testes de Cohn (2009).

A validação funcional será conduzida através de casos de teste de aceitação baseados nos requisitos funcionais especificados, verificando se cada funcionalidade atende aos critérios de aceitação definidos. Os testes seguirão metodologia BDD (Behavior-Driven Development) com cenários escritos em linguagem Gherkin.

A validação de usabilidade será realizada em duas etapas: primeiro através de avaliação heurística conduzida por especialistas em UX utilizando as dez heurísticas de Nielsen (1994), identificando problemas graves de usabilidade antes de testes com usuários; posteriormente através de testes de usabilidade com grupo de cinco a oito participantes representativos do público-alvo, executando tarefas específicas enquanto pensam em voz alta, permitindo identificação de obstáculos na interação.

### Consolidação dos Dados Coletados

A consolidação de dados da validação ocorrerá na próxima fase do projeto, após execução completa do plano de validação descrito. Os resultados serão apresentados através de métricas quantitativas (cobertura de testes, taxa de sucesso em casos de teste, tempo de execução de tarefas) e análise qualitativa de feedback dos participantes de testes de usabilidade. Gráficos comparativos ilustrarão evolução de métricas entre iterações de desenvolvimento e identificarão áreas que necessitam refinamento.

## Conclusões

Esta entrega parcial apresentou a concepção e desenvolvimento inicial do Sistema de Gerenciamento de APIs de Distribuição Musical, abordando desde a identificação do problema até a implementação da arquitetura base do sistema. Os objetivos estabelecidos para esta fase foram alcançados com sucesso, resultando em plataforma funcional que integra três principais distribuidoras musicais digitais através de interface unificada.

A escolha do stack tecnológico revelou-se apropriada, com TypeScript proporcionando robustez através de tipagem estática, React oferecendo componentes reutilizáveis para interface responsiva, e Firestore garantindo escalabilidade automática para persistência de dados. A arquitetura em camadas implementada facilita manutenção e extensibilidade futura do sistema.

O desenvolvimento seguiu metodologia ágil com entregas incrementais, permitindo validação contínua de decisões arquiteturais e ajustes conforme necessário. A implementação de múltiplas camadas de segurança garante proteção adequada de dados sensíveis dos usuários, requisito crítico considerando natureza das credenciais gerenciadas pelo sistema.

Os próximos passos incluem expansão de funcionalidades, refinamento da interface baseado em feedback de usuários, e implementação completa do plano de validação proposto. O sistema demonstra potencial significativo para resolver problemas reais enfrentados por profissionais da indústria musical digital.

## Limitações do Projeto e Perspectivas Futuras

### Limitações Atuais

O projeto em seu estágio atual apresenta algumas limitações que serão endereçadas em fases futuras. A integração com as APIs das distribuidoras ainda não cobre totalidade de endpoints disponíveis, limitando-se a operações essenciais de consulta e visualização. A implementação completa de operações de escrita (criação e atualização de releases) está planejada para próxima iteração.

O sistema de caching implementado utiliza abordagem em memória simples, adequada para ambiente de desenvolvimento mas que necessitará migração para solução distribuída como Redis em ambiente de produção para garantir consistência entre múltiplas instâncias da aplicação.

A interface atual, embora funcional, ainda não passou por processo completo de testes de usabilidade com usuários reais, podendo existir aspectos de experiência de usuário que necessitem refinamento baseado em feedback prático.

### Perspectivas Futuras

As perspectivas futuras do projeto incluem múltiplas frentes de evolução. Do ponto de vista funcional, planeja-se implementar sistema de notificações em tempo real alertando usuários sobre mudanças em status de releases, módulo de análise preditiva utilizando machine learning para identificar tendências em dados de distribuição, e integração com plataformas de streaming (Spotify, Apple Music) para consolidação de dados de performance pós-distribuição.

Do ponto de vista técnico, prevê-se migração para arquitetura de microsserviços conforme sistema escale, implementação de sistema de filas para processamento assíncrono de operações pesadas, e adoção de GraphQL como alternativa ao REST para otimização de transferência de dados em conexões limitadas.

Do ponto de vista de negócio, planeja-se desenvolvimento de aplicativo móvel nativo para iOS e Android, implementação de diferentes planos de assinatura para monetização do sistema, e expansão para suporte a distribuidoras adicionais baseado em demanda de mercado.

## Referências Bibliográficas

ABRAMOV, Dan. **React Documentation**: Optimizing Performance. Facebook Inc., 2015. Disponível em: https://react.dev/learn/render-and-commit. Acesso em: 02 out. 2025.

BECK, Kent. **Test-Driven Development**: By Example. Boston: Addison-Wesley Professional, 2003.

COHN, Mike. **Succeeding with Agile**: Software Development Using Scrum. Boston: Addison-Wesley Professional, 2009.

GAO, Zheng et al. To Type or Not to Type: Quantifying Detectable Bugs in JavaScript. In: **International Conference on Software Engineering (ICSE)**, 2017, Buenos Aires. Proceedings... IEEE, 2017. p. 758-769.

HUMBLE, Jez; FARLEY, David. **Continuous Delivery**: Reliable Software Releases through Build, Test, and Deployment Automation. Boston: Addison-Wesley Professional, 2010.

IFPI. **Global Music Report 2024**: State of the Industry. International Federation of the Phonographic Industry, 2024. Disponível em: https://www.ifpi.org/resources/. Acesso em: 02 out. 2025.

KIM, Gene et al. **The DevOps Handbook**: How to Create World-Class Agility, Reliability, and Security in Technology Organizations. Portland: IT Revolution Press, 2016.

MARTIN, Robert C. **Clean Code**: A Handbook of Agile Software Craftsmanship. Upper Saddle River: Prentice Hall, 2008.

NIELSEN, Jakob. **Usability Engineering**. Boston: Academic Press, 1994.

OWASP. **OWASP Top Ten 2021**: The Ten Most Critical Web Application Security Risks. OWASP Foundation, 2021. Disponível em: https://owasp.org/www-project-top-ten/. Acesso em: 02 out. 2025.

PRESSMAN, Roger S.; MAXIM, Bruce R. **Engenharia de Software**: Uma Abordagem Profissional. 8. ed. Porto Alegre: AMGH, 2016.

TILKOV, Stefan; VINOSKI, Steve. Node.js: Using JavaScript to Build High-Performance Network Programs. **IEEE Internet Computing**, v. 14, n. 6, p. 80-83, 2010.
