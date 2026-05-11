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
| V94 | Ocorrencia | Ocorrencia | ✅ Concluído PR #163 |
| V95 | AlertaManutencao | AlertaManutencao | ✅ Concluído PR #153 |
| V96 | WorkflowManutencao | WorkflowManutencao | ✅ QA Aprovado PR #169 |
| V97 | AvaliacaoFornecedor | AvaliacaoFornecedor | ✅ Concluído PR #154 |
| V98 | CompetenciaTecnica | CompetenciaTecnica | ✅ Concluído PR #156 |
| V99 | LimiteConsumoCombustivel | — | ❌ Não iniciado |
| V100 | ProdutoAvaliacao | Produto | ✅ QA Aprovado PR #164 |
| V100 | ProdutoAvaliacao (avaliação) | ProdutoAvaliacao | ✅ QA Aprovado PR #165 |
| V101 | FuncionarioBeneficio | FuncionarioBeneficio | ✅ Concluído PR #159 |
| V102 | CertificacaoTecnico | — | ❌ Não iniciado |
| V103 | TreinamentoTecnico | TreinamentoTecnico | ✅ QA Aprovado PR #167 |

> **Nota:** As entidades auxiliares migradas para EAV no backend (Grupo C backend) são configurações avançadas que podem ou não precisar de páginas de configuração dinâmica no frontend. A decisão é de produto/arquitetura.

## Entidades Nativas com EAV (fora do V94-V103)

| # | Entidade Frontend | Branch | PR | Status | Backend Ref |
|---|-------------------|--------|-----|--------|-------------|
| #135 | BannerEcommerce | feat/eav-banner-ecommerce | #155 | ✅ Concluído | Controller #75 |
| #137 | ConfiguracaoEcommerce | feat/eav-configuracao-ecommerce | #157 | ✅ Concluído | Controller #76 |
| #139 | Driver | feat/eav-driver | #158 | ✅ Concluído | — |
| #140 | FuncionarioBeneficio | feat/eav-funcionario-beneficio | #159 | ✅ QA Aprovado | V101 |
| #141 | GrupoDestaque | feat/eav-grupo-destaque | #160 | ✅ QA Aprovado | Controller #76 |
| #143 | ManutencaoProgramada | feat/eav-manutencao-programada | #162 | ✅ Concluído | — |
| #145 | Produto | feat/eav-produto | #164 | ✅ QA Aprovado | V100 |
| #146 | ProdutoAvaliacao | feat/eav-produto-avaliacao | #165 | ✅ QA Aprovado | V100 |
| #148 | Titulo | feat/eav-titulo | #166 | ✅ QA Aprovado | — |
| #149 | TreinamentoTecnico | feat/eav-treinamento-tecnico | #167 | ✅ QA Aprovado | V103 |
| #150 | Veiculo | feat/eav-veiculo | #168 | ✅ QA Aprovado | — |
| #151 | WorkflowManutencao | feat/eav-workflow-manutencao | #169 | ✅ QA Aprovado | V96 |

## Resumo

| Grupo | Entidades | Frontend | Backend |
|-------|-----------|----------|---------|
| Grupo A | 6 | ✅ Concluído | Entidades nativas |
| Grupo B | 17 | ✅ Concluído | Entidades nativas |
| Grupo C | 4 | ✅ Concluído | Entidades nativas |
| Grupo D — Backend EAV | 10 (V-migration) + novas | 🟢 6/10 V-migration concluído + BannerEcommerce + ConfiguracaoEcommerce + Driver + FuncionarioBeneficio + GrupoDestaque + Produto + Titulo + TreinamentoTecnico ✅ | ✅ Concluído (V94–V103) + BannerEcommerce + ConfiguracaoEcommerce + Driver + FuncionarioBeneficio + GrupoDestaque + Produto + Titulo + TreinamentoTecnico (entidades nativas EAV) |

**Total frontend: 44 entidades | 32 concluídas | 12 QA Aprovado | 0 pendente**

---

*Última atualização: 2026-05-11 — Grupo D: WorkflowManutencao PR #169 ✅ QA Aprovado*
