# AIS-OS - kit inicial de Sistema Operacional de IA para Claude Code

Um kit inicial gratuito, licenciado sob MIT, que transforma o Claude Code no seu **Sistema Operacional de IA (AIOS)** pessoal. Público: qualquer pessoa criando automações, incluindo empreendedores solo, operadores de pequenos negócios, gestores, criadores e consultores de IA. Acompanha uma masterclass em vídeo.

O kit se personaliza para você por meio de uma entrevista `/onboard` e depois entrega duas habilidades recorrentes de pensamento (`/audit`, `/level-up`) para continuar criando alavancagem semana após semana.

> **AIS-OS** significa **AI Automation Society OS** - a forma como Nate projetou este AIOS para ser configurado por membros da comunidade dele, [AI Automation Society](https://www.skool.com/ai-automation-society). O kit é universal, funciona para qualquer pessoa, mas a estrutura espelha como membros da AIS operam seus próprios negócios em cima dele.

---

## O teste decisivo

> **"Enquanto você não está na mesa, seu AIS-OS observa um evento real e produz uma entrega mais rápida e mais precisa do que você produziria sozinho."**

Toda decisão de design neste kit converge para esse teste. Se uma camada, habilidade ou modelo não contribui para isso, ela não entra.

---

## Como saber que está funcionando

Três **indicadores de sucesso sentidos na prática** mostram que o AIOS está realmente mudando como você trabalha. Não são KPIs, não há uma métrica objetiva. São experiências vividas que aparecem na sua semana.

**1. A equipe procura você:**

> *"Um colega manda uma mensagem com uma pergunta. Você percebe que seu AIOS responderia melhor, mais rápido e com fontes exatas, mesmo se você estivesse acordado e livre. Então você também pergunta ao AIOS. Esse é o momento em que você deixa de ser gargalo do próprio conhecimento."*

**2. Redução de troca de contexto:**

> *"Você para de abrir novas abas. Você para de iniciar o app desktop. Quando algo novo aparece, seu primeiro movimento é perguntar ao AIOS, não abrir seis coisas. A superfície padrão para trabalho intelectual muda. Silenciosa. Cumulativa."*

**3. O conhecimento sai da sua cabeça:**

> *"Você para de tentar lembrar fatos do negócio. Você não ensaia o que decidiu no trimestre passado nem o que o cliente disse naquela reunião. Você confia na recuperação. O AIOS guarda a verdade; você guarda as perguntas."*

**Base pessoal -> prontidão da empresa para IA.** Quando esses indicadores aparecem para uma pessoa, a mesma arquitetura de dados alimenta todo o resto. Dashboards personalizados sobre os dados que você já coleta. Automações em cima das conexões que você já configurou. Implantação para a equipe, onde cada pessoa tem o seu. *Uma empresa em que cada operador roda um AIOS pessoal é uma empresa realmente pronta para IA.*

O kit ensina AIOS pessoal primeiro. Todo o resto escala a partir daí.

---

## Dois frameworks

O kit ensina dois frameworks complementares. **Três Ms primeiro, Quatro Cs depois.** Sem a reprogramação do cérebro, a arquitetura é só uma estrutura de pastas.

### Os Três Ms - cérebro do operador (como você pensa)

| M | Resumo |
|---|---|
| **Mindset** | Mudança de Padrão, Quebra por Função, Regra da Curiosidade. *Até que ponto a IA pode ser aproveitada aqui?* |
| **Método** | Encontrar Restrição -> EAD (Eliminar, Automatizar, Delegar) -> Mapear Processo -> Escolher Nível de Autonomia -> Ligar a KPI. |
| **Máquina** | Princípio Lego, Cadeia de Validação, Método da Bicicleta, Regra do Estagiário, Botão de Emergência. *Chato é bonito. Workflows vencem agentes.* |

A explicação completa está em `referencias/framework-3ms.md`. A habilidade `/level-up` percorre os três semanalmente.

> *The Three Ms of AI(TM) é uma marca registrada de Nate Herk. © 2026 Nate Herk.*

### Os Quatro Cs - arquitetura (o que você constrói)

| # | Camada | Resumo | Teste de "esta camada está pronta" |
|---|---|---|---|
| 1 | **Contexto** | Conhece seu negócio | Uma sessão nova do Claude responde "o que este negócio faz e quem trabalha aqui?" sem navegar |
| 2 | **Conexões** | Acessa suas coisas | "O que há no meu calendário amanhã e quais tarefas vencem?" -> dados ao vivo, sem colar nada |
| 3 | **Capacidades** | Sabe fazer o trabalho | Uma frase curta dispara um workflow de várias etapas que produz um artefato |
| 4 | **Cadência** | Roda sem ser solicitado | Notebook fechado. Um resumo chega na caixa de entrada. Um colega manda mensagem e recebe uma resposta real |

**Linha de marca:** Contexto. Conexões. Capacidades. Cadência.

> *The Four Cs of an AIOS(TM) é uma marca registrada de Nate Herk. © 2026 Nate Herk.*

Grafo de dependência: Contexto não pode ser pulado. Conexões + Capacidades podem ser construídas em paralelo. Cadência vem por último - não automatize workflows que ainda não funcionam manualmente.

---

## O que vem no kit - 3 habilidades

O kit é intencionalmente enxuto. As habilidades aqui são prompts de ideação e ferramentas de pensamento, não automações pesadas. Você constrói em cima da estrutura.

| Habilidade | Tipo | Quando executar |
|---|---|---|
| `/onboard` | Assistente de configuração (uma vez) | Dia 1, imediatamente após clonar. Entrevista de 7 perguntas. Gera o conjunto de arquivos do Dia 1 + preenche `CLAUDE.md`. |
| `/audit` | Habilidade recorrente de pensamento | Dia 7, depois semanalmente. Relatório de lacunas dos Quatro Cs. Somente leitura. Veja a pontuação subir. |
| `/level-up` | Habilidade recorrente de pensamento | Dia 14, depois semanalmente. Entrevista dos Três Ms (Mindset -> Método -> Máquina). Uma execução = um artefato entregue. |

`/audit` pergunta *"o AIOS foi construído corretamente?"* (forma). `/level-up` pergunta *"qual alavancagem de negócio estou deixando passar?"* (função). Elas trabalham em série - corrija a estrutura primeiro, então o planejamento de capacidades passa a fazer sentido.

---

## Começo rápido

1. **Clone o repositório** para uma pasta de trabalho na sua máquina.
2. **Abra no Claude Code** e execute `/onboard`. Responda às 7 perguntas com honestidade. Amostras de voz devem ser coladas, não descritas. Leva cerca de 15 minutos. O conjunto de arquivos do Dia 1 é criado ao final.
3. **Use por uma semana.** Traga perguntas reais. Tome decisões reais. Registre-as via `/decision` ou apenas acrescente em `decisoes/registro.md`.
4. **Dia 7:** execute `/audit`. Leia o relatório de lacunas dos Quatro Cs. Escolha uma lacuna para fechar.
5. **Dia 14:** execute `/level-up`. A entrevista dos Três Ms revela uma automação que vale construir. Construa.
6. **Semana 3+:** ritual semanal de `/level-up`. Um artefato entregue por semana.

---

## Estrutura do repositório

```
AIS-OS/
├── LEIA-ME.md
├── CLAUDE.md                        <- Seu manual operacional (preenchido pelo /onboard)
├── EXPANSOES.md                     <- O que adicionar conforme você cresce
├── LICENCA
├── .gitignore
├── entrada-aios.md                  <- Fonte da verdade para /onboard. Edite + execute novamente quando quiser.
├── conexoes.md                      <- Registro de todo sistema que seu AIOS pode acessar
├── contexto/                        <- Sobre você e seu negócio (preenchido pelo /onboard)
├── referencias/
│   └── framework-3ms.md             <- O cérebro do operador
├── decisoes/
│   └── registro.md                  <- Registro somente de acréscimo do que foi decidido e por quê
├── arquivos/                        <- Coisas antigas. Não exclua. Mova para cá.
└── .claude/
    └── skills/
        ├── onboard/SKILL.md
        ├── audit/SKILL.md
        └── level-up/SKILL.md
```

Veja `EXPANSOES.md` para saber o que adicionar conforme cresce (`projetos/`, `modelos/`, `scripts/`, `.claude/agents/`, pastas sub-OS etc.).

---

## Licença + atribuição

Licença MIT. © 2026 Nate Herk.

The Three Ms of AI(TM) e The Four Cs of an AIOS(TM) são marcas registradas de Nate Herk. Os dois frameworks acompanham este repositório com atribuição. Use livremente; não reempacote como se fossem seus.

O vídeo de masterclass complementar percorre o kit passo a passo. O link será adicionado aqui quando for publicado.
