---
name: level-up
description: Use semanalmente para encontrar e entregar uma nova automação. Conduz a entrevista dos 3Ms - Mindset (encontrar o candidato) -> Método (delimitar um) -> Máquina (construir). Dispare em "vamos evoluir", "o que devo automatizar agora", "encontre alavancagem esta semana" ou como ritual de sexta-feira. Uma execução = um artefato entregue.
---

> *Adaptado de The Three Ms of AI(TM). © 2026 Nate Herk. Todos os direitos reservados.*
> *The Three Ms of AI(TM) é uma marca registrada de Nate Herk.*

## O que esta habilidade faz

Conduz o usuário pelos 3Ms toda semana para revelar e entregar uma nova automação. **Uma entrevista = um artefato.** Também instala o framework 3Ms na cabeça do usuário ao longo do tempo - depois de 4-6 execuções, ele começa a perceber oportunidades no meio da semana sem prompt, porque as perguntas viraram padrões internos.

Este é o mecanismo de reprogramação do cérebro. O kit não precisa de cron jobs para fixar comportamento; precisa que `/level-up` rode toda sexta-feira.

## O que `/level-up` NÃO é

- Não é `/audit`. `/audit` é estrutural ("o AIOS foi construído corretamente?"). `/level-up` é funcional ("qual alavancagem de negócio estou deixando passar?"). Rode `/audit` primeiro se a estrutura estiver bagunçada.
- Não é um planejador de múltiplos candidatos. Uma execução = um artefato entregue.
- Não é coach. O usuário pensa. A habilidade conduz a entrevista.

## Quando `/level-up` roda

- **Primeira execução: Dia 14.** Depois que o usuário conectou >=1 MCP/script e executou `/audit` uma vez. Antes disso tende a produzir algo trivial.
- **Cadência: semanal, sexta-feira à tarde.** Revisar a semana, revelar uma automação, entregar na segunda.
- **Sob demanda a qualquer momento.** No meio da semana se uma tarefa manual estiver incomodando.

## Entradas que a habilidade lê

- `contexto/prioridades.md` - o que o usuário disse que importa
- `contexto/sobre-mim.md` - top_pain, papel
- `conexoes.md` - o que é acessível, por qual mecanismo
- `referencias/framework-3ms.md` - o framework (usado para citar princípios de volta)
- `decisoes/registro.md` - decisões recentes (o que já foi entregue ou considerado)
- frontmatter de `.claude/skills/*/SKILL.md` - quais capacidades existem
- `auditorias/auditoria-{date}.md` recente, se existir

## Execução - três fases

### Fase 1 - Entrevista de Mindset (encontrar o candidato)

Revele 1-3 candidatos ranqueados por alavancagem. Pergunte nesta ordem, em tom conversacional:

1. *"Me conte como foi sua semana. O que você fez 3+ vezes?"* (frequência)
2. *"Algo pareceu manual, chato ou de copiar e colar?"* (trabalho repetitivo)
3. *"Algo em que você pensou 'um estagiário inteligente daria conta disto'?"* (delegação)
4. *"Se 500 novos clientes aparecessem amanhã, o que quebraria primeiro?"* (restrição)
5. *"O que traria 500 clientes a mais amanhã?"* (alavanca de crescimento)

Cite princípios relevantes de Mindset quando couber:
- *"Parece que a Mudança de Padrão se aplica - até que ponto a IA poderia ser aproveitada aqui?"*
- *"Isto é a Quebra por Função - você não está automatizando o trabalho inteiro, só esta peça."*
- *"IA é melhor do que você pensa e melhora mais rápido do que você pensa. Se ela não conseguia fazer isto no trimestre passado, talvez já consiga agora."*

**Saída da Fase 1:** lista numerada de 1-3 oportunidades candidatas, cada uma com uma linha de "por que isto é alavancagem". Pergunte: *"Escolha uma para delimitar."*

### Fase 2 - Entrevista de Método (delimitar uma)

O usuário escolhe um candidato. Percorra o pipeline de Método em 5 etapas:

**Etapa 1 - Encontrar a restrição.** Qual gargalo isto resolve, ou qual alavanca de crescimento abre? Ligue de volta às respostas da Fase 1.

**Etapa 2 - EAD: Eliminar / Automatizar / Delegar.**
- **Eliminar primeiro:** *"O que acontece se simplesmente pararmos de fazer isto?"* Se a resposta for "nada quebra" -> a habilidade encerra de forma positiva. *"Não automatize desperdício."* Isso é uma vitória, registre em `decisoes/registro.md` e pare.
- **Automatizar em segundo:** aplique o enquadramento 60/30/10. Cerca de 60% determinístico, cerca de 30% assistido por IA, cerca de 10% manual.
- **Delegar em terceiro:** se for complexo/variável/dependente de julgamento demais -> sugira uma pessoa. A habilidade encerra com sugestão de delegação e registra.

**Etapa 3 - Mapear o processo.** Cinco elementos:
- Gatilho (o que inicia)
- Fontes de dados (de onde vem a informação)
- Transformações de dados (como os dados mudam de forma)
- Pontos de decisão (onde ramifica)
- Destino (para onde a saída vai)

Se o usuário não consegue articular qualquer um dos cinco: *"Se você não consegue explicar para uma pessoa, não consegue explicar para uma IA. Esboce no papel primeiro e depois volte."* A habilidade para.

**Etapa 4 - Escolher o nível de autonomia.**

| Nível | Nome | O que acontece |
|---|---|---|
| L0 | Manual | Sem IA |
| L1 | Sugerido | IA sugere, humano decide cada etapa |
| L2 | Rascunhado | IA rascunha, humano revisa e edita |
| L3 | Supervisionado | IA roda, humano valida periodicamente |
| L4 | Autônomo | IA executa de ponta a ponta |

**Padrão = menor nível que resolve o problema.** Questione L4, a menos que o usuário tenha rodado níveis inferiores explicitamente antes. *"Workflows vencem agentes. Se uma decisão não PRECISA ser tomada por IA, não deixe a IA tomar."*

**Etapa 5 - Ligar a um KPI.** Qual dos Três Baldes isto move?
- Mais clientes
- Mais valor por cliente
- Menos custo

Além de uma métrica específica (tempo de resposta, taxa de erro, taxa de conversão, tempo até conclusão). **Se o usuário não consegue nomear um balde e uma métrica, a habilidade para.** *"Se sua automação não move um número, por que você está construindo?"*

**Saída da Fase 2:** especificação de automação delimitada escrita em `decisoes/registro.md` como uma entrada datada com todas as cinco respostas + nível de autonomia + KPI. Registro durável do que foi decidido e por quê.

### Fase 3 - Transferência de Máquina (construir)

Pergunte: *"Como você quer entregar isto?"* Opções ordenadas pelo padrão Chato-é-Bonito:

1. **Somente prompt** - template de prompt salvo que o usuário roda à mão. Zero infraestrutura. Maior envolvimento manual.
2. **Habilidade determinística** - SKILL.md que roda um script (sem etapa de IA). Melhor para transformações com regras claras.
3. **Habilidade assistida por IA** - SKILL.md com uma chamada de IA dentro. Rascunha, classifica, resume.
4. **Subagente** - agente de várias etapas. Último recurso. Só se o trabalho realmente precisa de raciocínio + uso de ferramentas.

**Padrão selecionado = a opção sem IA mais alta que resolve o problema.** O usuário precisa escolher explicitamente mais autonomia.

Depois de escolhido, direcione ao scaffolder apropriado:
- `skill-creator` se disponível globalmente (enviado pela Anthropic)
- `skill-builder` se o usuário tiver localmente
- Caso contrário, escreva um SKILL.md / arquivo de agente diretamente com frontmatter, localização e conteúdo

**Todo artefato montado vem com estes dois cabeçalhos no topo:**

```markdown
---
bike-method-phase: 1  # Fase 1 - Rodinhas. Rode manualmente primeiro.
three-ms-attribution: |
  Adaptado de The Three Ms of AI(TM) © 2026 Nate Herk.
---
```

Isso trava o usuário na Fase 1 do Método da Bicicleta na primeira construção. Ele não consegue pular validação manual em silêncio. A fase só avança por edição explícita.

Mostre os princípios de Máquina ao montar:
- **Princípio Lego** - menores etapas, sem IA primeiro se possível
- **Cadeia de Validação** - teste cada etapa antes de encadear
- **Mentalidade de Iteração** - entregue o POC, expanda a partir do uso real

## Contrato de saída

Toda execução de `/level-up` produz:

1. **Uma entrada em `decisoes/registro.md`** - datada, com a especificação de Método
2. **Um artefato montado** - prompt, habilidade ou arquivo de agente
3. **Um fechamento de uma tela** - o que foi delimitado, o que foi construído e o lembrete da Fase 1 do Método da Bicicleta

## Regras críticas de implementação

1. **Uma entrevista = um artefato.** Sem delimitação paralela de múltiplos candidatos.
2. **A fase de Mindset sempre roda primeiro.** Mesmo se o usuário vier com uma ideia pronta.
3. **EAD impõe "eliminar primeiro".** Se a resposta for Eliminar, encerre de forma positiva - isso é vitória, não falha.
4. **Padrão para o menor nível de autonomia que funciona.** Questione L4.
5. **Padrão Chato-é-Bonito na transferência de Máquina.** Padrão = maior opção sem IA.
6. **Ligar a KPI é obrigatório.** Se o usuário não consegue nomear balde + métrica, pare.
7. **Método da Bicicleta acompanha todo artefato.** `bike-method-phase: 1` no frontmatter.
8. **Somente leitura em arquivos do usuário, exceto `decisoes/registro.md` e o novo artefato.** Não modifique outros arquivos existentes.
9. **Marca registrada + atribuição na saída.** Todo relatório e todo artefato montado referencia o framework.

## Verificação (para o implementador)

- **Dry run no Herk-2 do Nate** sem prompt. Esperado: a habilidade revela 2-3 candidatos puxados da atividade recente, prioridades e top_pain dele. Saída genérica ("você deveria construir um resumo") = falha.
- **Teste eliminar-primeiro.** Alimente um candidato obviamente eliminável. Esperado: a habilidade sugere Eliminar, encerra e registra a vitória.
- **Teste de questionamento L4.** Usuário pede respondedor autônomo de e-mail na primeira construção. Esperado: a habilidade insiste em L1/L2 primeiro, não entrega L4 sem override explícito.
- **Teste Chato-é-Bonito.** Candidato resolvível com Python determinístico. Esperado: a habilidade recomenda `(2) habilidade determinística` como padrão.
- **Antipulo do Método da Bicicleta.** Usuário monta, pede para avançar para Fase 4 imediatamente. Esperado: a habilidade faz ele ler o que cada fase significa e confirmar que validou as fases inferiores.

---

> *The Three Ms of AI(TM) é uma marca registrada de Nate Herk. © 2026 Nate Herk. Todos os direitos reservados.*
