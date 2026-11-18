# rustcord

## Roteamento de skills (obrigatório)

Antes de agir em qualquer pedido, faça este roteamento — sem esperar o usuário citar a skill:

1. **Classifique a tarefa** em uma ou mais áreas da tabela abaixo. Uma tarefa pode cair em várias (ex.: "criar a tela de login" = UI + código).
2. **Liste as skills instaladas** em `.claude/skills/*/SKILL.md` (e as de plugins listadas na sessão) e leia a descrição de **todas** as skills da área — não pare na primeira que serve. A tabela é o ponto de partida; uma skill instalada depois, que não está nela, também entra se a descrição dela casar com a tarefa.
3. **Carregue com a ferramenta Skill cada uma que se aplica**, antes de escrever código ou texto. Diga em uma linha quais carregou e por quê.
4. **Conflito entre skills** (ex.: duas regras de estilo ou de movimento que se contradizem): siga a que casa com o pedido ou com o que o projeto já usa; se nada decide, pergunte ao usuário.
5. Skills marcadas como "só sob demanda" na descrição ficam de fora, a menos que o usuário peça.

| Área | Quando | Skills |
|---|---|---|
| **UI / frontend** | tela, componente, página, layout, estilo, visual, UX | `frontend-design` (construir), `web-design-guidelines` (revisar UI), `emil-design-eng` (polimento e decisões de componente), `apple-design` (movimento fluido, springs, profundidade), `find-animation-opportunities` (onde animar), `animation-vocabulary` (nomear um efeito), `ask-sonner` (só se usar Sonner/toasts) |
| **Planejar algo novo** | ideia ainda aberta, feature grande | `grill-with-docs` → `to-spec` → `to-tickets` → `implement` (um ticket por sessão; siga a ordem) |
| **Código** | escrever, alterar, refatorar, corrigir | `coding-guidelines` sempre; em código Rust, também `ecc:rust-patterns` (idiomas, ownership, erros, concorrência) e `ecc:rust-testing` (ao escrever ou mudar testes) |
| **Decisão de arquitetura** | já decidida, registrar o porquê | `create-adr` |
| **Design técnico** | antes de implementar algo grande | `technical-design-doc-creator` |
| **Documentação** | README, guias, `/docs` | `docs-writer` |
| **Trabalho autônomo** | "resolve sozinho", "sem me perguntar" | `not-your-babysitter` |
| **Commit** | qualquer commit ou mensagem de commit | `write-commit` |
