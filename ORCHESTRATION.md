# ORCHESTRATION.md - Workflow da Equipe

## Papel do Jarvis (Orquestrador)

Toda demanda chega pelo Renan → Jarvis analisa → delega pra quem faz sentido → acompanha → consolida → entrega.

## Time

| Agente | ID | Especialidade | Quando delegar |
|--------|----|---------------|----------------|
| ⚡ **Jarvis** | `main` | Orquestrador | Tarefas simples, coordenação, resposta direta |
| 🔧 **Dev SR** | `dev-sr` | Arquitetura, código, code review | Features, refactors, bugs complexos, decisões técnicas |
| 🐛 **QA** | `qa` | Testes, qualidade, bug reports | Validar features, plans de teste, investigar bugs |
| 📝 **Doc** | `doc` | Documentação técnica, vault | Docs, ADRs, changelogs, organização do vault |

## Fluxo de demanda

```
Renan → Jarvis
           │
           ├── tarefa simples? → Jarvis resolve direto
           │
           ├── precisa codificar? → 🔧 Dev SR
           │       └── depois → 🐛 QA valida
           │
           ├── precisa testar? → 🐛 QA
           │
           ├── precisa documentar? → 📝 Doc
           │
           └── demanda complexa (cod + test + doc)?
                   ├── 🔧 Dev SR implementa
                   ├── 🐛 QA valida
                   └── 📝 Doc documenta
                   └── Jarvis consolida e entrega
```

## Como delegar

Usar `openclaw agent --agent <id> --message "<tarefa>" --json` via exec.

**Sempre incluir no prompt:**
- Contexto claro do que precisa ser feito
- Formato de saída esperado
- Se necessário, anexar arquivos/referências
- Prazo/quando precisa

## Template de delegação

```
Contexto: {breve resumo do que está acontecendo}

Tarefa: {o que precisa ser feito, detalhado}

Formato de saída esperado:
{como quero a resposta - texto, formato, etc}

Referências:
{links, arquivos, contexto adicional}
```

## 📝 Regra de documentação contínua

**Toda demanda — seja bugfix, feature, refactor ou melhoria — ao ser concluída, deve ser verificada pelo 📝 Doc para saber se a documentação no vault Obsidian precisa de atualização.**

### Gatilhos para revisão do Doc

| Situação | Ação do Doc |
|----------|-------------|
| Nova feature criada | Criar/atualizar notas dos módulos afetados, adicionar endpoints na [[Projetos/Fich-Backend/API-Endpoints]], documentar fluxos |
| Endpoint alterado | Atualizar [[Projetos/Fich-Backend/Modulos]] e [[Projetos/Fich-Backend/API-Endpoints]] |
| Novo módulo | Criar nota do módulo, adicionar na visão geral e na lista de módulos |
| Mudança de arquitetura | Atualizar [[Projetos/Fich-Backend/Arquitetura]] e, se relevante, criar ADR |
| Dependência alterada | Atualizar [[Projetos/Fich-Backend/Dependencias]] |
| Bug crítico ou mudança de fluxo | Atualizar [[Projetos/Fich-Backend/Fluxos]] se o comportamento mudou |
| CI/CD ou infra alterada | Atualizar [[Projetos/Fich-Backend/Infraestrutura]] |

### Fluxo padrão pós-demanda

```
Jarvis recebe demanda
  → delega pra quem resolve
  → recebe resultado
  → 📝 Doc: verifica se vault precisa de update?
       ├── Sim → delega atualização pro Doc
       └── Não → segue
  → entrega pro Renan
```

## Qualidade e validação

Antes de entregar pro Renan:
1. Todo código passou pelo 🔧 Dev SR?
2. Toda feature foi testada pelo 🐛 QA?
3. Documentação no vault revisada pelo 📝 Doc?
4. A resposta está clara e completa?
