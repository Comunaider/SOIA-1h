# Conexões

Mapa de todo sistema que o SOIA acessa. **Este arquivo é mapa, não manual:** cada linha diz o que existe, o comando que funciona para falar com aquilo e onde está o detalhe.

Preenchido por `/onboard` a partir das respostas Q4-Q7 e expandido conforme você conecta ferramentas. Regra: nunca improvise um acesso. Se o sistema não está aqui, descubra uma vez e registre na mesma sessão, com data. `/audit` mede a cobertura.

| # | Domínio | Ferramenta | Como falo com ele | Detalhe | Verificado |
|---|---|---|---|---|---|
| 1 | Receita / Financeiro | _preenchido por /onboard_ | ainda não conectado | - | - |
| 2 | Interações com clientes | _preenchido por /onboard_ | ainda não conectado | - | - |
| 3 | Calendário | _preenchido por /onboard_ | ainda não conectado | - | - |
| 4 | Comunicação | _preenchido por /onboard_ | ainda não conectado | - | - |
| 5 | Gestão de projetos / tarefas | _preenchido por /onboard_ | ainda não conectado | - | - |
| 6 | Inteligência de reuniões | _preenchido por /onboard_ | ainda não conectado | - | - |
| 7 | Conhecimento / arquivos | _preenchido por /onboard_ | ainda não conectado | - | - |

**Como falo com ele:** o comando ou caminho exato que funciona. Exemplos: `python scripts/agenda.py amanha`, `MCP google-calendar`, `exportar CSV em dados/vendas.csv toda sexta`, `ainda não conectado`. Chaves e senhas ficam no `.env`, nunca aqui.

**Detalhe:** o arquivo com endpoints, autenticação e consultas comuns, normalmente `referencias/{ferramenta}-api.md`.

Quando conectar uma nova ferramenta, também salve `referencias/{ferramenta}-api.md` com endpoints, fluxo de autenticação e consultas comuns - pesquisado uma vez, salvo para sempre.
