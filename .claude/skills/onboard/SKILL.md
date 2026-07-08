---
name: onboard
description: Use no Dia 1 de uma instalação AIS-OS, quando alguém diz "configure para mim", "faça meu onboarding", "vamos começar", "preencha meu AIOS", ou acabou de clonar o kit. Assistente combinado - roda o intake de 7 perguntas E monta o conjunto de arquivos do Dia 1 ao final. Idempotente - execute novamente a qualquer momento após editar entrada-aios.md.
---

## O que esta habilidade faz

Assistente combinado único. Lê ou escreve `entrada-aios.md` (o intake canônico), conduz a entrevista de 7 perguntas se o arquivo não estiver preenchido e então monta o conjunto de arquivos do Dia 1 diretamente ao final da execução. Não há uma habilidade separada `/scaffold-from-intake` - este é um fluxo único.

**O momento "uau":** no final, sugira o prompt de fechamento *"Teste isto - pergunte: no que devo focar esta semana?"* O usuário executa uma vez. Esse é o "uau". Não há habilidade `/today` para salvar - o próprio prompt planta o framework de Mindset (Mudança de Padrão) para ele internalizar.

## Quando NÃO executar isto

- Se o usuário já fez onboarding e quer atualizar: ainda execute, mas pule perguntas já respondidas (idempotente).
- Se o usuário quer adicionar uma nova conexão: isso não é onboarding - direcione para editar `conexoes.md` diretamente, ou agende uma caminhada pela Fase 2 de `/level-up`.

## Execução

### Etapa 1: Ler o intake

Leia `entrada-aios.md`. Verifique quais seções Q1-Q7 têm conteúdo versus placeholders `[Sua resposta aqui]`.

- **Tudo preenchido** -> pule a Etapa 2, vá para a Etapa 3 (montagem).
- **Algumas preenchidas** -> pergunte ao usuário: "Vejo que Q1, Q3, Q4 estão respondidas. Quer preencher o restante agora ou montar a partir do que já existe?" A escolha é dele.
- **Nenhuma preenchida (clone novo)** -> rode a Etapa 2 em conversa.

### Etapa 2: A entrevista (7 perguntas, limite rígido)

Pergunte uma de cada vez. Escreva cada resposta em `entrada-aios.md` conforme avança (assim o usuário pode retomar se for interrompido).

**Q1 - Quem é você, o que você vende e para quem vende?**
Identidade, oferta, ICP. Um parágrafo para cada é suficiente.

**Q2 - Cole 1-2 coisas que você escreveu recentemente. Não edite.**
*Esta é a única pergunta com regra rígida.* Amostras de voz DEVEM ser coladas, não digitadas no meio da conversa. Se o usuário começar a digitar prosa nova, recuse:

> *"Pare - cole o texto bruto. Se você digitar aqui enquanto conversamos, a amostra já estará moldada pela nossa conversa. Abra seu último e-mail ou post do LinkedIn em outra aba e cole o texto sem edição. Esta é a única regra que não posso flexibilizar."*

Peça duas amostras. Um e-mail, um post. Ou duas de qualquer tipo.

**Q3 - Quais são suas 2-3 maiores prioridades para os próximos 90 dias?**
Prioridades trimestrais. Questione se ele disser "crescer meu negócio" - faça nomear um número, prazo ou entrega.

**Q4 - Onde a receita realmente cai e onde ela é acompanhada?**
Várias respostas são aceitáveis. Mapeie para Domínio Tier-1 1 (Receita/Financeiro).

**Q5 - Onde você conversa com clientes, equipe e mundo externo no dia a dia?**
E-mail (Gmail/Outlook), Slack/Teams/Discord, DMs. Mapeie para Domínios 2 + 4.

**Q6 - Onde ficam gravações de reuniões, notas e documentos importantes?**
Mapeie para Domínios 6 + 7.

**Q7 - Qual é a tarefa que consome sua semana e onde você acompanha o trabalho hoje?**
Capture top_pain (usado por `/level-up` no Dia 14) + Domínio 5 (tarefas).

Domínio 3 (Calendário) é inferido automaticamente da Q5: Gmail -> Google Cal; Outlook -> Outlook Cal. Confirme na Etapa 3.

### Etapa 3: Montar o conjunto de arquivos do Dia 1

Quando o intake estiver completo, gere estes arquivos (ou atualize se estiver reexecutando). Faça backup dos originais em `arquivos/intake-{YYYY-MM-DD-HHMM}/` se algum já existir.

1. **`contexto/sobre-mim.md`** - a partir da Q1 (identidade, papel) + Q7 (top_pain). Um parágrafo curto para cada.
2. **`contexto/sobre-negocio.md`** - a partir da Q1 (oferta, ICP) + Q4 (modelo de receita). Um parágrafo.
3. **`contexto/prioridades.md`** - a partir da Q3. Lista numerada, uma linha por prioridade.
4. **`referencias/voz.md`** - a partir da Q2. Cole amostras literalmente com um cabeçalho curto explicando o uso ("Combine este registro ao rascunhar; não finja a voz em conteúdo externo sem me mostrar primeiro").
5. **`conexoes.md`** - preencha a tabela de 7 linhas a partir das respostas Q4-Q7. Cada linha recebe `mecanismo: ainda não conectado`, `autenticação: -`, `última verificação: -`. O usuário conecta ferramentas no Dia 2.
6. **`AGENTS.md`** - preencha todos os placeholders `{{...}}`. Substitua o nome do usuário, prioridade declarada, resumo do registro de voz e um breve resumo de conexões. Não toque em `CLAUDE.md` nem `GEMINI.md` - são espelhos que apenas importam `AGENTS.md`.

### Etapa 4: A tela de fechamento

Imprima uma tela. Três linhas no máximo:

```
✓ Dia 1 concluído. Seu AIOS sabe quem você é, o que vende, o que importa neste trimestre e como você soa.

Hoje: pergunte - "no que devo focar esta semana?"
Amanhã: escolha uma ferramenta em conexoes.md e conecte (instalação manual de MCP ou escreva um pequeno script de API + salve referencias/{ferramenta}-api.md).
Dia 7: execute /audit para ver sua pontuação.
```

Quando o usuário executar o prompt de fechamento ("no que devo focar esta semana?"), responda usando apenas os novos arquivos de contexto. Inclua:
- lista de 3 bullets de prioridade, no registro de voz dele a partir da Q2
- cada bullet ligado a uma prioridade declarada de 90 dias da Q3
- linha final: *"Se eu tivesse que escolher uma coisa para segunda-feira, seria [X], porque [motivo das prioridades]. Quer que eu rascunhe o primeiro e-mail? E onde a Mudança de Padrão poderia se aplicar aqui? Até que ponto a IA poderia ser aproveitada nesta tarefa?"*

A pergunta de Mudança de Padrão semeia o framework de Mindset antes de `/level-up` apresentá-lo formalmente no Dia 14.

## Regras críticas de implementação

1. **O limite de 7 perguntas não é negociável.** Não adicione Q8 na conversa.
2. **A colagem de voz não pode ser pulada.** Se o usuário digitar amostras no chat, recuse e peça para colar de uma escrita real.
3. **Montagem em uma única passada.** Depois que a Etapa 2 termina, escreva os arquivos da Etapa 3 em um único lote. Sem confirmação multi-turno. O usuário itera editando `entrada-aios.md` e executando novamente.
4. **Idempotente.** Reexecutar com um intake editado atualiza arquivos de contexto; cria backup em `arquivos/intake-{ts}/`. Pula perguntas já respondidas, salvo se o usuário quiser revisar.
5. **Tela de fechamento tem três linhas.** Não é um menu.
6. **Nenhuma habilidade extra gerada.** Não monte `/today`, `/draft`, `/connect` etc. O kit vem com 3 habilidades; o usuário cria mais via `/level-up`.
7. **Somente leitura em `referencias/framework-3ms.md`.** Ele já vem no kit. Não sobrescreva.
8. **Sem escrita em `.env`.** Não peça chaves de API no Dia 1. Conexões vêm no Dia 2.

## Verificação (para o implementador)

- Teste frio: clone um kit novo, execute `/onboard`, preencha 7 respostas, a montagem roda, pergunte o prompt "uau"; a resposta cita Q1 + Q3 + Q7 especificamente. Genérico = falha.
- Idempotência: execute `/onboard` novamente com uma prioridade Q3 alterada. Esperado: apenas `contexto/prioridades.md` e a seção de prioridade de `AGENTS.md` são atualizadas; backup criado em `arquivos/intake-{ts}/`.
- Rejeição de voz: digite uma amostra no meio do chat. Esperado: a habilidade recusa e pede colagem.

> *Adaptado de The Three Ms of AI(TM) © 2026 Nate Herk. A linguagem de Mindset usada na tela de fechamento vem de `referencias/framework-3ms.md`.*
