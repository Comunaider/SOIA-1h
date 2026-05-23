# EXPANSIONS - o que adicionar conforme você cresce

O kit vem enxuto de propósito. Três habilidades, seis pastas, uma referência de framework. Só isso. Conforme você usa, vai ultrapassar a base - este guia diz o que adicionar, quando e por quê.

A estrutura do AIOS deve parecer uma pequena empresa bem administrada. Não o porão de um acumulador.

---

## O que vem no kit (não remova)

| Pasta / arquivo | Propósito |
|---|---|
| `contexto/` | Sobre você, seu negócio e suas prioridades. Preenchido por `/onboard`. |
| `referencias/` | Frameworks, amostras de voz, guias de API e SOPs conforme você os constrói. |
| `decisoes/registro.md` | Registro somente de acréscimo do que foi decidido e por quê. |
| `arquivos/` | Arquivos antigos. Não exclua - mova para cá. |
| `conexoes.md` | Registro de todo sistema que seu AIOS pode acessar. |
| `.claude/skills/` | Suas habilidades: `/onboard`, `/audit`, `/level-up`. Adicione mais via `/level-up`. |
| `entrada-aios.md` | Fonte da verdade para `/onboard`. Edite e execute novamente quando quiser. |
| `CLAUDE.md` | Manual operacional raiz. Preenchido por `/onboard`. Edite quando seu papel/voz mudar. |

---

## O que adicionar conforme você cresce

| Pasta / arquivo | Adicione quando | Por quê |
|---|---|---|
| `projetos/` | Você começa a tocar 2+ frentes de trabalho contínuas com contexto próprio | Projetos ativos precisam de contexto delimitado separado dos arquivos permanentes em `contexto/` |
| `modelos/` | Você se pega copiando e colando os mesmos prompts ou estruturas de documentos | Pontos de partida reutilizáveis e parametrizados; reduz deriva |
| `ativos-marca/` | Você gera conteúdo visual (carrosséis, slides, thumbnails, imagens) | Centraliza logos, paletas, fontes, voz/tom - o AIOS consulta isso em vez de adivinhar |
| `referencias/sops/` | Você documenta como processos recorrentes rodam | Procedimentos operacionais padrão que o AIOS lê para executar com consistência |
| `referencias/{ferramenta}-api.md` | Você conecta uma nova API ou MCP e descobre como ela funciona | Pesquisado uma vez, salvo para sempre. `/audit` recompensa isso; habilidades futuras não pesquisam tudo de novo. |
| `scripts/` | Você escreve Python ou Bash para chamar APIs não cobertas por MCPs | A segunda conexão da maioria das pessoas é um script, não um MCP |
| `.claude/agents/` | Você precisa de um subassistente para pesquisa/escrita repetível de várias etapas | Agentes rodam em modelos mais baratos no próprio contexto - mantenha a sessão principal enxuta |
| Pastas sub-OS (ex.: `youtube-os/`) | Você tem uma vertical com dados, planilhas, transcrições e scripts próprios | Padrão de isolamento - workflows verticais recebem seu próprio manual operacional delimitado + habilidades |

---

## Cadências sugeridas

Quando cada superfície é tocada rotineiramente:

- `decisoes/registro.md` - toda decisão significativa (`/level-up` Fase 2 captura isso automaticamente)
- `arquivos/` - limpeza trimestral; mova projetos obsoletos, habilidades descontinuadas, versões antigas do intake
- `referencias/sops/` - quando um processo for reexecutado por alguém novo, escreva a SOP
- `conexoes.md` - toda vez que uma nova ferramenta for conectada, adicione uma linha
- `referencias/{ferramenta}-api.md` - no mesmo momento da atualização de `conexoes.md`; capture a API uma vez
- `CLAUDE.md` - revisão trimestral; reescreva a seção de persona/prioridades após `/level-up` Q90

---

## O que NÃO adicionar

Antipadrões. Parecem úteis, mas apodrecem a estrutura:

- **Não despeje arquivos brutos de e-mail/Slack em `referencias/`.** A wiki não é depósito de documentos. Apenas fatos interpretados.
- **Não crie pasta dentro de pasta por teatro organizacional.** Estrutura plana com bons nomes vence aninhamento profundo. Se você precisa de hierarquia de pastas para encontrar algo, tem um problema de busca, não de organização.
- **Não adicione `notas/`, `misc/`, `tmp/` ou `entrada/`.** Cemitérios. Use `arquivos/` se for antigo; escreva um arquivo real no lugar certo se for novo.
- **Não pré-crie pastas de que ainda não precisa.** Pastas vazias são ruído. O AIOS dirá quando for hora.
- **Não mantenha `decisoes.md` e `decisoes/registro.md` paralelos.** Escolha um. O kit vem com `decisoes/registro.md`.
- **Não bifurque seu manual operacional.** Um `CLAUDE.md` na raiz. Pastas sub-OS podem ter o próprio `CLAUDE.md` delimitado, mas a raiz é canônica.

---

## Como saber quando é hora de adicionar uma pasta

Faça três perguntas:

1. **Isto é conceitualmente novo?** Ou cabe em algum lugar existente?
2. **Vou tocar nisso 3+ vezes no próximo mês?** Se não, é prematuro.
3. **`/level-up` poderia direcionar naturalmente uma habilidade futura para cá?** Se sim, o AIOS vai usar. Se não, você está organizando para si mesmo, não para o sistema.

Dois "sim" = adicione. Um "sim" = espere.

---

> *A estrutura do seu AIOS deve parecer uma pequena empresa bem administrada - não o porão de um acumulador. Quando você não consegue encontrar algo, isso é um sinal para consolidar, não para adicionar outra pasta.*
