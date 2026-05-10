# EAV - Avaliação de Produto

**Issue:** [#87](https://github.com/Fich-System/Fich-Backend/issues/87)  
**PR:** [#97](https://github.com/Fich-System/Fich-Backend/pull/97)  
**Branch:** `feat/eav-87-produto-avaliacao`  
**Migration:** V100  
**Status:** ✅ Merged

## Estrutura

| Entidade | Tabela |
|----------|--------|
| ProdutoAvaliacaoConfiguracaoAba | `produto_avaliacao_configuracao_aba` |
| ProdutoAvaliacaoConfiguracaoGrupo | `produto_avaliacao_configuracao_grupo` |
| ProdutoAvaliacaoConfiguracaoCampo | `produto_avaliacao_configuracao_campo` |
| ProdutoAvaliacaoValor | `produto_avaliacao_valores` |

## Pacotes

- **models:** `br.com.fich.backend.models.produto`
- **repository:** `br.com.fich.backend.repository.produto`
- **services:** `br.com.fich.backend.services.produto`
- **controllers:** `br.com.fich.backend.controllers.produto`

## Abas (3)

| Aba | Ícone | Ordem |
|-----|-------|-------|
| Dados da Avaliação | star | 1 |
| Informações do Cliente | person | 2 |
| Produto e Compra | shopping_cart | 3 |

## Grupos (5)

| Grupo | Aba |
|-------|-----|
| Dados Básicos | Dados da Avaliação |
| Moderação e Resposta | Dados da Avaliação |
| Dados do Avaliador | Informações do Cliente |
| Referências do Produto | Produto e Compra |
| Dados da Compra | Produto e Compra |

## Campos (14)

| Campo | Tipo | Aba | Grupo |
|-------|------|-----|-------|
| Nota | NUMBER | Dados da Avaliação | Dados Básicos |
| Título | TEXT | Dados da Avaliação | Dados Básicos |
| Comentário | TEXTAREA | Dados da Avaliação | Dados Básicos |
| Recomenda | BOOLEAN | Dados da Avaliação | Dados Básicos |
| Status | SELECT | Dados da Avaliação | Dados Básicos |
| Resposta da Loja | TEXTAREA | Dados da Avaliação | Moderação e Resposta |
| Data da Resposta | DATETIME | Dados da Avaliação | Moderação e Resposta |
| Usuário Resposta | TEXT | Dados da Avaliação | Moderação e Resposta |
| Nome do Avaliador | TEXT | Informações do Cliente | Dados do Avaliador |
| Email do Avaliador | TEXT | Informações do Cliente | Dados do Avaliador |
| Imagens | TEXTAREA | Informações do Cliente | Dados do Avaliador |
| Produto | NUMBER | Produto e Compra | Referências do Produto |
| Variação do Produto | NUMBER | Produto e Compra | Referências do Produto |
| Compra Verificada | BOOLEAN | Produto e Compra | Dados da Compra |
| Data da Compra | DATETIME | Produto e Compra | Dados da Compra |
| Likes | NUMBER | Produto e Compra | Dados da Compra |
| Dislikes | NUMBER | Produto e Compra | Dados da Compra |

## Permissões

- `PRODUTO_AVALIACAO_CREATE`
- `PRODUTO_AVALIACAO_READ`
- `PRODUTO_AVALIACAO_UPDATE`
- `PRODUTO_AVALIACAO_DELETE`

## EntidadeHandler

- Classe: `ProdutoAvaliacaoEntidadeHandler`
- `create/exclude` via gatilho: `UnsupportedOperationException` (consciente)
- `get/set` valor campo: implementado via `ProdutoAvaliacaoValorService`

## Entidade Base

A entidade `ProdutoAvaliacao` existente continua sendo usada como entidade principal (com seus relacionamentos com `Produto` e `ProdutoVariacao`). Os dados configuráveis agora são gerenciados via EAV.
