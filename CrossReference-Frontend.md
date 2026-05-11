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
| #105 | Sinistro | feat/eav-sinistro | #112 | ✅ Concluído |
| #104 | ChecklistManutencao | feat/eav-checklist-manutencao | #113 | ✅ Concluído |
| #103 | Troca | feat/eav-troca | #114 | ✅ Concluído |
| #102 | Certificacao | feat/eav-certificacao | #115 | ✅ Concluído |
| #101 | OrdemServico | feat/eav-ordem-servico | #116 | ✅ Concluído |
| #100 | Pneu | feat/eav-pneu | #117 | ✅ Concluído |
| #99 | Rodizio | feat/eav-rodizio | #118 | ✅ Concluído |
| #98 | Multa | feat/eav-multa | #119 | ✅ Concluído |
| #97 | Estoque | feat/eav-estoque | #120 | ✅ Concluído |
| #96 | NfeEntrada | feat/eav-nfe-entrada | #121 | ✅ Concluído |
| #95 | Manutencao | feat/eav-manutencao | #122 | ✅ Concluído |
| #94 | Abastecimento | feat/eav-abastecimento | #123 | ✅ Concluído |
| #93 | ChecklistVeiculos | feat/eav-checklist-veiculos | #124 | ✅ Concluído |
| #88 | TransferenciaBancaria | feat/eav-transferencia-bancaria | #125 | ✅ Concluído |
| #87 | MovimentacaoBancaria | feat/eav-movimentacao-bancaria | #126 | ✅ Concluído |
| #86 | Inventario | feat/eav-inventario | #127 | ✅ Concluído |
| #85 | MovimentacaoEstoque | feat/eav-movimentacao-estoque | #128 | ✅ Concluído |

## Grupo C — Concluído ✅

| # | Entidade Frontend | Branch | PR | Status |
|---|-------------------|--------|-----|--------|
| #92 | NotaFiscalServico | feat/eav-notafiscal-servico | #129 | ✅ Concluído |
| #91 | Servico | feat/eav-servico | #130 | ✅ Concluído |
| #90 | RegraTributacao | feat/eav-regra-tributacao | #131 | ✅ Concluído |
| #89 | SubGrupo | feat/eav-subgrupo | #132 | ✅ Concluído |

## Backend EAV (Migration) ↔ Frontend Cross-Reference

Mapeamento das migrações EAV do backend para possíveis futuras páginas de configuração no frontend.

| Backend Migration | Entidade EAV | Frontend Page | Status Frontend |
|-------------------|--------------|---------------|-----------------|
| V94 | Ocorrencia | — | ❌ Não iniciado |
| V95 | AlertaManutencao | AlertaManutencao | ✅ Concluído PR #153 |
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
| Grupo B | 17 | ✅ Concluído | Entidades nativas |
| Grupo C | 4 | ✅ Concluído | Entidades nativas |
| Grupo D — Backend EAV | 10 | 🟢 1/10 concluído | ✅ Concluído (V94–V103) |

**Total frontend: 28 entidades | 28 concluídas | 0 pendente**

---

*Última atualização: 2026-05-10 — Grupo D Backend EAV iniciado: AlertaManutencao PR #153 ✅*
