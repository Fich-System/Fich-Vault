# EAV - Limite de Consumo de Combustível

**Issue:** [#86](https://github.com/Fich-System/Fich-Backend/issues/86)  
**PR:** [#96](https://github.com/Fich-System/Fich-Backend/pull/96)  
**Branch:** `feat/eav-86-limite-consumo-combustivel`  
**Migration:** V99  
**Status:** ✅ Merged

## Estrutura

| Entidade | Tabela |
|----------|--------|
| LimiteConsumoCombustivelConfiguracaoAba | `limite_consumo_configuracao_aba` |
| LimiteConsumoCombustivelConfiguracaoGrupo | `limite_consumo_configuracao_grupo` |
| LimiteConsumoCombustivelConfiguracaoCampo | `limite_consumo_configuracao_campo` |
| LimiteConsumoCombustivelValor | `limite_consumo_valores` |

## Pacotes

- **models:** `br.com.fich.backend.models.frota`
- **repository:** `br.com.fich.backend.repository.frota`
- **services:** `br.com.fich.backend.services.frota`
- **controllers:** `br.com.fich.backend.controllers.frota`

## Abas (4)

| Aba | Ícone | Ordem |
|-----|-------|-------|
| Limites | speed | 1 |
| Período | calendar_month | 2 |
| Vínculo | link | 3 |
| Observações | note | 4 |

## Grupos (4)

| Grupo | Aba |
|-------|-----|
| Limites de Consumo | Limites |
| Datas | Período |
| Associação | Vínculo |
| Notas | Observações |

## Campos (10)

| Campo | Tipo | Aba | Grupo |
|-------|------|-----|-------|
| Tipo de Limite | SELECT | Limites | Limites de Consumo |
| Limite Litros | DECIMAL | Limites | Limites de Consumo |
| Limite Valor (R$) | DECIMAL | Limites | Limites de Consumo |
| Limite Abastecimentos | NUMBER | Limites | Limites de Consumo |
| Ativo | BOOLEAN | Limites | Limites de Consumo |
| Data Início | DATE | Período | Datas |
| Data Fim | DATE | Período | Datas |
| Veículo | NUMBER | Vínculo | Associação |
| Motorista | NUMBER | Vínculo | Associação |
| Observação | TEXTAREA | Observações | Notas |

## Permissões

- `LIMITE_CONSUMO_COMBUSTIVEL_CREATE`
- `LIMITE_CONSUMO_COMBUSTIVEL_READ`
- `LIMITE_CONSUMO_COMBUSTIVEL_UPDATE`
- `LIMITE_CONSUMO_COMBUSTIVEL_DELETE`

## EntidadeHandler

- Classe: `LimiteConsumoCombustivelEntidadeHandler`
- `create/exclude` via gatilho: `UnsupportedOperationException` (consciente)
- `get/set` valor campo: implementado via `LimiteConsumoCombustivelValorService`

## Migração de Dados

Migração completa das colunas da tabela `limite_consumo_combustivel` para valores EAV:
- `tipo_limite` → Tipo de Limite
- `limite_litros` → Limite Litros
- `limite_valor` → Limite Valor (R$)
- `limite_abastecimentos` → Limite Abastecimentos
- `ativo` → Ativo
- `data_inicio` → Data Início
- `data_fim` → Data Fim
- `veiculo_id` → Veículo
- `funcionario_id` → Motorista
- `observacao` → Observação

## Frontend — Página de Configuração EAV

**Issue:** [#142](https://github.com/Fich-System/FICH-RETAGUARDA/issues/142)  
**PR:** [#161](https://github.com/Fich-System/FICH-RETAGUARDA/pull/161)  
**Branch:** `feat/eav-limite-consumo`  
**Status:** ✅ QA Aprovado

### Arquivos (7)

| Arquivo | Responsabilidade |
|---------|-----------------|
| `limite_consumo_eav_config_page.dart` | TabBar principal — Abas / Grupos / Campos |
| `limite_consumo_abas_page.dart` | Listagem CRUD de abas |
| `limite_consumo_aba_form_page.dart` | Formulário criar/editar aba |
| `limite_consumo_grupos_page.dart` | Listagem CRUD de grupos |
| `limite_consumo_grupo_form_page.dart` | Formulário criar/editar grupo |
| `limite_consumo_campos_page.dart` | Listagem CRUD de campos |
| `limite_consumo_campo_form_page.dart` | Formulário criar/editar campo |

### API

- `/api/configuracao-limite-consumo-combustivel/abas`
- `/api/configuracao-limite-consumo-combustivel/grupos`
- `/api/configuracao-limite-consumo-combustivel/campos`

### Rota

- `/configuracoes/configuracao-limite-consumo-combustivel` (adicionada em `main.dart`)

## Entidade Base

A entidade `LimiteConsumoCombustivel` existente continua sendo usada como entidade principal (com seus relacionamentos com `Veiculo` e `Funcionario`). Os dados configuráveis agora são gerenciados via EAV.
