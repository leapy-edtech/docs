```
Preciso criar documentação completa para a feature [NOME_DA_FEATURE].

**Sobre a feature:**
O Matchmaker é uma feature chat-based onde o usuário pode conversar com a IA e passar uma url com a descrição da vaga ou então um texto dizendo que ele precisa de um talento com as skills A,B ,C e D. O sistema então faz todo um fluxo detalhado para entregar os talentos que tenham mais % de match com a vaga ou lista de skills.

**Repositórios/Locais:**
- Endpoints Agent-System (NEW): /Users/marlonwanderllich/code/leapy/agent-system
- Endpoints Backoffice (já existe na doc): /Users/marlonwanderllich/code/leapy/directus-backoffice-with-extensions
- Frontend: /Users/marlonwanderllich/code/leapy/leapy-rh
- Database: Buscar no projeto supabase dev-leapy-backoffice

**Estrutura desejada:**

1. **API Reference** (em `api-reference/[modulo]/`):
   - O matchmaker tem os endpoints que estão no agent-system e tb uma espécie de proxy que está no backoffice
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
4. **IMPORTANTE - Se o backend for Directus**: Explore extensions customizadas:
   - Verificar `extensions/hooks/src/` para hooks CRON e event listeners
   - Verificar `extensions/endpoints/src/` para endpoints customizados (além dos CRUD padrão)
   - Verificar `extensions/endpoints-workflows/src/` para workflows/operações especiais
   - Verificar `extensions/operations/src/` para operações customizadas
   - Verificar `extensions/shared/` para utilities compartilhadas

   Para cada extension encontrada:
   - Documentar rotas/endpoints customizados com método HTTP, parâmetros, validações e exemplos
   - Documentar hooks CRON com horários de execução, lógica e eventos disparados
   - Documentar eventos customizados que são enviados para Inngest ou outros sistemas
   - Incluir diagrama de fluxo mostrando: Hook CRON → Evento → Job Inngest
   - Adicionar seção "Extensions do Directus" em `integrations.mdx`
   - Adicionar seção "Hooks CRON" em `operations.mdx`
   - Criar arquivo separado para endpoints customizados: `api-reference/[modulo]/[feature]-endpoints-custom.mdx`
5. Para cada arquivo criado:
   - Use exemplos reais do código (com CodeGroup para múltiplas linguagens)
   - Inclua diagramas Mermaid quando apropriado (arquitetura, fluxos, ER)
   - Adicione Warnings, Tips e Notes para destacar informações importantes
   - Use CardGroups para organizar links relacionados
5. Priorize API Reference e Guias sobre documentação técnica detalhada se o tempo for limitado
6. SEMPRE atualize docs.json para que a nova documentação apareça na navegação

**Output esperado:**

Mínimo de 20 arquivos (pode chegar a 30+):
- ~5-7 arquivos de API Reference (incluindo endpoints customizados se houver)
- ~8-12 arquivos de Guias (divididos entre usuários finais e internos)
- ~5-8 arquivos de Documentação Técnica (incluindo seções sobre extensions)
- 1 atualização do docs.json

**Se o backend for Directus com extensions customizadas, adicione:**
- 1 arquivo `[feature]-endpoints-custom.mdx` em API Reference
- Seção "Hooks CRON" em `operations.mdx`
- Seção "Extensions do Directus" em `integrations.mdx`
- Diagrama de fluxo Hook → Evento → Job

Siga a estrutura usada na documentação de Pulsos como referência de qualidade e organização.
```
