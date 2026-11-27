# nassauTickets

Sistema de Controle de Atendimento para um **Laboratório de Análises Clínicas**, desenvolvido para gerenciar a emissão de senhas, organização da fila por prioridade, chamadas sonoras, atendimento por guichês e acompanhamento do fluxo de atendimento.

## 1. Objetivo

O projeto tem como objetivo desenvolver uma aplicação web para organizar o atendimento de um laboratório de análises clínicas, aplicando conceitos de desenvolvimento web, arquitetura cliente-servidor, gerenciamento de filas, versionamento com Git/GitHub e documentação técnica.

## 2. Funcionalidades

- **Totem de Autoatendimento:** emissão de senhas prioritárias, para exames e gerais.
- **Painel de Chamadas:** exibição das senhas chamadas e reprodução de chamadas por síntese de voz.
- **Terminal do Atendente:** identificação do operador, seleção de guichê, chamada de senhas, rechamada, início e encerramento de atendimentos.
- **Gestão da Fila:** acompanhamento das senhas aguardando, chamadas e atendidas.
- **Encerramento do Expediente:** possibilidade de encerrar o expediente e finalizar as senhas ainda aguardando.

## 3. Tipos de Senha e Regras de Prioridade

O sistema trabalha com três categorias:

| Sigla | Tipo | Descrição |
|---|---|---|
| SP | Serviço Prioritário | Atendimento prioritário |
| SE | Serviço de Exames | Coleta e retirada de exames |
| SG | Serviço Geral | Informações e serviços gerais |

A regra de chamada alterna entre a categoria prioritária (SP) e as categorias operacionais (SE e SG), respeitando a ordem de chegada dentro das categorias e considerando a disponibilidade de senhas.

## 4. Máquina de Estados

O fluxo de atendimento utiliza os seguintes estados:

`AGUARDANDO` → `CHAMADA` → `CHAMADA_NOVAMENTE` → `EM_ATENDIMENTO` → `ATENDIDA`

Também existe o estado `NAO_COMPARECEU`, utilizado quando o cliente não comparece ao atendimento.

As operações são realizadas por meio de rotas específicas da API, que validam os estados permitidos para cada ação.

## 5. Arquitetura

O projeto utiliza arquitetura cliente-servidor, dividida em duas aplicações:

- **Frontend:** interface web responsável pela interação com clientes, atendentes e painel.
- **Backend:** API responsável pelo gerenciamento das senhas, aplicação das regras de prioridade e atualização do estado da fila.

O frontend realiza requisições HTTP ao backend para consultar e modificar os dados do atendimento.

## 6. Tecnologias Utilizadas

### Frontend
- React
- Vite
- JavaScript
- React Router DOM
- Tailwind CSS
- Lucide React

### Backend
- Node.js
- Express
- JavaScript
- CORS

### Ferramentas
- Visual Studio Code
- Git e GitHub
- GitHub Desktop

## 7. Estrutura do Repositório

```text
nassauTickets/
├── backend/
│   ├── node_modules/
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
├── docs/
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── pages/
│   │   └── services/
│   ├── package.json
│   └── vite.config.js
├── .gitignore
├── LICENSE
└── README.md
```

## 8. Pré-requisitos

Antes de executar o projeto, é necessário ter instalado:

- Node.js
- npm
- Git (opcional, para clonar o repositório)

## 9. Instalação e Execução

### 9.1. Clonar o repositório

```bash
git clone https://github.com/gabriellaguedesaa-source/nassauTickets.git
cd nassauTickets
```

### 9.2. Iniciar o Backend

Abra um terminal na pasta do projeto:

```bash
cd backend
npm install
npm run dev
```

O servidor será iniciado em:

`http://localhost:3000`

### 9.3. Iniciar o Frontend

Abra outro terminal na pasta principal do projeto:

```bash
cd frontend
npm install
npm run dev
```

O Vite disponibilizará a aplicação em:

`http://localhost:5173`

### 9.4. Acessar as funcionalidades

| Rota | Funcionalidade |
|---|---|
| `/` | Tela inicial |
| `/totem` | Emissão de senhas |
| `/painel` | Painel público de chamadas |
| `/atendente` | Terminal do atendente |
| `/gestor` | Área de gestão |

## 10. API Backend

A API é disponibilizada em `http://localhost:3000/api`.

| Método | Endpoint | Descrição |
|---|---|---|
| GET | `/` | Verificação da API |
| POST | `/senhas` | Emissão de uma nova senha |
| GET | `/senhas` | Consulta das senhas |
| GET | `/senhas/:id` | Consulta de uma senha específica |
| GET | `/estado` | Consulta do estado geral da fila |
| POST | `/senhas/proxima` | Chamada da próxima senha |
| PATCH | `/senhas/:id/rechamar` | Rechamada de uma senha |
| PATCH | `/senhas/:id/iniciar` | Início do atendimento |
| PATCH | `/senhas/:id/concluir` | Conclusão do atendimento |
| PATCH | `/senhas/:id/nao-compareceu` | Registro de não comparecimento |
| PATCH | `/expediente/encerrar` | Encerramento do expediente |
| DELETE | `/senhas` | Limpeza das senhas |

## 11. Armazenamento e Limitações

Nesta versão, o backend utiliza armazenamento em memória para controlar as senhas e o estado da fila.

Consequentemente:
- Os dados são mantidos enquanto o servidor estiver em execução.
- Ao reiniciar o backend, os dados armazenados em memória são perdidos.
- Não há integração com banco de dados relacional nesta versão.
- A identificação do operador na interface não representa um sistema completo de autenticação e autorização no servidor.
- Recursos avançados de auditoria, persistência e controle de concorrência em múltiplos servidores não estão implementados integralmente.

Esses pontos representam possibilidades de evolução para versões futuras.

## 12. Acessibilidade e LGPD

O Totem permite a emissão de senhas sem solicitar dados pessoais do cliente. O Painel utiliza a Web Speech API do navegador para reproduzir chamadas sonoras, contribuindo para a acessibilidade do atendimento.

## 13. Branches e Versionamento

O projeto utiliza Git e GitHub para controle de versão e colaboração.

- `main`: branch principal do projeto.
- `dev`: branch destinada ao desenvolvimento e integração de funcionalidades.

O fluxo de trabalho prevê a validação das alterações em desenvolvimento antes da integração à versão principal.

## 14. Equipe

| Integrante | Matrícula | Responsabilidade |
|---|---|---|
| Gabriella Guedes | 01847354 | Scrum Master |
| Helena Nunes | 01792836 | Testadora |

---

**Projeto acadêmico — Sistema de Informação**

Sistema de Controle de Atendimento para Laboratório de Análises Clínicas.
