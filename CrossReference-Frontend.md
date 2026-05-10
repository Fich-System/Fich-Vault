# Cross-Reference — Frontend

Mapa de correspondência entre entidades EAV do backend e páginas de configuração no frontend Flutter.

## Grupo A — Concluído ✅

| Backend (Issue) | Migration | Frontend (PR) | Branch | Página |
|-----------------|-----------|---------------|--------|--------|
| — (entidade nativa) | — | #106 | feat/eav-plano-contas | PlanoContasEavConfigPage |
| — (entidade nativa) | — | #107 | feat/eav-fornecedor | FornecedorEavConfigPage |
| — (entidade nativa) | — | #108 | feat/eav-funcionario | FuncionarioEavConfigPage |
| — (entidade nativa) | — | #109 | feat/eav-grupo | GrupoEavConfigPage |
| — (entidade nativa) | — | #110 | feat/eav-cliente | ClienteEavConfigPage |
| — (entidade nativa) | — | #111 | feat/eav-centro-custo | CentroDeCustoEavConfigPage |

> **Nota:** As entidades do Grupo A (PlanoContas, Fornecedor, Funcionario, Grupo, Cliente, CentroDeCusto) são entidades nativas do sistema que ganharam páginas de configuração dinâmica no frontend. Elas não passaram por migração EAV no backend (são entidades principais, não auxiliares).

## Grupo B — Pendente 🟡

| # | Entidade Frontend | Branch | PR | Status |
|---|-------------------|--------|-----|--------|
| #105 | Sinistro | | | ⏳ Pendente |
| #104 | ChecklistManutencao | | | ⏳ Pendente |
| #103 | Troca | | | ⏳ Pendente |
| #102 | Certificacao | | | ⏳ Pendente |
| #101 | OrdemServico | | | ⏳ Pendente |
| #100 | Pneu | | | ⏳ Pendente |
| #99 | Rodizio | | | ⏳ Pendente |
| #98 | Multa | | | ⏳ Pendente |
| #97 | Estoque | | | ⏳ Pendente |
| #96 | NfeEntrada | | | ⏳ Pendente |
| #95 | Manutencao | | | ⏳ Pendente |
| #94 | Abastecimento | | | ⏳ Pendente |
| #93 | ChecklistVeiculos | | | ⏳ Pendente |
| #88 | TransferenciaBancaria | | | ⏳ Pendente |
| #87 | MovimentacaoBancaria | | | ⏳ Pendente |
| #86 | Inventario | | | ⏳ Pendente |
| #85 | MovimentacaoEstoque | | | ⏳ Pendente |

## Grupo C — Pendente 🟢

| # | Entidade Frontend | Branch | PR | Status |
|---|-------------------|--------|-----|--------|
| #92 | NotaFiscalServico | | | ⏳ Pendente |
| #91 | Servico | | | ⏳ Pendente |
| #90 | RegraTributacao | | | ⏳ Pendente |
| #89 | SubGrupo | | | ⏳ Pendente |

## Backend EAV (Migration) ↔ Frontend Cross-Reference

Mapeamento das migrações EAV do backend para possíveis futuras páginas de configuração no frontend.

| Backend Migration | Entidade EAV | Frontend Page | Status Frontend |
|-------------------|--------------|---------------|-----------------|
| V94 | Ocorrencia | — | ❌ Não iniciado |
| V95 | AlertaManutencao | — | ❌ Não iniciado |
| V96 | WorkflowManutencao | — | ❌ Não iniciado |
| V97 | AvaliacaoFornecedor | — | ❌ Não iniciado |
| V98 | CompetenciaTecnica | — | ❌ Não iniciado |
| V99 | LimiteConsumoCombustivel | — | ❌ Não iniciado |
| V100 | ProdutoAvaliacao | — | ❌ Não iniciado |
| V101 | FuncionarioBeneficio | — | ❌ Não iniciado |
| V102 | CertificacaoTecnico | — | ❌ Não iniciado |
| V103 | TreinamentoTecnico | — | ❌ Não iniciado |

> **Nota:** As entidades auxiliares migradas para EAV no backend (Grupo C backend) são configurações avançadas que podem ou não precisar de páginas de configuração dinâmica no frontend. A decisão é de produto/arquitetura.

## Resumo

| Grupo | Entidades | Frontend | Backend |
|-------|-----------|----------|---------|
| Grupo A | 6 | ✅ Concluído | Entidades nativas |
| Grupo B | 17 | ⏳ Pendente | Entidades nativas |
| Grupo C | 4 | ⏳ Pendente | Entidades nativas |
| Backend EAV | 10 | ❌ Não iniciado | ✅ Concluído (V94–V103) |

**Total frontend: 27 entidades | 6 concluídas | 21 pendentes | 10 backend EAV sem frontend**

---

*Última atualização: 2026-05-10*
