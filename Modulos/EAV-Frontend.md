# EAV Frontend — FICH-RETAGUARDA (Flutter)

Módulo de configuração dinâmica de entidades no frontend Flutter. Permite criar abas, grupos e campos customizáveis para cada entidade do sistema.

## Arquitetura

Cada entidade EAV implementa **7 arquivos** no diretório `lib/pages/configuracoes/eav/`:

| Arquivo | Responsabilidade |
|---------|-----------------|
| `{entidade}_eav_config_page.dart` | **TabBar principal** — Abas / Grupos / Campos |
| `{entidade}_abas_page.dart` | Listagem CRUD de abas (com paginação) |
| `{entidade}_aba_form_page.dart` | Formulário criar/editar aba |
| `{entidade}_grupos_page.dart` | Listagem CRUD de grupos |
| `{entidade}_grupo_form_page.dart` | Formulário criar/editar grupo |
| `{entidade}_campos_page.dart` | Listagem CRUD de campos |
| `{entidade}_campo_form_page.dart` | Formulário criar/editar campo |

### Componentes Reutilizáveis

- **`lib/components/eav/eav_helpers.dart`** — Funções utilitárias compartilhadas (formatadores, validações, constantes)

### APIs Consumidas

Cada entidade expõe 3 endpoints REST no backend:

```
/api/configuracao-{entidade}/abas     → CRUD de abas
/api/configuracao-{entidade}/grupos   → CRUD de grupos
/api/configuracao-{entidade}/campos   → CRUD de campos
```

## Padrão de Código

### Widgets Base

| Widget | Uso |
|--------|-----|
| `BaseLayout` | Layout padrão com título, breadcrumb e ações |
| `PaginationSection` | Paginação de listas (page, size, total) |
| `ApiService` | Chamadas HTTP centralizadas |

### Fluxo da TabBar Principal

```dart
// Exemplo: PlanoContasEavConfigPage
class PlanoContasEavConfigPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return BaseLayout(
      title: 'Plano de Contas — Configuração',
      child: DefaultTabController(
        length: 3,
        child: Column(
          children: [
            TabBar(tabs: [
              Tab(text: 'Abas'),
              Tab(text: 'Grupos'),
              Tab(text: 'Campos'),
            ]),
            Expanded(
              child: TabBarView(children: [
                PlanoContasAbasPage(),
                PlanoContasGruposPage(),
                PlanoContasCamposPage(),
              ]),
            ),
          ],
        ),
      ),
    );
  }
}
```

### Fluxo de Criação/Edição

1. **Listagem** → Botão "Nova Aba" / "Novo Grupo" / "Novo Campo"
2. **Form Page** → Coleta dados, valida, chama `ApiService.post()` ou `.put()`
3. **Retorno** → Pop com resultado, listagem faz refresh

## Entidades Implementadas — Grupo A ✅

| # | Entidade | Branch | PR | Status |
|---|----------|--------|-----|--------|
| #84 | PlanoContas | feat/eav-plano-contas | #106 | ✅ Concluído |
| #83 | Fornecedor | feat/eav-fornecedor | #107 | ✅ Concluído |
| #82 | Funcionario | feat/eav-funcionario | #108 | ✅ Concluído |
| #81 | Grupo | feat/eav-grupo | #109 | ✅ Concluído |
| #80 | Cliente | feat/eav-cliente | #110 | ✅ Concluído |
| #79 | CentroDeCusto | feat/eav-centro-custo | #111 | ✅ Concluído |

### Estrutura de Arquivos no Projeto

```
lib/pages/configuracoes/eav/
├── eav_helpers.dart
├── centro_de_custo_abas_page.dart
├── centro_de_custo_aba_form_page.dart
├── centro_de_custo_grupos_page.dart
├── centro_de_custo_grupo_form_page.dart
├── centro_de_custo_campos_page.dart
├── centro_de_custo_campo_form_page.dart
├── centro_de_custo_eav_config_page.dart
├── cliente_abas_page.dart
├── cliente_aba_form_page.dart
├── cliente_grupos_page.dart
├── cliente_grupo_form_page.dart
├── cliente_campos_page.dart
├── cliente_campo_form_page.dart
├── cliente_eav_config_page.dart
├── grupo_abas_page.dart
├── grupo_aba_form_page.dart
├── grupo_grupos_page.dart
├── grupo_grupo_form_page.dart
├── grupo_campos_page.dart
├── grupo_campo_form_page.dart
├── grupo_eav_config_page.dart
├── funcionario_abas_page.dart
├── funcionario_aba_form_page.dart
├── funcionario_grupos_page.dart
├── funcionario_grupo_form_page.dart
├── funcionario_campos_page.dart
├── funcionario_campo_form_page.dart
├── funcionario_eav_config_page.dart
├── fornecedor_abas_page.dart
├── fornecedor_aba_form_page.dart
├── fornecedor_grupos_page.dart
├── fornecedor_grupo_form_page.dart
├── fornecedor_campos_page.dart
├── fornecedor_campo_form_page.dart
├── fornecedor_eav_config_page.dart
├── plano_contas_abas_page.dart
├── plano_contas_aba_form_page.dart
├── plano_contas_grupos_page.dart
├── plano_contas_grupo_form_page.dart
├── plano_contas_campos_page.dart
├── plano_contas_campo_form_page.dart
└── plano_contas_eav_config_page.dart
```

**Total: 43 arquivos** (42 páginas + 1 helper)

## Como Adicionar uma Nova Entidade

### Template (Copy-Paste)

Para adicionar uma nova entidade EAV no frontend, siga este passo a passo:

1. **Copie os 7 arquivos** de uma entidade existente (ex: `Cliente`)
2. **Renomeie**:
   - Arquivos: `cliente_` → `{nova_entidade}_`
   - Classes: `Cliente` → `{NovaEntidade}`
3. **Ajuste os endpoints** da API:
   - `/api/configuracao-cliente/abas` → `/api/configuracao-{nova_entidade}/abas`
   - Idem para `/grupos` e `/campos`
4. **Ajuste a rota** no arquivo de rotas do app
5. **Registre no menu** de configurações

### Checklist por Entidade

- [ ] `{entidade}_eav_config_page.dart` — TabBar com 3 tabs
- [ ] `{entidade}_abas_page.dart` — Listagem com paginação + botão "Nova Aba"
- [ ] `{entidade}_aba_form_page.dart` — Form com validação (nome)
- [ ] `{entidade}_grupos_page.dart` — Listagem com paginação + botão "Novo Grupo"
- [ ] `{entidade}_grupo_form_page.dart` — Form com validação (nome)
- [ ] `{entidade}_campos_page.dart` — Listagem com paginação + botão "Novo Campo"
- [ ] `{entidade}_campo_form_page.dart` — Form com validação (nome, tipo, aba, grupo)

### Convenções de Nomenclatura

| Convenção | Exemplo |
|-----------|---------|
| Nome da entidade | `plano_contas` (snake_case nos arquivos) |
| Classe Dart | `PlanoContas` (PascalCase) |
| Endpoint API | `/api/configuracao-plano-contas` (kebab-case) |
| Rota | `/configuracoes/eav/plano-contas` |

## Próximos Passos

- [x] **Grupo B** — 17 entidades (média prioridade) ✅
- [x] **Grupo C** — 4 entidades (baixa prioridade) — ✅ 4/4 CONCLUÍDO (#92 NotaFiscalServico, #91 Servico, #90 RegraTributacao, #89 SubGrupo)
- [ ] **Grupo D** — Backend EAV (10 entidades) — 🟢 1/10 concluído
- [ ] Testes de integração das páginas
- [ ] Validação de permissões por entidade

---

## Entidades Implementadas — Grupo B ✅ CONCLUÍDO

| # | Entidade | Branch | PR | Status |
|---|----------|--------|-----|--------|
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

**Grupo B: 17/17 = 100% concluído**

### Estrutura de Arquivos no Projeto (Grupo B adicionado)

```
lib/pages/configuracoes/eav/
├── eav_helpers.dart
├── ... (Grupo A — 43 arquivos) ...
├── sinistro_abas_page.dart
├── sinistro_aba_form_page.dart
├── sinistro_grupos_page.dart
├── sinistro_grupo_form_page.dart
├── sinistro_campos_page.dart
├── sinistro_campo_form_page.dart
├── sinistro_eav_config_page.dart
├── checklist_manutencao_abas_page.dart
├── checklist_manutencao_aba_form_page.dart
├── checklist_manutencao_grupos_page.dart
├── checklist_manutencao_grupo_form_page.dart
├── checklist_manutencao_campos_page.dart
├── checklist_manutencao_campo_form_page.dart
├── checklist_manutencao_eav_config_page.dart
├── troca_abas_page.dart
├── troca_aba_form_page.dart
├── troca_grupos_page.dart
├── troca_grupo_form_page.dart
├── troca_campos_page.dart
├── troca_campo_form_page.dart
├── troca_eav_config_page.dart
├── certificacao_abas_page.dart
├── certificacao_aba_form_page.dart
├── certificacao_grupos_page.dart
├── certificacao_grupo_form_page.dart
├── certificacao_campos_page.dart
├── certificacao_campo_form_page.dart
├── certificacao_eav_config_page.dart
├── ordem_servico_abas_page.dart
├── ordem_servico_aba_form_page.dart
├── ordem_servico_grupos_page.dart
├── ordem_servico_grupo_form_page.dart
├── ordem_servico_campos_page.dart
├── ordem_servico_campo_form_page.dart
├── ordem_servico_eav_config_page.dart
├── pneu_abas_page.dart
├── pneu_aba_form_page.dart
├── pneu_grupos_page.dart
├── pneu_grupo_form_page.dart
├── pneu_campos_page.dart
├── pneu_campo_form_page.dart
├── pneu_eav_config_page.dart
├── rodizio_abas_page.dart
├── rodizio_aba_form_page.dart
├── rodizio_grupos_page.dart
├── rodizio_grupo_form_page.dart
├── rodizio_campos_page.dart
├── rodizio_campo_form_page.dart
├── rodizio_eav_config_page.dart
├── multa_abas_page.dart
├── multa_aba_form_page.dart
├── multa_grupos_page.dart
├── multa_grupo_form_page.dart
├── multa_campos_page.dart
├── multa_campo_form_page.dart
├── multa_eav_config_page.dart
├── estoque_abas_page.dart
├── estoque_aba_form_page.dart
├── estoque_grupos_page.dart
├── estoque_grupo_form_page.dart
├── estoque_campos_page.dart
├── estoque_campo_form_page.dart
├── estoque_eav_config_page.dart
├── nfe_entrada_abas_page.dart
├── nfe_entrada_aba_form_page.dart
├── nfe_entrada_grupos_page.dart
├── nfe_entrada_grupo_form_page.dart
├── nfe_entrada_campos_page.dart
├── nfe_entrada_campo_form_page.dart
├── nfe_entrada_eav_config_page.dart
├── manutencao_abas_page.dart
├── manutencao_aba_form_page.dart
├── manutencao_grupos_page.dart
├── manutencao_grupo_form_page.dart
├── manutencao_campos_page.dart
├── manutencao_campo_form_page.dart
├── manutencao_eav_config_page.dart
├── abastecimento_abas_page.dart
├── abastecimento_aba_form_page.dart
├── abastecimento_grupos_page.dart
├── abastecimento_grupo_form_page.dart
├── abastecimento_campos_page.dart
├── abastecimento_campo_form_page.dart
├── abastecimento_eav_config_page.dart
├── checklist_veiculos_abas_page.dart
├── checklist_veiculos_aba_form_page.dart
├── checklist_veiculos_grupos_page.dart
├── checklist_veiculos_grupo_form_page.dart
├── checklist_veiculos_campos_page.dart
├── checklist_veiculos_campo_form_page.dart
├── checklist_veiculos_eav_config_page.dart
├── transferencia_bancaria_abas_page.dart
├── transferencia_bancaria_aba_form_page.dart
├── transferencia_bancaria_grupos_page.dart
├── transferencia_bancaria_grupo_form_page.dart
├── transferencia_bancaria_campos_page.dart
├── transferencia_bancaria_campo_form_page.dart
├── transferencia_bancaria_eav_config_page.dart
├── movimentacao_bancaria_abas_page.dart
├── movimentacao_bancaria_aba_form_page.dart
├── movimentacao_bancaria_grupos_page.dart
├── movimentacao_bancaria_grupo_form_page.dart
├── movimentacao_bancaria_campos_page.dart
├── movimentacao_bancaria_campo_form_page.dart
├── movimentacao_bancaria_eav_config_page.dart
├── inventario_abas_page.dart
├── inventario_aba_form_page.dart
├── inventario_grupos_page.dart
├── inventario_grupo_form_page.dart
├── inventario_campos_page.dart
├── inventario_campo_form_page.dart
└── inventario_eav_config_page.dart
├── movimentacao_estoque_abas_page.dart
├── movimentacao_estoque_aba_form_page.dart
├── movimentacao_estoque_grupos_page.dart
├── movimentacao_estoque_grupo_form_page.dart
├── movimentacao_estoque_campos_page.dart
├── movimentacao_estoque_campo_form_page.dart
└── movimentacao_estoque_eav_config_page.dart
```

**Total: 204 arquivos** (43 do Grupo A + 119 do Grupo B (17×7) + 28 do Grupo C (4×7: NotaFiscalServico, Servico, RegraTributacao, SubGrupo) + 7 do Grupo D (1×7: AlertaManutencao) + 1 helper eav_helpers.dart + 6 helpers/componentes)

## Entidades Implementadas — Grupo C ✅ CONCLUÍDO (4/4)

| # | Entidade | Branch | PR | Status |
|---|----------|--------|-----|--------|
| #92 | NotaFiscalServico | feat/eav-notafiscal-servico | #129 | ✅ Concluído |
| #91 | Servico | feat/eav-servico | #130 | ✅ Concluído |
| #90 | RegraTributacao | feat/eav-regra-tributacao | #131 | ✅ Concluído |
| #89 | SubGrupo | feat/eav-subgrupo | #132 | ✅ Concluído |

**Grupo C: 4/4 = 100% concluído**

### Estrutura de Arquivos no Projeto (Grupo C adicionado)

```
lib/pages/configuracoes/eav/
├── ... (Grupos A e B) ...
├── notafiscal_servico_abas_page.dart
├── notafiscal_servico_aba_form_page.dart
├── notafiscal_servico_grupos_page.dart
├── notafiscal_servico_grupo_form_page.dart
├── notafiscal_servico_campos_page.dart
├── notafiscal_servico_campo_form_page.dart
└── notafiscal_servico_eav_config_page.dart
├── servico_abas_page.dart
├── servico_aba_form_page.dart
├── servico_grupos_page.dart
├── servico_grupo_form_page.dart
├── servico_campos_page.dart
├── servico_campo_form_page.dart
└── servico_eav_config_page.dart
├── regra_tributacao_abas_page.dart
├── regra_tributacao_aba_form_page.dart
├── regra_tributacao_grupos_page.dart
├── regra_tributacao_grupo_form_page.dart
├── regra_tributacao_campos_page.dart
├── regra_tributacao_campo_form_page.dart
└── regra_tributacao_eav_config_page.dart
├── subgrupo_abas_page.dart
├── subgrupo_aba_form_page.dart
├── subgrupo_grupos_page.dart
├── subgrupo_grupo_form_page.dart
├── subgrupo_campos_page.dart
├── subgrupo_campo_form_page.dart
└── subgrupo_eav_config_page.dart
```

## Entidades Implementadas — Grupo D 🟢 Em Progresso (1/10)

| # | Entidade | Branch | PR | Status |
|---|----------|--------|-----|--------|
| #133 | AlertaManutencao | feat/eav-alerta-manutencao | #153 | ✅ Concluído |

**Grupo D: 1/10 — Backend EAV migrations (V94–V103)**

### Estrutura de Arquivos no Projeto (Grupo D adicionado)

```
lib/pages/configuracoes/eav/
├── ... (Grupos A, B e C) ...
├── alerta_manutencao_abas_page.dart
├── alerta_manutencao_aba_form_page.dart
├── alerta_manutencao_grupos_page.dart
├── alerta_manutencao_grupo_form_page.dart
├── alerta_manutencao_campos_page.dart
├── alerta_manutencao_campo_form_page.dart
└── alerta_manutencao_eav_config_page.dart
```

---

*Última atualização: 2026-05-10 — Projeto EAV Frontend expandido! Grupos A–C completos (27/27) + Grupo D Backend EAV iniciado (1/10: AlertaManutencao PR #153 ✅)*
