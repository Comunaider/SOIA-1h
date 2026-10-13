---
name: audit
description: Use quando alguém pede uma auditoria do AIOS, pede pontuação da configuração contra os Quatro Cs ou diz "meu AIOS está funcionando" / "audite minha configuração" / "encontre lacunas no meu AIOS". Produz um placar dos Quatro Cs com as 3 principais correções ranqueadas por alavancagem.
---

## O que esta habilidade faz

Roda a **Auditoria dos Quatro Cs** no projeto atual. Funciona em qualquer agente de IA que leia esta habilidade (Claude Code, Codex, OpenCode, Gemini CLI etc.). Lê (nunca escreve) o manual operacional do projeto, memória, habilidades, agentes, MCPs, decisões e referências. Dá nota de 0 a 25 para cada um dos Quatro Cs. Mostra pontos fortes e as 3 principais lacunas ponderadas por alavancagem, com comandos concretos de próximo passo.

**O escopo é estrutural - "o AIOS foi construído corretamente?"** Não é planejador de capacidades. Lacunas de capacidade ("você poderia criar um resumo diário se conectasse o calendário") pertencem a `/level-up`. A auditoria responde: arquivos, pastas, registros e conexões estão em bom estado?

A primeira execução é a linha de base. Reexecute semanalmente para ver a pontuação subir. Esse é o gancho cumulativo.

## Contexto de hoje

- **Data:** !`date +%Y-%m-%d`
- **Raiz do projeto:** diretório de trabalho atual

## Os Quatro Cs (25 pontos cada = 100 total)

| Camada | Teste |
|---|---|
| **Contexto** | Conhece o negócio - identidade, equipe, voz, decisões, referências |
| **Conexões** | Acessa as coisas do usuário - MCPs, integrações, fontes de dados |
| **Capacidades** | Sabe fazer trabalho - habilidades + agentes |
| **Cadência** | Roda sem ser solicitado - agendas, hooks, rituais recorrentes |

## Execução

### Etapa 1: Descobrir a forma do projeto

A auditoria procura **padrões e intenção**, não caminhos exatos. Nomes de arquivo variam. Use Glob e Read para verificar:

**Manual operacional:** `AGENTS.md` (raiz, canônico), `CLAUDE.md` / `GEMINI.md` (espelhos que só importam), `CLAUDE.local.md` (gitignored).
**Memória:** `MEMORY.md` (raiz), `~/.claude/projects/<id>/memory/MEMORY.md` ou pasta `memory/`.
**Habilidades:** `.claude/skills/*/SKILL.md` - contagem + frontmatter. Atalhos em `.agents/skills/`, `.opencode/command/` e `.gemini/commands/` apontam para a mesma habilidade - não conte em dobro.
**Agentes:** `.claude/agents/*.md` - contagem + frontmatter.
**Mecanismos de conexão** (qualquer um destes = "acessível"):
- MCPs: `.mcp.json`, `.claude/settings.json` (chave mcpServers), `.claude/settings.local.json`, `.codex/config.toml`, `opencode.json`, `.gemini/settings.json`
- Scripts de API: `scripts/*.py|.js|.ts` documentados em CLAUDE.md
- Pipelines de exportação: `data/`, `imports/`, `exports/` com script de atualização + timestamp da última execução
- Chaves de API + guia de referência: entradas `.env` + `referencias/{ferramenta}-api.md` correspondente

**Registro de conexões:** `conexoes.md` (em qualquer lugar).
**Guias de referência:** `referencias/{ferramenta}-api.md`, `referencias/*-referencia.md` ou equivalente.
**Decisões:** `decisoes/registro.md`, `decisoes.md` ou qualquer arquivo de decisões somente de acréscimo.
**Referências / SOPs:** pastas `referencias/`, `docs/`, `sops/`.
**Templates:** `modelos/`, `.claude/templates/`.
**Rotinas agendadas:** rotinas do `/schedule` do Claude Code, tarefas do Agendador de Tarefas do Windows, `cron` ou `systemd` documentados no `AGENTS.md` ou em `conexoes.md`, `.github/workflows/*.yml` com `schedule:`, ou nomes de habilidades que combinem com `morning-*`, `weekly-*`, `daily-*`, `monthly-*`, `standup`. Hook de `.claude/settings.json` sozinho não é rotina: ele reage a um evento da sessão, não roda com o notebook fechado.

Não penalize nomes não canônicos se a intenção equivalente estiver capturada em outro lugar.

### Etapa 2: Pontuar cada C (25 pontos cada)

#### Contexto (25 pts)

| Critério | Pontos | Como detectar |
|---|---|---|
| Manual operacional existe e é substancial (>200 palavras) | 5 | Leia AGENTS.md (ou CLAUDE.md, se não houver AGENTS.md), conte palavras |
| Identidade / papel / voz capturados | 5 | AGENTS.md (ou CLAUDE.md) menciona quem é o usuário + papel/missão, OU `.claude/rules/*.md` existe |
| Memória persistente existe com várias entradas | 5 | MEMORY.md existe com >3 entradas, OU `memory/` tem >3 arquivos |
| Documentos de referência existem | 5 | `referencias/`, `docs/` ou `sops/` tem >=1 arquivo |
| Decisões capturadas | 5 | `decisoes/registro.md` ou equivalente tem >=1 entrada |

#### Conexões (25 pts) - ciente de domínio, agnóstico a mecanismo

Uma conexão "acessível" conta por QUALQUER mecanismo: MCP, script, pipeline de exportação ou chave `.env` + `referencias/{ferramenta}-api.md`. O kit é API-first; a auditoria não prefere MCPs.

**Os 7 Domínios Universais Tier-1 de Dados:**

| # | Domínio | Exemplos |
|---|---|---|
| 1 | Receita / Financeiro | Extrato/Pix do banco, Mercado Pago, Asaas, Hotmart, Kiwify, Stripe, Bling, Conta Azul, planilha de vendas |
| 2 | Interações com clientes | WhatsApp Business, Instagram Direct, Kommo, RD Station, HubSpot, planilha de clientes |
| 3 | Calendário | Google Agenda, Outlook, Calendly |
| 4 | Comunicação | WhatsApp, Gmail, Outlook, Slack, Teams |
| 5 | Gestão de projetos / tarefas | Trello, Notion, ClickUp, Asana, planilha de tarefas |
| 6 | Inteligência de reuniões | Google Meet (gravação/transcrição), tl;dv, Fireflies, Otter, Zoom |
| 7 | Conhecimento / arquivos | Google Drive, OneDrive, Notion, Dropbox, SharePoint |

**Tier-2 (bônus):** chaves de API de serviços de IA (OpenRouter, Anthropic, OpenAI), decisões/histórico, conteúdo/publicação.

| Critério | Pontos | Como detectar |
|---|---|---|
| Cobertura de domínios Tier-1 | 10 | 1,4 pt por domínio tier-1 acessível. Arredonde para o 0,5 mais próximo. Limite 10. |
| Presença de guia de referência | 5 | -1 por ferramenta conectada sem `referencias/{ferramenta}-api.md`. Piso 0. |
| Atualização de auth / pipeline | 5 | -1 por conexão em estado `needs-auth`/`expired`, ou script sem execução nos últimos 30 dias. Piso 0. |
| Documentação em `conexoes.md` | 3 | 0 se ausente; 1 esparsa; 2 maioria; 3 cobre todos os acessíveis. |
| Equilíbrio leitura-E-escrita | 2 | Pelo menos uma conexão pode ESCREVER (enviar e-mail, postar atualização etc.). 0 se tudo é somente leitura - o AIOS é visualizador, não OS. |

#### Capacidades (25 pts)

| Critério | Pontos | Como detectar |
|---|---|---|
| 3+ habilidades instaladas | 10 | Conte `.claude/skills/*/SKILL.md` |
| 1+ habilidade criada pelo usuário | 10 | Nomes de habilidades que não estejam em: `onboard`, `audit`, `level-up`, `skill-creator`, `skill-builder`, `decision`, `connect`, `connect-check`, `memory-prune`, `scaffold-skill`, `scaffold-agent`, `draft`, `standup` (kit canônico + habilidades enviadas pela Anthropic) |
| 1+ agente definido | 5 | Conte `.claude/agents/*.md` >= 1 |

#### Cadência (25 pts)

| Critério | Pontos | Como detectar |
|---|---|---|
| 1+ rotina agendada | 10 | Alguma rotina agendada da Etapa 1 documentada no projeto, OU nome de habilidade combina com `morning-*` / `daily-*` / `weekly-*` / `monthly-*` / `standup` |
| Atividade recente / sinal de uso | 10 | Arquivos em `.claude/skills/` modificados nos últimos 30 dias, OU `decisoes/registro.md` tem entrada nos últimos 30 dias |
| Pasta de templates populada | 5 | `modelos/` ou `.claude/templates/` tem >=1 arquivo |

### Etapa 3: Identificar as 3 principais lacunas por alavancagem

Para cada critério que perdeu pontos: alavancagem = (pontos perdidos) x (multiplicador de impacto).

**Multiplicadores de impacto:**
- 0 domínios tier-1 acessíveis: **4x** (AIOS está cego para o negócio)
- Manual operacional ausente ou raso: **3x** (fundação)
- <=2 domínios tier-1 acessíveis: **3x** (Conexões é a porta de entrada para dados ao vivo)
- 0 habilidades: **2x** (sem Capacidades = sem AIOS)
- Sem rotina agendada: **2x** (sem Cadência = sem autonomia)
- Todas as conexões somente leitura: **2x** (visualizador, não OS)
- 0 guias de referência para ferramentas conectadas: **1,5x** (toda habilidade futura pesquisa as mesmas APIs de novo)
- Sem log de decisões: **1,5x**
- Todos os demais: **1x**

Ordene lacunas por alavancagem decrescente. Pegue as 3 principais. Para cada uma, escreva um próximo passo concreto em uma linha:
- **Precisa de uma nova habilidade?** Recomende `skill-creator` (Anthropic) ou `skill-builder` (se local), ou "escreva SKILL.md em `.claude/skills/<name>/SKILL.md` com frontmatter YAML."
- **Precisa registrar uma decisão?** "Acrescente em `decisoes/registro.md`."
- **Precisa acessar um domínio tier-1?** Prefira API+script (escreva `scripts/{ferramenta}_api.py` + salve `referencias/{ferramenta}-api.md`). Recomende MCP (`claude mcp add`, `codex mcp add` ou o equivalente da sua ferramenta) somente se não houver caminho por API.
- **Ferramenta conectada sem guia de referência?** "Pesquise a API uma vez, salve endpoints + auth + consultas comuns em `referencias/{ferramenta}-api.md`."
- **Precisa de rotina agendada?** "Pegue a habilidade que já funciona na mão e agende: `/schedule` no Claude Code (roda na nuvem, notebook fechado), Agendador de Tarefas do Windows ou `cron`. Registre o agendamento em `conexoes.md`. Não agende o que ainda não roda bem manualmente."

### Etapa 4: Emitir o relatório

Imprima diretamente no chat (Markdown). Formato:

```
# Auditoria AIOS - {date}
**Pontuação: {total}/100** ({stage})

Limiares de estágio:
- 0-39 -> Estágio 0: Fundação
- 40-69 -> Estágio 1: Construído
- 70-89 -> Estágio 2: Cumulativo
- 90-100 -> Estágio 3: Autônomo

## Placar

Contexto       {bar}  {n}/25  {label}
Conexões       {bar}  {n}/25  {label}
Capacidades    {bar}  {n}/25  {label}
Cadência       {bar}  {n}/25  {label}

(barra = ## por 5pts; label = "Forte" >=20, "Sólido" 15-19, "Fino" 8-14, "Ausente" <8)

## Pontos Fortes
- {1-3 bullets curtos dos critérios de maior pontuação}

## Top 3 Lacunas (ranqueadas por alavancagem)
1. **{nome da lacuna}** (-{points} x {multiplier})
   -> {próximo passo concreto}
2. **{nome da lacuna}** (-{points} x {multiplier})
   -> {próximo passo concreto}
3. **{nome da lacuna}** (-{points} x {multiplier})
   -> {próximo passo concreto}

## Próximo sugerido: {ação única de maior alavancagem}

---
Somente lacunas estruturais. Para explorar lacunas de CAPACIDADE (o que seu AIOS poderia FAZER e ainda não faz), execute /level-up após esta auditoria.
```

### Etapa 5: Oferecer salvar o relatório

Depois de imprimir, pergunte: "Salvar esta auditoria em `auditorias/auditoria-{date}.md` para acompanhar a pontuação ao longo do tempo?" Se sim, escreva (criando a pasta `auditorias/` se necessário). Este é o único efeito colateral de escrita.

## Observações

- **Somente leitura por padrão.** Nunca modifique AGENTS.md/CLAUDE.md, memória, habilidades ou arquivos do projeto. A única escrita opcional é o relatório de auditoria.
- **Seja flexível com nomes de arquivo.** Não penalize nomes não canônicos se a intenção estiver capturada.
- **Seja honesto, não generoso.** 95/100 é um flex. A maioria das configurações cai entre 40-70.
- **Não sugira habilidades que não existem.** Aponte para o que está realmente disponível.
- **Velocidade importa.** Relatório em menos de 60 segundos de relógio. Leia arquivos direcionados, conte pastas de habilidades sem ler cada uma por inteiro (somente frontmatter).
- **Detecção de cadência é difusa.** Infira por nomes de habilidades se as rotinas agendadas não estiverem documentadas.
