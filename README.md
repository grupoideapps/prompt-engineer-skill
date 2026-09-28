# /prompt-engineer — skill de engenharia de prompt para o Claude

Skill que faz o Claude criar, refinar e validar prompts usando uma **estrutura obrigatória de 6 partes**:

1. **ROLE** — quem a IA é nessa conversa
2. **TASK** — o que ela precisa entregar (e o critério de sucesso)
3. **INPUTS / DADOS** — os fatos e arquivos que você dá
4. **CONTEXT** — quem você é, pra quem é, por quê
5. **SPECIFICS** — processo de execução e formato da saída
6. **NOTES** — restrições, protocolo de incerteza e validação final

Inclui técnicas avançadas (Chain-of-Thought, Few-Shot, RAG, Prompt Chaining, Self-Correction, Step-Back) e um fluxo de
**diagnóstico**: quando a resposta vem ruim, a tabela mostra qual das 6 partes reforçar.

## Como instalar

**Claude Code** — copie a pasta `prompt-engineer` para `~/.claude/skills/`:

```bash
git clone https://github.com/grupoideapps/prompt-engineer-skill.git
cp -r prompt-engineer-skill/prompt-engineer ~/.claude/skills/
```

Depois é só pedir: *"usa a skill prompt-engineer pra montar um prompt que…"* ou digitar `/prompt-engineer`.

**Claude.ai (app/web)** — compacte a pasta `prompt-engineer` em `.zip` e envie em *Configurações → Capacidades → Skills*.

## Estrutura

```
prompt-engineer/
├── SKILL.md                       # instruções e fluxos (criação e refinamento)
└── references/
    ├── prompt_structure.md        # as 6 partes, com exemplos
    └── advanced_techniques.md     # CoT, Few-Shot, RAG, chaining, self-correction…
```

---
Feita por **Luan Lucas Bonadie** · Instagram [@omentor.ai](https://www.instagram.com/omentor.ai/)
