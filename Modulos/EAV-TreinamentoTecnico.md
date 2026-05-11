# EAV - Treinamento Técnico

## Issues
- **Backend Issue:** #90
- **Backend PR:** #100
- **Frontend Issue:** #149
- **Frontend PR:** #167
- **Módulo:** rh
- **Status Backend:** ✅ Merged
- **Status Frontend:** ✅ QA Aprovado

## Estrutura EAV

### Abas (TreinamentoTecnicoConfiguracaoAba)

| Aba | Ordem | Ícone | Descrição |
|-----|-------|-------|-----------|
| Identificação | 1 | school | Dados do treinamento |
| Detalhes | 2 | description | Conteúdo, requisitos e custo |
| Datas | 3 | event | Período e status |
| Contexto | 4 | info | Referências e observações |

### Grupos (TreinamentoTecnicoConfiguracaoGrupo)

| Grupo | Aba | Ordem |
|-------|-----|-------|
| Dados Básicos | Identificação | 1 |
| Classificação | Identificação | 2 |
| Conteúdo | Detalhes | 1 |
| Custo e Vagas | Detalhes | 2 |
| Período | Datas | 1 |
| Status e Validade | Datas | 2 |
| Referências | Contexto | 1 |
| Observações | Contexto | 2 |

### Campos (TreinamentoTecnicoConfiguracaoCampo)

| Campo | Tipo | Aba | Grupo | Obrigatório |
|-------|------|-----|-------|-------------|
| Título | TEXT | Identificação | Dados Básicos | Sim |
| Descrição | TEXTAREA | Identificação | Dados Básicos | Não |
| Instrutor | TEXT | Identificação | Dados Básicos | Sim |
| Local | TEXT | Identificação | Dados Básicos | Não |
| Tipo | SELECT | Identificação | Classificação | Sim |
| Modalidade | SELECT | Identificação | Classificação | Sim |
| Obrigatório | BOOLEAN | Identificação | Classificação | Não |
| Objetivos | TEXTAREA | Detalhes | Conteúdo | Não |
| Conteúdo Programático | TEXTAREA | Detalhes | Conteúdo | Não |
| Pré-Requisitos | TEXTAREA | Detalhes | Conteúdo | Não |
| Método Avaliação | TEXT | Detalhes | Conteúdo | Não |
| Nota Mínima | DECIMAL | Detalhes | Conteúdo | Não |
| Custo Total | DECIMAL | Detalhes | Custo e Vagas | Não |
| Custo por Participante | DECIMAL | Detalhes | Custo e Vagas | Não |
| Vagas Disponíveis | NUMBER | Detalhes | Custo e Vagas | Não |
| Vagas Ocupadas | NUMBER | Detalhes | Custo e Vagas | Não |
| Material Fornecido | TEXTAREA | Detalhes | Custo e Vagas | Não |
| Data Início | DATETIME | Datas | Período | Sim |
| Data Fim | DATETIME | Datas | Período | Sim |
| Carga Horária | NUMBER | Datas | Período | Sim |
| Status | SELECT | Datas | Status e Validade | Sim |
| Validez (meses) | NUMBER | Datas | Status e Validade | Não |
| Requer Certificação | BOOLEAN | Datas | Status e Validade | Não |
| Aprovado Por | TEXT | Datas | Status e Validade | Não |
| Data Aprovação | DATETIME | Datas | Status e Validade | Não |
| URL Material Online | TEXT | Contexto | Referências | Não |
| Observações | TEXTAREA | Contexto | Observações | Não |

## Permissões

| Código | Descrição |
|--------|-----------|
| TREINAMENTO_TECNICO_CREATE | Criar treinamentos |
| TREINAMENTO_TECNICO_READ | Visualizar treinamentos |
| TREINAMENTO_TECNICO_UPDATE | Atualizar treinamentos |
| TREINAMENTO_TECNICO_DELETE | Remover treinamentos |

## Arquivos

| Tipo | Path |
|------|------|
| Models | `models/rh/TreinamentoTecnicoConfiguracaoAba.java` |
| | `models/rh/TreinamentoTecnicoConfiguracaoGrupo.java` |
| | `models/rh/TreinamentoTecnicoConfiguracaoCampo.java` |
| | `models/rh/TreinamentoTecnicoValor.java` |
| Repositories | `repository/rh/TreinamentoTecnicoConfiguracaoAbaRepository.java` |
| | `repository/rh/TreinamentoTecnicoConfiguracaoGrupoRepository.java` |
| | `repository/rh/TreinamentoTecnicoConfiguracaoCampoRepository.java` |
| | `repository/rh/TreinamentoTecnicoValorRepository.java` |
| Services | `services/rh/TreinamentoTecnicoConfiguracaoAbaService.java` |
| | `services/rh/TreinamentoTecnicoConfiguracaoGrupoService.java` |
| | `services/rh/TreinamentoTecnicoConfiguracaoCampoService.java` |
| | `services/rh/TreinamentoTecnicoValorService.java` |
| | `services/rh/TreinamentoTecnicoEntidadeHandler.java` |
| Controllers | `controllers/rh/TreinamentoTecnicoConfiguracaoAbaController.java` |
| | `controllers/rh/TreinamentoTecnicoConfiguracaoGrupoController.java` |
| | `controllers/rh/TreinamentoTecnicoConfiguracaoCampoController.java` |
| | `controllers/rh/TreinamentoTecnicoValorController.java` |
| Migration | `db/migration/V103__treinamento_tecnico_configuracao_dinamica.sql` |

## Frontend (Flutter)

### Páginas EAV de Configuração

7 arquivos em `lib/pages/configuracoes/eav/`:
- `treinamento_tecnico_eav_config_page.dart` — TabBar (Abas / Grupos / Campos)
- `treinamento_tecnico_abas_page.dart` — CRUD de abas
- `treinamento_tecnico_aba_form_page.dart` — Form criar/editar aba
- `treinamento_tecnico_grupos_page.dart` — CRUD de grupos
- `treinamento_tecnico_grupo_form_page.dart` — Form criar/editar grupo
- `treinamento_tecnico_campos_page.dart` — CRUD de campos
- `treinamento_tecnico_campo_form_page.dart` — Form criar/editar campo

### APIs consumidas
- `/api/configuracao-treinamento-tecnico/abas`
- `/api/configuracao-treinamento-tecnico/grupos`
- `/api/configuracao-treinamento-tecnico/campos`

## Observações
- Entidade pai: `models/pessoa/TreinamentoTecnico.java` (já existente)
- Referência FK: `treinamento_tecnico_valores.treinamento_id → treinamento_tecnico.id`
- Migração V103 cria tabelas + estrutura padrão inicial
- Frontend PR #167 implementa página de configuração dinâmica para TreinamentoTecnico
