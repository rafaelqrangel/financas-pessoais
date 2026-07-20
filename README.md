# Finanças Pessoais — Personal Financial Advisor

Sistema de consultoria financeira pessoal operado via Claude Code, no estilo didático de Gustavo Cerbasi.

## Arquitetura

```
┌─────────────────────────────┐
│  Claude Code (este repo)    │  ← cérebro executor
│  skill: personal-financial- │
│  advisor (estilo Cerbasi)   │
└──────┬──────────┬───────────┘
       │          │
       ▼          ▼
┌────────────┐  ┌──────────────────────┐
│ Google     │  │ NotebookLM           │
│ Drive      │  │ "Personal Financial  │
│ (planilhas │  │ Advisor"             │
│ da família)│  │ (base técnica)       │
└────────────┘  └──────────────────────┘
```

- **Cérebro executor**: a skill em `.claude/skills/personal-financial-advisor/` — persona, método de diagnóstico, frameworks de cálculo e tom de voz.
- **Dados reais**: planilhas do Google Drive (ORCAMENTO CASA, SEMEAR CASA - Dados, Assinaturas, faturas) acessadas via MCP.
- **Base técnica**: NotebookLM (consultado via protocolo de ponte — o advisor formula as perguntas, Rafael cola e traz as respostas).
- **Memória**: `knowledge/` guarda perfil, decisões e respostas técnicas entre sessões.

## Estrutura

```
.claude/skills/personal-financial-advisor/
├── SKILL.md                          # persona + método em 5 passos
└── references/
    ├── tom-de-voz-cerbasi.md         # os 7 traços do estilo
    ├── metodo-diagnostico.md         # 5 perfis + protocolo anti-sangria
    ├── frameworks-financeiros.md     # fórmulas (independência, aportes, fila de alocação)
    └── fontes-de-dados.md            # IDs das planilhas + ponte NotebookLM
knowledge/
├── perfil.md                         # retrato financeiro da família
├── decisoes.md                       # log de decisões com números
└── notebooklm/                       # espelho das consultas técnicas
```

## Missão (em ordem)

1. **Estancar a sangria** — juros, parcelas empilhadas, assinaturas, gastos invisíveis.
2. **Construir previsibilidade** — orçamento que projeta, não só registra.
3. **Crescer patrimônio** — meta, ritmo de aporte e alocação, com o tempo como aliado.
