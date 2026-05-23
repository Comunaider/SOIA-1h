# Intake do AIS-OS

Este é o arquivo fonte da verdade do seu AIOS. Preencha digitando, colando por voz (Wispr Flow / ditado do sistema operacional) ou executando `/onboard` para uma conversa guiada. Seja qual for o modo, este arquivo é o que `/onboard` lê para montar sua configuração do Dia 1.

**Limite rígido: 7 perguntas.** Cada uma pode ser respondida em menos de 60 segundos. Não pense demais - você pode editar e executar `/onboard` novamente a qualquer momento.

---

## Q1 - Quem é você, o que você vende e para quem vende?

Identidade, oferta, ICP. Um parágrafo para cada é suficiente.

```
[Sua resposta aqui]
```

---

## Q2 - Cole 1-2 coisas que você escreveu recentemente. Não edite.

Um e-mail, um post no LinkedIn, uma DM, um documento - qualquer coisa que soe como você quando não está tentando forçar. **Cole literalmente.** Não digite esses textos no meio da conversa com o Claude - amostras moldadas por chat são piores do que nenhuma amostra (contaminação de voz).

```
[Amostra 1 - cole o texto bruto]
```

```
[Amostra 2 - cole o texto bruto]
```

---

## Q3 - Quais são suas 2-3 maiores prioridades para os próximos 90 dias?

Prioridades trimestrais. Não aspirações anuais. Coisas que, se não forem feitas até julho, fariam você dizer "desperdicei o Q2".

```
1. [Prioridade 1]
2. [Prioridade 2]
3. [Prioridade 3]
```

---

## Q4 - Onde a receita realmente cai e onde ela é acompanhada?

Várias respostas são aceitáveis. Stripe? Skool? GoHighLevel? QuickBooks? Uma planilha?

```
[Sua resposta aqui]
```

---

## Q5 - Onde você conversa com clientes, equipe e mundo externo no dia a dia?

E-mail (qual - Gmail / Outlook)? Slack? Teams? DMs (Skool / Discord / iMessage)? Telefone?

```
[Sua resposta aqui]
```

---

## Q6 - Onde ficam gravações de reuniões, notas e documentos importantes?

Granola? Otter? Fireflies? Google Drive? Notion? Dropbox? Uma pasta na área de trabalho que você vive querendo organizar?

```
[Sua resposta aqui]
```

---

## Q7 - Qual é a tarefa que consome sua semana e onde você acompanha o trabalho hoje?

A maior fonte única de perda de tempo ou tarefa recorrente chata. Além disso, onde tarefas/projetos ficam (ClickUp / Asana / Linear / Notion / um caderno).

```
[Sua resposta aqui]
```

---

Quando este arquivo estiver preenchido, execute `/onboard` ou execute novamente. O assistente montará seu conjunto de arquivos do Dia 1: `contexto/`, `referencias/voz.md`, `conexoes.md` preenchido e `CLAUDE.md` preenchido.
