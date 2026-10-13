# SOIA - kit inicial do seu Sistema Operacional de IA

Kit gratuito, licença MIT, que transforma o seu agente de IA de terminal (Claude Code, Codex, OpenCode, Gemini CLI, Cursor...) no seu **Sistema Operacional de IA (SOIA)** pessoal. Feito para donos de pequenos negócios, profissionais solo, gestores e criadores que querem usar IA no trabalho de verdade, não só no chat.

O kit se personaliza para você numa entrevista (`/onboard`) e depois entrega duas habilidades semanais (`/audit`, `/level-up`) para você continuar evoluindo o sistema.

Mantido por **Gustavo Schineider** e usado no curso e nas instalações 1:1. Baseado no **AIS-OS**, kit aberto de Nate Herk ([AI Automation Society](https://www.skool.com/ai-automation-society)), adaptado para português e para a realidade de negócio brasileira (WhatsApp, Pix, planilha).

---

## Antes de começar

Você precisa de três coisas instaladas:

1. **VS Code** - [code.visualstudio.com](https://code.visualstudio.com)
2. **Git** - [git-scm.com/downloads](https://git-scm.com/downloads)
3. **Um agente de terminal.** O caminho recomendado é o Claude Code (exige plano pago da Anthropic, Pro ou superior):
   - Windows (PowerShell): `irm https://claude.ai/install.ps1 | iex`
   - macOS / Linux: `curl -fsSL https://claude.ai/install.sh | bash`
   - Teste: abra um terminal novo, digite `claude` e faça uma pergunta qualquer.

Prefere outra IA? Veja a tabela abaixo. O kit funciona igual.

---

## Começo rápido

1. **Baixe o kit.** No terminal, dentro da pasta onde você guarda projetos:
   ```
   git clone https://github.com/Comunaider/SOIA-1h.git meu-soia
   ```
   Sem Git? Clique em **Code > Download ZIP** aqui no GitHub e descompacte.
2. **Abra a pasta `meu-soia` no VS Code** e abra o terminal dentro dela.
3. **Rode o agente** (`claude`, `codex`, `opencode`, `gemini`...) e digite `/onboard`, ou peça "faça meu onboarding". São 7 perguntas, cerca de 15 minutos. Amostras de voz devem ser **coladas** de algo que você já escreveu, não digitadas na hora.
4. **Use por uma semana.** Traga perguntas reais do seu trabalho. Quando decidir algo, peça "registra essa decisão" (vai para `decisoes/registro.md`).
5. **Dia 7:** rode `/audit`. Leia as 3 lacunas. Escolha uma para fechar.
6. **Dia 14:** rode `/level-up`. A entrevista revela uma automação que vale construir. Construa.
7. **Semana 3 em diante:** um `/level-up` por semana. Um artefato entregue por semana.

---

## Funciona com qualquer IA

O manual do sistema segue o padrão aberto **AGENTS.md** e as habilidades são markdown puro. O mesmo repositório roda em qualquer agente de terminal.

| Ferramenta | Manual que ela lê | Como chamar as habilidades |
|---|---|---|
| **Claude Code** | `CLAUDE.md` (importa `AGENTS.md`) | `/onboard`, `/audit`, `/level-up` via `.claude/skills/` |
| **OpenAI Codex** | `AGENTS.md` | Skills do projeto em `.agents/skills/`. Use `/skills` ou `$onboard`, ou peça em linguagem natural |
| **OpenCode** | `AGENTS.md` | `/onboard`, `/audit`, `/level-up` via `.opencode/command/` |
| **Gemini CLI** | `GEMINI.md` (importa `AGENTS.md`) | `/onboard`, `/audit`, `/level-up` via `.gemini/commands/` |
| **Cursor / Copilot / outros** | `AGENTS.md` | Peça em linguagem natural. O `AGENTS.md` aponta o arquivo certo |

Três regras mantêm isso funcionando:

1. **`AGENTS.md` é o manual canônico.** `CLAUDE.md` e `GEMINI.md` só importam. Edite sempre o `AGENTS.md`.
2. **`.claude/skills/*/SKILL.md` é a fonte única de cada habilidade.** Os arquivos em `.agents/`, `.opencode/` e `.gemini/` são atalhos que mandam ler o SKILL.md. Nunca duplique a lógica neles.
3. **Linguagem natural sempre funciona.** Dizer "audite meu sistema" dispara a habilidade em qualquer ferramenta.

---

## O teste decisivo

> **"Enquanto você não está na mesa, seu SOIA observa um evento real e produz uma entrega mais rápida e mais precisa do que você produziria sozinho."**

Toda decisão de design do kit converge para esse teste.

---

## Como saber que está funcionando

Três sinais que aparecem na sua semana. Não são métricas, são experiências.

**1. Você pergunta primeiro pro sistema.** Alguém te faz uma pergunta sobre o negócio e você percebe que o SOIA responde melhor e mais rápido, com a fonte. Você deixa de ser o gargalo do próprio conhecimento.

**2. Menos abas abertas.** Quando algo novo aparece, o primeiro movimento é perguntar ao SOIA, não abrir seis ferramentas.

**3. O conhecimento sai da sua cabeça.** Você para de tentar lembrar o que decidiu no mês passado ou o que o cliente disse na reunião. O sistema guarda a verdade. Você guarda as perguntas.

Quando isso acontece com uma pessoa, a mesma estrutura serve para o resto: painéis sobre os dados que você já coleta, automações em cima das conexões que você já fez, e um SOIA por pessoa da equipe.

---

## Dois frameworks

**Três Ms primeiro, Quatro Cs depois.** Sem mudar o jeito de pensar, a arquitetura é só uma estrutura de pastas.

### Os Três Ms - como você pensa

| M | Resumo |
|---|---|
| **Mindset** | Mudança de Padrão, Quebra por Função, Regra da Curiosidade. *Até que ponto a IA pode ser aproveitada aqui?* |
| **Método** | Encontrar Restrição -> EAD (Eliminar, Automatizar, Delegar) -> Mapear Processo -> Escolher Nível de Autonomia -> Ligar a KPI. |
| **Máquina** | Princípio Lego, Cadeia de Validação, Método da Bicicleta, Regra do Estagiário, Botão de Emergência. *Chato é bonito. Workflows vencem agentes.* |

Explicação completa em `referencias/framework-3ms.md`. O `/level-up` percorre os três toda semana.

> *The Three Ms of AI(TM) é uma marca registrada de Nate Herk. © 2026 Nate Herk.*

### Os Quatro Cs - o que você constrói

| # | Camada | Resumo | Teste de "está pronta" |
|---|---|---|---|
| 1 | **Contexto** | Conhece seu negócio | Uma sessão nova responde "o que este negócio faz e quem trabalha aqui?" sem você explicar |
| 2 | **Conexões** | Acessa suas coisas | "O que tenho na agenda amanhã e o que vence?" -> dado ao vivo, sem colar nada |
| 3 | **Capacidades** | Sabe fazer o trabalho | Uma frase curta dispara um fluxo de várias etapas que entrega um arquivo pronto |
| 4 | **Cadência** | Roda sem você pedir | Notebook fechado. Um resumo chega no seu WhatsApp ou e-mail |

> *The Four Cs of an AIOS(TM) é uma marca registrada de Nate Herk. © 2026 Nate Herk.*

Ordem: Contexto não pode ser pulado. Conexões e Capacidades podem andar juntas. Cadência vem por último: não automatize o que ainda não funciona na mão.

---

## As 3 habilidades do kit

O kit é enxuto de propósito. As habilidades são ferramentas de pensamento, não automações pesadas. Você constrói o resto em cima.

| Habilidade | Tipo | Quando rodar |
|---|---|---|
| `/onboard` | Configuração (uma vez) | Dia 1. Entrevista de 7 perguntas. Monta os arquivos de contexto e preenche o `AGENTS.md`. Pode rodar de novo quando quiser. |
| `/audit` | Semanal | Dia 7, depois toda semana. Nota de 0 a 100 nos Quatro Cs e as 3 lacunas que mais rendem. Só lê, não altera nada. |
| `/level-up` | Semanal | Dia 14, depois toda semana. Entrevista dos Três Ms. Uma execução = um artefato entregue. |

`/audit` pergunta *"o sistema foi montado direito?"*. `/level-up` pergunta *"que ganho estou deixando passar?"*. Corrija a estrutura primeiro, depois planeje capacidades.

---

## Estrutura do repositório

```
meu-soia/
├── README.md
├── LICENCA
├── AGENTS.md                        <- Manual canônico do sistema (preenchido pelo /onboard)
├── CLAUDE.md                        <- Espelho para Claude Code (importa AGENTS.md)
├── GEMINI.md                        <- Espelho para Gemini CLI (importa AGENTS.md)
├── EXPANSOES.md                     <- O que adicionar conforme você cresce
├── entrada-aios.md                  <- Respostas do /onboard. Edite e rode de novo quando quiser.
├── conexoes.md                      <- Mapa de todo sistema que o SOIA acessa
├── contexto/                        <- Sobre você e seu negócio (preenchido pelo /onboard)
├── referencias/
│   └── framework-3ms.md             <- Como pensar sobre trabalho com IA
├── decisoes/
│   └── registro.md                  <- O que foi decidido e por quê (só acrescenta)
├── arquivos/                        <- Coisas antigas. Não exclua, mova para cá.
├── .claude/skills/                  <- Fonte única das habilidades (markdown puro)
│   ├── onboard/SKILL.md
│   ├── audit/SKILL.md
│   └── level-up/SKILL.md
├── .agents/skills/                  <- Atalhos para Codex e outras IAs do padrão Agent Skills
├── .opencode/command/               <- Atalhos para OpenCode
└── .gemini/commands/                <- Atalhos para Gemini CLI
```

Veja `EXPANSOES.md` para saber o que adicionar conforme cresce (`projetos/`, `modelos/`, `scripts/`, `processos/`, `.claude/agents/` etc.).

---

## Licença e atribuição

Licença MIT, texto completo em `LICENCA`. Kit original © 2026 Nate Herk. Adaptação © 2026 Gustavo Schineider.

The Three Ms of AI(TM) e The Four Cs of an AIOS(TM) são marcas registradas de Nate Herk. Os dois frameworks acompanham este repositório com atribuição. Use livremente, mas não reempacote como se fossem seus.
