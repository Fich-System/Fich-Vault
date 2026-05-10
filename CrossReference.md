# Cross-Reference

Referência cruzada entre entidades, módulos e artefatos.

## Módulo → Pacote

| Módulo | Pacote Models | Pacote Services | Pacote Controllers |
|--------|---------------|-----------------|-------------------|
| frota | `models.frota` | `services.frota` | `controllers.frota` |
| pessoa | `models.pessoa` | `services.pessoa` | `controllers.pessoa` |
| rh | `models.rh` | `services.rh` | `controllers.rh` |
| financeiro | `models.*` | `modules.financeiro.services` | `controllers.*` |

## Migration → Entidade

| Migration | Entidade EAV |
|-----------|-------------|
| V94 | Ocorrencia |
| V95 | AlertaManutencao |
| V96 | WorkflowManutencao |
| V97 | AvaliacaoFornecedor |
| V98 | CompetenciaTecnica |
| V99 | LimiteConsumoCombustivel |
| V100 | ProdutoAvaliacao |
| V101 | FuncionarioBeneficio |
| V102 | CertificacaoTecnico |
| V103 | TreinamentoTecnico |

## Permissão → Entidade

| Permissão | Entidade |
|-----------|----------|
| OCORRENCIA_* | Ocorrencia |
| ALERTA_MANUTENCAO_* | AlertaManutencao |
| WORKFLOW_MANUTENCAO_* | WorkflowManutencao |
| AVALIACAO_FORNECEDOR_* | AvaliacaoFornecedor (via CodigoPermissao pendente) |
| COMPETENCIA_TECNICA_* | CompetenciaTecnica |
| LIMITE_CONSUMO_COMBUSTIVEL_* | LimiteConsumoCombustivel |
| PRODUTO_AVALIACAO_* | ProdutoAvaliacao |
| FUNCIONARIO_BENEFICIO_* | FuncionarioBeneficio |
| CERTIFICACAO_TECNICO_* | CertificacaoTecnico |
| TREINAMENTO_TECNICO_* | TreinamentoTecnico |

## EntidadeHandler → TipoEntidadeDinamica

| Handler | TipoEntidadeDinamica |
|---------|---------------------|
| OcorrenciaEntidadeHandler | OCORRENCIA |
| AlertaManutencaoEntidadeHandler | ALERTA_MANUTENCAO |
| WorkflowManutencaoEntidadeHandler | WORKFLOW_MANUTENCAO |
| AvaliacaoFornecedorEntidadeHandler | AVALIACAO_FORNECEDOR |
| CompetenciaTecnicaEntidadeHandler | COMPETENCIA_TECNICA |
| LimiteConsumoCombustivelEntidadeHandler | LIMITE_CONSUMO_COMBUSTIVEL |
| ProdutoAvaliacaoEntidadeHandler | PRODUTO_AVALIACAO |
| FuncionarioBeneficioEntidadeHandler | FUNCIONARIO_BENEFICIO |
| CertificacaoTecnicoEntidadeHandler | CERTIFICACAO_TECNICO |
| TreinamentoTecnicoEntidadeHandler | TREINAMENTO_TECNICO |
| LimiteConsumoCombustivelEntidadeHandler | LIMITE_CONSUMO_COMBUSTIVEL |
| ProdutoAvaliacaoEntidadeHandler | PRODUTO_AVALIACAO |
| FuncionarioBeneficioEntidadeHandler | FUNCIONARIO_BENEFICIO |
