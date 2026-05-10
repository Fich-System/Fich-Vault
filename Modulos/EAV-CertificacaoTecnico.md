# EAV - Certificação Técnico

## Issue
- **Issue:** #89
- **PR:** #99
- **Módulo:** rh
- **Status:** ✅ Merged

## Estrutura EAV

### Abas (CertificacaoTecnicoConfiguracaoAba)

| Aba | Ordem | Ícone | Descrição |
|-----|-------|-------|-----------|
| Identificação | 1 | badge | Dados da certificação |
| Detalhes | 2 | description | Nota, custo e renovação |
| Validade | 3 | event | Datas e renovação |
| Contexto | 4 | info | Referências e observações |

### Grupos (CertificacaoTecnicoConfiguracaoGrupo)

| Grupo | Aba | Ordem |
|-------|-----|-------|
| Dados Básicos | Identificação | 1 |
| Classificação | Identificação | 2 |
| Notas | Detalhes | 1 |
| Custo | Detalhes | 2 |
| Datas | Validade | 1 |
| Renovação | Validade | 2 |
| Referências | Contexto | 1 |
| Observações | Contexto | 2 |

### Campos (CertificacaoTecnicoConfiguracaoCampo)

| Campo | Tipo | Aba | Grupo | Obrigatório |
|-------|------|-----|-------|-------------|
| Nome da Certificação | TEXT | Identificação | Dados Básicos | Sim |
| Código | TEXT | Identificação | Dados Básicos | Não |
| Órgão Emissor | TEXT | Identificação | Dados Básicos | Sim |
| Número Registro | TEXT | Identificação | Dados Básicos | Não |
| Tipo | SELECT | Identificação | Classificação | Sim |
| Obrigatória | BOOLEAN | Identificação | Classificação | Não |
| Nível Dificuldade | SELECT | Identificação | Classificação | Não |
| Nota Obtida | DECIMAL | Detalhes | Notas | Não |
| Nota Mínima | DECIMAL | Detalhes | Notas | Não |
| Custo | DECIMAL | Detalhes | Custo | Não |
| Carga Horária | NUMBER | Detalhes | Custo | Não |
| Data Emissão | DATETIME | Validade | Datas | Sim |
| Data Validade | DATETIME | Validade | Datas | Não |
| Status | SELECT | Validade | Datas | Sim |
| Requer Renovação | BOOLEAN | Validade | Renovação | Não |
| Prazo Renovação (meses) | NUMBER | Validade | Renovação | Não |
| Data Renovação | DATETIME | Validade | Renovação | Não |
| Funcionário | NUMBER | Contexto | Referências | Sim |
| Local Realização | TEXT | Contexto | Referências | Não |
| Instrutor | TEXT | Contexto | Referências | Não |
| URL Certificado | TEXT | Contexto | Referências | Não |
| Observações | TEXTAREA | Contexto | Observações | Não |
| Competências Adquiridas | TEXTAREA | Contexto | Observações | Não |

## Permissões

| Código | Descrição |
|--------|-----------|
| CERTIFICACAO_TECNICO_CREATE | Criar certificações |
| CERTIFICACAO_TECNICO_READ | Visualizar certificações |
| CERTIFICACAO_TECNICO_UPDATE | Atualizar certificações |
| CERTIFICACAO_TECNICO_DELETE | Remover certificações |

## Arquivos

| Tipo | Path |
|------|------|
| Models | `models/rh/CertificacaoTecnicoConfiguracaoAba.java` |
| | `models/rh/CertificacaoTecnicoConfiguracaoGrupo.java` |
| | `models/rh/CertificacaoTecnicoConfiguracaoCampo.java` |
| | `models/rh/CertificacaoTecnicoValor.java` |
| Repositories | `repository/rh/CertificacaoTecnicoConfiguracaoAbaRepository.java` |
| | `repository/rh/CertificacaoTecnicoConfiguracaoGrupoRepository.java` |
| | `repository/rh/CertificacaoTecnicoConfiguracaoCampoRepository.java` |
| | `repository/rh/CertificacaoTecnicoValorRepository.java` |
| Services | `services/rh/CertificacaoTecnicoConfiguracaoAbaService.java` |
| | `services/rh/CertificacaoTecnicoConfiguracaoGrupoService.java` |
| | `services/rh/CertificacaoTecnicoConfiguracaoCampoService.java` |
| | `services/rh/CertificacaoTecnicoValorService.java` |
| | `services/rh/CertificacaoTecnicoEntidadeHandler.java` |
| Controllers | `controllers/rh/CertificacaoTecnicoConfiguracaoAbaController.java` |
| | `controllers/rh/CertificacaoTecnicoConfiguracaoGrupoController.java` |
| | `controllers/rh/CertificacaoTecnicoConfiguracaoCampoController.java` |
| | `controllers/rh/CertificacaoTecnicoValorController.java` |
| Migration | `db/migration/V102__certificacao_tecnico_configuracao_dinamica.sql` |

## Observações
- Entidade pai: `models/pessoa/CertificacaoTecnico.java` (já existente)
- Referência FK: `certificacao_tecnico_valores.certificacao_id → certificacao_tecnico.id`
- Migração V102 cria tabelas + estrutura padrão inicial
