# EAV - Competência Técnica

**Issue:** [#85](https://github.com/Fich-System/Fich-Backend/issues/85)  
**PR:** [#95](https://github.com/Fich-System/Fich-Backend/pull/95)  
**Branch:** `feat/eav-85-competencia-tecnica`  
**Migration:** V98  
**Status:** ✅ Merged

## Estrutura

| Entidade | Tabela |
|----------|--------|
| CompetenciaTecnicaConfiguracaoAba | `competencia_tecnica_configuracao_aba` |
| CompetenciaTecnicaConfiguracaoGrupo | `competencia_tecnica_configuracao_grupo` |
| CompetenciaTecnicaConfiguracaoCampo | `competencia_tecnica_configuracao_campo` |
| CompetenciaTecnicaValor | `competencia_tecnica_valores` |

## Pacotes

- **models:** `br.com.fich.backend.models.rh`
- **repository:** `br.com.fich.backend.repository.rh`
- **services:** `br.com.fich.backend.services.rh`
- **controllers:** `br.com.fich.backend.controllers.rh`

## Abas (5)

| Aba | Ícone | Ordem |
|-----|-------|-------|
| Identificação | badge | 1 |
| Avaliação | star | 2 |
| Níveis | trending_up | 3 |
| Desenvolvimento | school | 4 |
| Contexto | info | 5 |

## Grupos (10)

| Grupo | Aba |
|-------|-----|
| Dados Básicos | Identificação |
| Classificação | Identificação |
| Notas | Avaliação |
| Autoavaliação | Avaliação |
| Nível Atual | Níveis |
| Metas | Níveis |
| Treinamento | Desenvolvimento |
| Plano de Ação | Desenvolvimento |
| Referências | Contexto |
| Metodologia | Contexto |

## Campos (27)

| Campo | Tipo | Aba | Grupo |
|-------|------|-----|-------|
| Nome da Competência | TEXT | Identificação | Dados Básicos |
| Descrição | TEXTAREA | Identificação | Dados Básicos |
| Categoria | SELECT | Identificação | Classificação |
| Experiência (anos) | NUMBER | Identificação | Classificação |
| Experiência (meses) | NUMBER | Identificação | Classificação |
| Pontuação Atual | DECIMAL | Avaliação | Notas |
| Pontuação Máxima | DECIMAL | Avaliação | Notas |
| Data da Avaliação | DATETIME | Avaliação | Notas |
| Próxima Avaliação | DATETIME | Avaliação | Notas |
| Avaliador | TEXT | Avaliação | Notas |
| Autoavaliação (1-5) | DECIMAL | Avaliação | Autoavaliação |
| Avaliação Gestor (1-5) | DECIMAL | Avaliação | Autoavaliação |
| Avaliação Pares (1-5) | DECIMAL | Avaliação | Autoavaliação |
| Nível Atual | SELECT | Níveis | Nível Atual |
| Nível Desejado | SELECT | Níveis | Nível Atual |
| Nível Mínimo Função | SELECT | Níveis | Nível Atual |
| Meta Prazo | DATETIME | Níveis | Metas |
| Atingiu Meta | BOOLEAN | Níveis | Metas |
| Data Meta Atingida | DATETIME | Níveis | Metas |
| Crítica para Função | BOOLEAN | Níveis | Metas |
| Em Desenvolvimento | BOOLEAN | Desenvolvimento | Treinamento |
| Precisa Treinamento | BOOLEAN | Desenvolvimento | Treinamento |
| Precisa Certificação | BOOLEAN | Desenvolvimento | Treinamento |
| Plano Desenvolvimento | TEXTAREA | Desenvolvimento | Plano de Ação |
| Observações | TEXTAREA | Desenvolvimento | Plano de Ação |
| Evidências | TEXTAREA | Desenvolvimento | Plano de Ação |
| Funcionário | NUMBER | Contexto | Referências |
| Metodologia Avaliação | TEXTAREA | Contexto | Metodologia |

## Permissões

- `COMPETENCIA_TECNICA_CREATE`
- `COMPETENCIA_TECNICA_READ`
- `COMPETENCIA_TECNICA_UPDATE`
- `COMPETENCIA_TECNICA_DELETE`

## EntidadeHandler

- Classe: `CompetenciaTecnicaEntidadeHandler`
- `create/exclude` via gatilho: `UnsupportedOperationException` (consciente)
- `get/set` valor campo: implementado via `CompetenciaTecnicaValorService`

## Migração de Dados

Migração completa das colunas da tabela `competencia_tecnica` para valores EAV:
- `nome_competencia` → Nome da Competência
- `descricao` → Descrição
- `categoria` → Categoria
- `pontuacao_atual` → Pontuação Atual
- `pontuacao_maxima` → Pontuação Máxima
- `data_avaliacao` → Data da Avaliação
- `data_proxima_avaliacao` → Próxima Avaliação
- `avaliador` → Avaliador
- `autoavaliacao` → Autoavaliação (1-5)
- `avaliacao_gestor` → Avaliação Gestor (1-5)
- `avaliacao_pares` → Avaliação Pares (1-5)
- `nivel_atual` → Nível Atual
- `nivel_desejado` → Nível Desejado
- `nivel_minimo_funcao` → Nível Mínimo Função
- `meta_prazo` → Meta Prazo
- `atingiu_meta` → Atingiu Meta
- `data_meta_atingida` → Data Meta Atingida
- `critica_para_funcao` → Crítica para Função
- `em_desenvolvimento` → Em Desenvolvimento
- `precisa_treinamento` → Precisa Treinamento
- `precisa_certificacao` → Precisa Certificação
- `plano_desenvolvimento` → Plano Desenvolvimento
- `observacoes` → Observações
- `evidencias` → Evidências
- `funcionario_id` → Funcionário
- `metodologia_avaliacao` → Metodologia Avaliação
- `experiencia_anos` → Experiência (anos)
- `experiencia_meses` → Experiência (meses)

## Frontend (Flutter — Fich-Retaguarda)

**Issue:** [#136](https://github.com/Fich-System/FICH-RETAGUARDA/issues/136)
**PR:** [#156](https://github.com/Fich-System/FICH-RETAGUARDA/pull/156)
**Branch:** `feat/eav-competencia-tecnica`
**Status:** ✅ QA Aprovado (PR aberto)

### Páginas (7 arquivos)

| Arquivo | Tipo |
|---------|------|
| `competencia_tecnica_eav_config_page.dart` | Página principal com abas |
| `competencia_tecnica_abas_page.dart` | Listagem de abas |
| `competencia_tecnica_aba_form_page.dart` | Formulário de aba |
| `competencia_tecnica_grupos_page.dart` | Listagem de grupos |
| `competencia_tecnica_grupo_form_page.dart` | Formulário de grupo |
| `competencia_tecnica_campos_page.dart` | Listagem de campos |
| `competencia_tecnica_campo_form_page.dart` | Formulário de campo |

### APIs

| Endpoint | Método |
|----------|--------|
| `/api/configuracao-competencia-tecnica/abas` | CRUD |
| `/api/configuracao-competencia-tecnica/grupos` | CRUD |
| `/api/configuracao-competencia-tecnica/campos` | CRUD |

### Rota

- `/configuracoes/competencia-tecnica-eav`

### Alterações em arquivos existentes

- `lib/main.dart` — Registro da rota
- `lib/models/menu_item.dart` — Item de menu
- `lib/utils/navigation_helper.dart` — Navegação
