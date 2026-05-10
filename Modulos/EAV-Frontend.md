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

- [ ] **Grupo B** — 17 entidades (média prioridade)
- [ ] **Grupo C** — 4 entidades (baixa prioridade)
- [ ] Testes de integração das páginas
- [ ] Validação de permissões por entidade

---

*Última atualização: 2026-05-10 — Grupo A concluído (6/27 entidades)*
