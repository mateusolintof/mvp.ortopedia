# Claude Code - MVP Agente Conversacional Flowise

## 📋 Contexto do Projeto

Você está desenvolvendo um **MVP de agente de agendamento conversacional** usando **Flowise** com embed em aplicação própria.

**Stack Principal:**
- Flowise (orchestrator de IA)
- Claude/GPT (LLM)
- Node.js + Express (backend)
- React/Vue (frontend com embed)
- PostgreSQL/MongoDB (banco de dados)

---

## 🚀 Quick Start

```bash
# 1. Instalar Flowise (se não tiver)
npm install -g flowise

# 2. Rodar Flowise
flowise
# Acesse: http://localhost:3000

# 3. Inicializar projeto
npm init -y
npm install express cors axios dotenv

# 4. Criar estrutura básica
mkdir -p src/{context,api,routes}
mkdir -p flowise-config/{agentes,templates}

# 5. Criar .env
echo "FLOWISE_URL=http://localhost:3000" > .env
echo "DATABASE_URL=postgresql://..." >> .env
```

---

## 📐 Estrutura do Projeto

```
seu-projeto/
├── src/
│   ├── server.js          # Express server
│   ├── context/
│   │   └── contextEngine.js
│   ├── api/
│   │   └── appointments.js
│   └── routes/
│       └── agendamentos.js
├── flowise-config/
│   └── agentes/
│       └── agendamento-mvp.json
├── .env
├── .mcp.json              # MCP Context7
└── package.json
```

---

## 🤖 Como Usar Context7 MCP

**Context7** fornece documentação atualizada do Flowise e outras libs.

### Quando você tiver dúvida, peça:

```
"Qual é a melhor forma de configurar Tool Calling no Flowise?"
"Como fazer embed do Flowise em React?"
"Qual é a sintaxe correta do node de Memory no Flowise?"
```

**Claude consultará a documentação mais recente automaticamente via Context7.**

---

## 🎯 Tarefas Principais (Ordem)

### Fase 1: Setup (2h)
- [ ] Flowise rodando localmente
- [ ] Backend Node.js criado
- [ ] DB conectado
- [ ] ENV configurado

### Fase 2: Flowise (3h)
- [ ] Criar chatflow básico
- [ ] Adicionar nodes: Chat Input → LLM → Tool Calling → Chat Output
- [ ] Configurar system prompt
- [ ] Testar manualmente

### Fase 3: Backend (4h)
- [ ] APIs criadas (`POST /appointments`, `GET /available-slots`)
- [ ] Context Engine implementado
- [ ] Integração com Flowise funcionando

### Fase 4: Embed (2h)
- [ ] Chatbot embarcado em React/Vue
- [ ] Testes funcionais
- [ ] Validações funcionando

### Fase 5: Deploy (1h)
- [ ] Flowise em produção
- [ ] Backend em produção
- [ ] SSL configurado

---

## 💡 Padrões de Prompts

### System Prompt Base (copie isto para seu LLM no Flowise)

```markdown
Você é um assistente de agendamento para [NEGÓCIO].

SERVIÇOS:
- Consulta Geral: 60min, R$ 250
- Retorno: 30min, R$ 150

REGRAS:
- Agendamento mínimo 24h antes
- Máximo 2 agendamentos por cliente
- Cancelamento até 24h antes

FLUXO:
1. Cumpriment + identifique necessidade
2. Ofereça 3 slots disponíveis
3. Colete dados (nome, telefone, email)
4. Confirme tudo antes de criar
5. Forneça número de confirmação

TONE: Profissional, empático, conciso
```

---

## 🔧 Comandos Úteis

```bash
# Claude Code
claude                          # Abrir prompt
claude "tarefa aqui"           # Rodar tarefa específica

# Flowise
flowise                        # Rodar localmente
npm install -g flowise         # Instalar/atualizar

# Node/NPM
npm install                    # Instalar dependências
npm run dev                    # Rodar com nodemon
npm test                       # Testes

# Git
git init
git add .
git commit -m "Initial commit"
```

---

## 🔌 APIs Que Você Vai Precisar

### GET /api/availability/slots
```javascript
// Retorna slots disponíveis para um serviço/data
{
  "service": "Consulta Geral",
  "date": "2025-11-20",
  "slots": [
    { "time": "09:00", "specialist": "Dr. João" },
    { "time": "14:00", "specialist": "Dra. Maria" }
  ]
}
```

### POST /api/appointments
```javascript
// Cria agendamento
{
  "client_name": "João Silva",
  "phone": "(11) 9876-5432",
  "service": "Consulta Geral",
  "date": "2025-11-20",
  "time": "14:00"
}

// Retorna
{
  "success": true,
  "confirmation_number": "AG-2025-11-20-001"
}
```

### GET /api/appointments/:clientId
```javascript
// Retorna agendamentos do cliente
{
  "appointments": [
    {
      "id": 1,
      "service": "Consulta",
      "date": "2025-11-20",
      "time": "14:00"
    }
  ]
}
```

---

## 🛠️ Ferramentas Úteis

| Ferramenta | Uso | Link |
|---|---|---|
| **Flowise** | Orchestrator IA | flowise.io |
| **Postman** | Testar APIs | postman.com |
| **pgAdmin** | Gerenciar DB | pgadmin.org |
| **Claude Code** | IDE com IA | anthropic.com |

---

## ⚠️ Erros Comuns

**Erro: "Tool não funciona"**
- Cheque URL da API
- Verifique headers (Content-Type, Authorization)
- Teste com Postman antes

**Erro: "Contexto perdido na conversa"**
- Verifique Memory node está conectado
- Limpe histórico antigo (>7 dias)

**Erro: "Agendamentos duplicados"**
- Adicione validação antes de criar
- Use transaction no DB

---

## 📞 Quando Pedir Ajuda ao Claude Code

```
✅ "Configure um Tool Calling node para chamar minha API de agendamentos"
✅ "Qual é a estrutura correta de um Context Engine?"
✅ "Como fazer embed do Flowise em React?"
✅ "Implemente validação de email/telefone em JavaScript"
✅ "Crie um sistema prompt para agente de agendamento médico"

❌ Não: "Faça o projeto inteiro"
✅ Sim: Tarefas específicas e bem definidas
```

---

## 🎯 Checklist MVP

- [ ] Flowise rodando
- [ ] Chatflow básico criado
- [ ] Backend com APIs funcionando
- [ ] Context Engine estruturado
- [ ] System prompt testado
- [ ] Embed em app React/Vue
- [ ] Validações implementadas
- [ ] Testes manuais ok
- [ ] Pronto para deploy

---

## 📚 Documentação Rápida

**Usar Context7 para:** Flowise, TypeScript, JavaScript, React, Node.js, PostgreSQL

```
Peça ao Claude Code:
"Use Context7 para verificar a sintaxe correta de [coisa que quer]"
```

---

## 🚀 Próximo Passo

Rode:
```bash
npm init -y
npm install express cors axios dotenv
npm install -D nodemon
mkdir -p src/{context,api,routes} flowise-config/agentes
```

Depois peça ao Claude Code:
```
"Crie um express server básico em src/server.js que vá servir 
como backend para meu agente Flowise de agendamento"
```

---

**Boa codificação! 🎯**