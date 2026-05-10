# MEMORY.md — Memória de Longo Prazo do Jarvis

Registro curado de decisões, eventos e aprendizados. Atualizado periodicamente.

---

## 2026-05-10 — Conclusão do Grupo A (Frontend EAV)

**Contexto:** FICH-RETAGUARDA — Frontend Flutter.

O **Grupo A** das páginas de configuração EAV foi concluído com sucesso. São 6 entidades de alta prioridade que agora possuem interface completa de configuração dinâmica (abas, grupos, campos):

| # | Entidade | PR |
|---|----------|-----|
| #84 | PlanoContas | #106 |
| #83 | Fornecedor | #107 |
| #82 | Funcionario | #108 |
| #81 | Grupo | #109 |
| #80 | Cliente | #110 |
| #79 | CentroDeCusto | #111 |

**Detalhes técnicos:**
- 43 arquivos no diretório `lib/pages/configuracoes/eav/` (42 páginas + 1 helper)
- Padrão de 7 arquivos por entidade: eav_config_page, abas_page, aba_form_page, grupos_page, grupo_form_page, campos_page, campo_form_page
- Componentes reutilizáveis: BaseLayout, PaginationSection, ApiService
- Cada branch nomeada como `feat/eav-{entidade}`

**Próximos passos:**
- Grupo B: 17 entidades (média prioridade) — pending
- Grupo C: 4 entidades (baixa prioridade) — pending
- Backend EAV (Grupo C): 10 migrações concluídas (V94–V103), sem frontend ainda

**Vault atualizado:**
- `Modulos/EAV-Frontend.md` — Documentação completa do módulo
- `Issues-Front-Tracking.md` — Grupo A marcado como concluído
- `CrossReference-Frontend.md` — Mapa backend ↔ frontend
- `Pendentes.md` — Seção de frontend adicionada

---

## Padrões e Convenções

### Branches
- Frontend: `feat/eav-{entidade}` (snake_case)
- Backend: `feat/eav-{entidade}` (snake_case)

### PRs
- 1 PR por entidade
- Linka a issue correspondente (`Closes #NN`)
- Só merge após QA aprovar

### Vault
- Documentação em `Modulos/` — arquivos Markdown em português
- Tracking em `Issues-*-Tracking.md`
- Cross-reference em `CrossReference*.md`

---

*Este arquivo é mantido pelo Jarvis. Atualizado conforme novos eventos significativos.*
