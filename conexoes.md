# Conexões

Registro de todo sistema que seu AIOS pode acessar. Preenchido por `/onboard` a partir das respostas Q4-Q7; expandido ao longo do tempo conforme você conecta novas ferramentas. `/audit` verifica este arquivo quanto à cobertura de domínios e atualização.

| # | Domínio | Ferramenta | Mecanismo | Autenticação | Última verificação |
|---|---|---|---|---|---|
| 1 | Receita / Financeiro | _preenchido por /onboard_ | ainda não conectado | - | - |
| 2 | Interações com clientes | _preenchido por /onboard_ | ainda não conectado | - | - |
| 3 | Calendário | _preenchido por /onboard_ | ainda não conectado | - | - |
| 4 | Comunicação | _preenchido por /onboard_ | ainda não conectado | - | - |
| 5 | Gestão de projetos / tarefas | _preenchido por /onboard_ | ainda não conectado | - | - |
| 6 | Inteligência de reuniões | _preenchido por /onboard_ | ainda não conectado | - | - |
| 7 | Conhecimento / arquivos | _preenchido por /onboard_ | ainda não conectado | - | - |

**Opções de mecanismo:** `mcp` (servidor MCP), `script` (Python/Bash chamando uma API, em `scripts/`), `export` (pipeline de dump CSV/JSON), `key+ref` (chave em `.env` + guia `referencias/{ferramenta}-api.md`), `ainda não conectado`.

Quando conectar uma nova ferramenta, também salve `referencias/{ferramenta}-api.md` com endpoints, fluxo de autenticação e consultas comuns - pesquisado uma vez, salvo para sempre.
