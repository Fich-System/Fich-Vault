# EAV - Benefício de Funcionário

**Issue:** [#88](https://github.com/Fich-System/Fich-Backend/issues/88)  
**PR:** [#98](https://github.com/Fich-System/Fich-Backend/pull/98)  
**Branch:** `feat/eav-88-funcionario-beneficio`  
**Migration:** V101  
**Status:** ✅ Merged

## Estrutura

| Entidade | Tabela |
|----------|--------|
| FuncionarioBeneficioConfiguracaoAba | `funcionario_beneficio_configuracao_aba` |
| FuncionarioBeneficioConfiguracaoGrupo | `funcionario_beneficio_configuracao_grupo` |
| FuncionarioBeneficioConfiguracaoCampo | `funcionario_beneficio_configuracao_campo` |
| FuncionarioBeneficioValor | `funcionario_beneficio_valores` |

## Pacotes

- **models:** `br.com.fich.backend.models.pessoa`
- **repository:** `br.com.fich.backend.repository.pessoa`
- **services:** `br.com.fich.backend.services.pessoa`
- **controllers:** `br.com.fich.backend.controllers.pessoa`

## Abas (3)

| Aba | Ícone | Ordem |
|-----|-------|-------|
| Dados do Benefício | card_giftcard | 1 |
| Funcionário e Valores | person | 2 |
| Vigência | calendar_today | 3 |

## Grupos (5)

| Grupo | Aba |
|-------|-----|
| Dados Básicos | Dados do Benefício |
| Valores | Funcionário e Valores |
| Referência ao Funcionário | Funcionário e Valores |
| Datas do Benefício | Vigência |
| Observações | Vigência |

## Campos (11)

| Campo | Tipo | Aba | Grupo |
|-------|------|-----|-------|
| Tipo de Benefício | SELECT | Dados do Benefício | Dados Básicos |
| Descrição | TEXTAREA | Dados do Benefício | Dados Básicos |
| Ativo | BOOLEAN | Dados do Benefício | Dados Básicos |
| Valor | DECIMAL | Funcionário e Valores | Valores |
| Percentual | DECIMAL | Funcionário e Valores | Valores |
| Funcionário | NUMBER | Funcionário e Valores | Referência ao Funcionário |
| Data de Início | DATE | Vigência | Datas do Benefício |
| Data de Término | DATE | Vigência | Datas do Benefício |
| Data de Concessão | DATETIME | Vigência | Datas do Benefício |
| Observações | TEXTAREA | Vigência | Observações |
| Motivo | TEXTAREA | Vigência | Observações |

## Permissões

- `FUNCIONARIO_BENEFICIO_CREATE`
- `FUNCIONARIO_BENEFICIO_READ`
- `FUNCIONARIO_BENEFICIO_UPDATE`
- `FUNCIONARIO_BENEFICIO_DELETE`

## EntidadeHandler

- Classe: `FuncionarioBeneficioEntidadeHandler`
- `create/exclude` via gatilho: `UnsupportedOperationException` (consciente)
- `get/set` valor campo: implementado via `FuncionarioBeneficioValorService`

## Entidade Base

A entidade `FuncionarioBeneficio` existente continua sendo usada como entidade principal (com seu relacionamento com `Funcionario`). Os dados configuráveis agora são gerenciados via EAV. Foi adicionado o campo `empresaId` à entidade para suporte a validação multi-tenant no ValorService.
