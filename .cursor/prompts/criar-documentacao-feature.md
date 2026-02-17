# Prompt: Criar Documentação Completa de Feature

## Contexto

Use este prompt para documentar qualquer feature nova seguindo a metodologia estruturada utilizada na documentação de **Pulsos**. Esta abordagem cobre API Reference, Guias de Usuário e Documentação Técnica.

## Prompt Principal

```
Preciso criar documentação completa para a feature [NOME_DA_FEATURE]. 

**Sobre a feature:**
[Descrever resumidamente o que a feature faz, quem usa, e onde está implementada]

**Repositórios/Locais:**
- Endpoints: [repo ou local]
- Frontend: [repo ou local]
- Jobs/Automações: [repo ou local]
- Database: [sistema, tabelas relevantes]

**Estrutura desejada:**

1. **API Reference** (em `api-reference/[modulo]/`):
   - index.mdx atualizado com seção sobre a feature
   - Arquivos separados para cada entidade/endpoint principal
   - Arquivo de webhooks/eventos (se aplicável)
   - Arquivo de exemplos práticos

2. **Guias de Usuário** (em `guides/`):
   - Para usuários finais (app-rh, app-talent, etc)
   - Para usuários internos (backoffice, operações, CS)
   - Incluir: quickstart, FAQs, troubleshooting

3. **Documentação Técnica** (em `documentation/domains/[dominio]/`):
   - index.mdx (visão geral com diagrama de arquitetura)
   - data-model.mdx (com diagramas ER)
   - jobs-[sistema].mdx (se houver jobs/automações)
   - integrations.mdx (serviços externos)
   - metrics.mdx (métricas e KPIs)
   - journeys.mdx (fluxos de usuário)
   - business-rules.mdx (regras de negócio)

4. **Navegação** (atualizar `docs.json`):
   - Adicionar novos arquivos nas seções apropriadas
   - Organizar em sub-grupos quando necessário

**Instruções:**

1. Explore os repositórios usando Glob, Grep e SemanticSearch para coletar informações
2. Use Task (explore subagent) para explorar múltiplos repos em paralelo
3. Se necessário, use MCP tools (GitHub, Supabase) para acessar schemas e códigos
4. Para cada arquivo criado:
   - Use exemplos reais do código (com CodeGroup para múltiplas linguagens)
   - Inclua diagramas Mermaid quando apropriado (arquitetura, fluxos, ER)
   - Adicione Warnings, Tips e Notes para destacar informações importantes
   - Use CardGroups para organizar links relacionados
5. Priorize API Reference e Guias sobre documentação técnica detalhada se o tempo for limitado
6. SEMPRE atualize docs.json para que a nova documentação apareça na navegação

**Output esperado:**

Mínimo de 20 arquivos (pode chegar a 30+):
- ~5-7 arquivos de API Reference
- ~8-12 arquivos de Guias (divididos entre usuários finais e internos)
- ~5-8 arquivos de Documentação Técnica
- 1 atualização do docs.json

Siga a estrutura usada na documentação de Pulsos como referência de qualidade e organização.
```

## Variações do Prompt

### Para Feature Simples (apenas API)

```
Preciso documentar apenas a API da feature [NOME_DA_FEATURE].

**Endpoints:**
- [Lista de endpoints]

**Estrutura desejada:**
- api-reference/[modulo]/[feature].mdx com todos os endpoints
- Atualizar api-reference/[modulo]/index.mdx
- Exemplos em múltiplas linguagens (cURL, TypeScript, Python)
- Atualizar docs.json

Total esperado: 2 arquivos + docs.json
```

### Para Feature com Jobs/Automações

```
Preciso documentar a feature [NOME_DA_FEATURE] que possui jobs automáticos.

**Jobs/Automações:**
[Sistema usado: Inngest, Make, Cron, etc]
[Lista de jobs e seus propósitos]

**Foco em:**
- documentation/domains/[dominio]/jobs-[sistema].mdx (detalhes técnicos de cada job)
- guides/backoffice/[feature]-operacoes.mdx (como operar/monitorar)
- guides/backoffice/[feature]-troubleshooting.mdx (resolver problemas)

Incluir diagramas de sequência (Mermaid) mostrando fluxos entre jobs.
```

### Para Feature com UI Complexa

```
Preciso documentar a feature [NOME_DA_FEATURE] que tem interface de usuário complexa.

**Usuários:**
- [Tipo de usuário 1]: [O que fazem]
- [Tipo de usuário 2]: [O que fazem]

**Foco em:**
- guides/app-[tipo]/[feature]-introducao.mdx (o que é, para quê serve)
- guides/app-[tipo]/[feature]-quickstart.mdx (tutorial de 5min)
- guides/app-[tipo]/[feature]-[acao-principal].mdx (para cada ação chave)
- guides/app-[tipo]/[feature]-faq.mdx (perguntas frequentes)

Incluir screenshots ou descrições detalhadas das telas.
```

## Checklist Pós-Criação

Após criar a documentação, valide:

- [ ] Todos os arquivos `.mdx` têm frontmatter completo (title, description)
- [ ] Diagramas Mermaid renderizam corretamente (sem erros de sintaxe)
- [ ] Code blocks usam syntax highlighting apropriado
- [ ] Links internos funcionam (caminhos corretos)
- [ ] `docs.json` foi atualizado e JSON é válido
- [ ] Navegação faz sentido (ordem lógica, agrupamentos corretos)
- [ ] Exemplos de código são completos e executáveis
- [ ] Não há informações sensíveis (tokens, senhas, IPs internos)

## Estrutura de Pastas Padrão

```
.
├── api-reference/
│   ├── backoffice/
│   │   ├── index.mdx
│   │   └── [feature]/
│   │       ├── [entidade-1].mdx
│   │       ├── [entidade-2].mdx
│   │       ├── webhooks.mdx
│   │       └── examples.mdx
│   └── [outro-modulo]/
│
├── guides/
│   ├── app-rh/
│   │   └── [feature]/
│   │       ├── introducao.mdx
│   │       ├── quickstart.mdx
│   │       ├── [acao-1].mdx
│   │       └── faq.mdx
│   └── backoffice/
│       └── [feature]/
│           ├── operacoes.mdx
│           ├── troubleshooting.mdx
│           ├── manual-tecnico.mdx
│           └── acessar-via-api.mdx
│
├── documentation/
│   └── domains/
│       └── [dominio]/
│           ├── index.mdx
│           ├── data-model.mdx
│           ├── jobs-[sistema].mdx
│           ├── integrations.mdx
│           ├── metrics.mdx
│           ├── journeys.mdx
│           ├── business-rules.mdx
│           └── operations.mdx
│
└── docs.json
```

## Exemplos de Bons Diagramas

### Arquitetura

```mermaid
flowchart TB
    subgraph Frontend
        App[App Next.js]
    end
    
    subgraph Backend
        API[Directus API]
        Jobs[Inngest Jobs]
    end
    
    subgraph Storage
        DB[(PostgreSQL)]
    end
    
    subgraph External
        Service[External Service]
    end
    
    App -->|REST| API
    API -->|Read/Write| DB
    API -->|Trigger| Jobs
    Jobs -->|Call| Service
```

### Fluxo de Processo

```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant API
    participant Job
    participant Email
    
    User->>Frontend: Ação
    Frontend->>API: POST /endpoint
    API->>Job: Trigger evento
    Job->>Email: Enviar notificação
    Email-->>User: Email recebido
```

### Modelo de Dados

```mermaid
erDiagram
    ENTIDADE_A ||--o{ ENTIDADE_B : "tem"
    ENTIDADE_B }|--|| ENTIDADE_C : "pertence a"
    
    ENTIDADE_A {
        int id PK
        string nome
    }
    
    ENTIDADE_B {
        int id PK
        int entidade_a_id FK
        int entidade_c_id FK
    }
```

## Dicas Finais

1. **Priorize usuários finais**: Guias de usuário são mais valiosos que documentação técnica profunda
2. **Use linguagem clara**: Evite jargões técnicos em guias de usuário
3. **Exemplos reais**: Sempre use exemplos baseados no código real, não inventados
4. **Mantenha consistência**: Use a mesma estrutura para features similares
5. **Atualize incrementalmente**: É melhor documentar bem uma parte do que superficialmente tudo
6. **Teste a navegação**: Após atualizar docs.json, verifique que os links funcionam

## Referência

A documentação de **Pulsos** serve como exemplo completo desta metodologia:
- API Reference: 7 arquivos
- Guias: 12 arquivos (8 app-rh + 4 backoffice)
- Docs Técnicas: 8 arquivos (com diagramas Mermaid)
- Total: ~27 arquivos

Consulte esses arquivos como referência de qualidade e estrutura.
