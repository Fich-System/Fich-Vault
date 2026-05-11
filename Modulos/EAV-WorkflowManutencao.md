# EAV - Workflow de Manutenção

## Issues
- **Backend Issue:** #83
- **Backend PR:** (Grupo C backend — migration V96)
- **Frontend Issue:** #151
- **Frontend PR:** #169
- **Módulo:** manutencao
- **Status Backend:** ✅ Merged (Grupo C)
- **Status Frontend:** ✅ QA Aprovado

## Estrutura EAV

### Abas (WorkflowManutencaoConfiguracaoAba)

| Aba | Ordem | Ícone | Descrição |
|-----|-------|-------|-----------|
| Etapas | 1 | settings | Configuração das etapas do workflow |
| Regras | 2 | rule | Regras de transição entre etapas |
| Ações | 3 | play_arrow | Ações executadas em cada transição |

### Grupos (WorkflowManutencaoConfiguracaoGrupo)

| Grupo | Aba | Ordem |
|-------|-----|-------|
| Dados da Etapa | Etapas | 1 |
| Configurações | Etapas | 2 |
| Critérios | Regras | 1 |
| Condições | Regras | 2 |
| Execução | Ações | 1 |
| Notificações | Ações | 2 |

### Campos (WorkflowManutencaoConfiguracaoCampo)

| Campo | Tipo | Aba | Grupo | Obrigatório |
|-------|------|-----|-------|-------------|
| Nome da Etapa | TEXT | Etapas | Dados da Etapa | Sim |
| Descrição | TEXTAREA | Etapas | Dados da Etapa | Não |
| Ordem | NUMBER | Etapas | Dados da Etapa | Sim |
| Status Inicial | BOOLEAN | Etapas | Configurações | Não |
| Status Final | BOOLEAN | Etapas | Configurações | Não |
| Permite Retorno | BOOLEAN | Etapas | Configurações | Não |
| Etapa Origem | SELECT | Regras | Critérios | Sim |
| Etapa Destino | SELECT | Regras | Critérios | Sim |
| Condição | TEXT | Regras | Condições | Não |
| Tipo Ação | SELECT | Ações | Execução | Não |
| Parâmetros | TEXT | Ações | Execução | Não |
| Notificar Responsável | BOOLEAN | Ações | Notificações | Não |
| Template Notificação | TEXT | Ações | Notificações | Não |

## Permissões

| Código | Descrição |
|--------|-----------|
| WORKFLOW_MANUTENCAO_CREATE | Criar workflows |
| WORKFLOW_MANUTENCAO_READ | Visualizar workflows |
| WORKFLOW_MANUTENCAO_UPDATE | Atualizar workflows |
| WORKFLOW_MANUTENCAO_DELETE | Remover workflows |

## Arquivos

| Tipo | Path |
|------|------|
| Models | `models/manutencao/WorkflowManutencaoConfiguracaoAba.java` |
| | `models/manutencao/WorkflowManutencaoConfiguracaoGrupo.java` |
| | `models/manutencao/WorkflowManutencaoConfiguracaoCampo.java` |
| | `models/manutencao/WorkflowManutencaoValor.java` |
| Repositories | `repository/manutencao/WorkflowManutencaoConfiguracaoAbaRepository.java` |
| | `repository/manutencao/WorkflowManutencaoConfiguracaoGrupoRepository.java` |
| | `repository/manutencao/WorkflowManutencaoConfiguracaoCampoRepository.java` |
| | `repository/manutencao/WorkflowManutencaoValorRepository.java` |
| Services | `services/manutencao/WorkflowManutencaoConfiguracaoAbaService.java` |
| | `services/manutencao/WorkflowManutencaoConfiguracaoGrupoService.java` |
| | `services/manutencao/WorkflowManutencaoConfiguracaoCampoService.java` |
| | `services/manutencao/WorkflowManutencaoValorService.java` |
| | `services/manutencao/WorkflowManutencaoEntidadeHandler.java` |
| Controllers | `controllers/manutencao/WorkflowManutencaoConfiguracaoAbaController.java` |
| | `controllers/manutencao/WorkflowManutencaoConfiguracaoGrupoController.java` |
| | `controllers/manutencao/WorkflowManutencaoConfiguracaoCampoController.java` |
| | `controllers/manutencao/WorkflowManutencaoValorController.java` |
| Migration | `db/migration/V96__workflow_manutencao_configuracao_dinamica.sql` |

## Frontend (Flutter)

### Páginas EAV de Configuração

7 arquivos em `lib/pages/configuracoes/eav/`:
- `workflow_manutencao_eav_config_page.dart` — TabBar (Abas / Grupos / Campos)
- `workflow_manutencao_abas_page.dart` — CRUD de abas
- `workflow_manutencao_aba_form_page.dart` — Form criar/editar aba
- `workflow_manutencao_grupos_page.dart` — CRUD de grupos
- `workflow_manutencao_grupo_form_page.dart` — Form criar/editar grupo
- `workflow_manutencao_campos_page.dart` — CRUD de campos
- `workflow_manutencao_campo_form_page.dart` — Form criar/editar campo

### APIs consumidas
- `/api/configuracao-workflow-manutencao/abas`
- `/api/configuracao-workflow-manutencao/grupos`
- `/api/configuracao-workflow-manutencao/campos`

## Observações
- Entidade pai: `models/manutencao/WorkflowManutencao.java` (já existente)
- Referência FK: `workflow_manutencao_valores.workflow_id → workflow_manutencao.id`
- Migração V96 cria tabelas + estrutura padrão inicial
- Frontend PR #169 implementa página de configuração dinâmica para WorkflowManutencao
