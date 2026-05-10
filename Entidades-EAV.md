# Entidades EAV

Lista de todas as entidades migradas para o padrão EAV (Entity-Attribute-Value).

| # | Entidade | Issue | PR | Migration | Status | Módulo |
|---|----------|-------|-----|-----------|--------|--------|
| 1 | Ocorrencia | #81 | #91 | V94 | ✅ | frota |
| 2 | AlertaManutencao | #82 | #92 | V95 | ✅ | frota |
| 3 | WorkflowManutencao | #83 | #93 | V96 | ✅ | frota |
| 4 | AvaliacaoFornecedor | #84 | (merged) | V97 | ✅ | pessoa |
| 5 | CompetenciaTecnica | #85 | #95 | V98 | ✅ | rh |
| 6 | LimiteConsumoCombustivel | #86 | #96 | V99 | ✅ | frota |
| 7 | ProdutoAvaliacao | #87 | #97 | V100 | ✅ | produto |
| 8 | FuncionarioBeneficio | #88 | #98 | V101 | ✅ | pessoa |
| 9 | CertificacaoTecnico | #89 | #99 | V102 | ✅ | rh |
| 10 | TreinamentoTecnico | #90 | #100 | V103 | ✅ | rh |

## Padrão de Arquivos (por entidade)

Cada entidade EAV gera:
- **4 models:** ConfiguracaoAba, ConfiguracaoGrupo, ConfiguracaoCampo, Valor
- **4 repositories:** repositórios JPA com queries otimizadas
- **5 services:** AbaService, GrupoService, CampoService, ValorService, EntidadeHandler
- **4 controllers:** REST controllers com @PreAuthorize
- **1 migration:** Flyway SQL
- **Enum:** TipoEntidadeDinamica + CodigoPermissao
