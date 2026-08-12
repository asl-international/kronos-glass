# AGENT_DOCS — Regras de Manutenção da Documentação

> Mavis (eu) sigo estas regras toda vez que trabalho na documentação do Instituto Kronos. Se você (Marcelo) ver algo errado aqui, me corrija.

---

## 📜 Regra de ouro: documentação é viva

> **"Arquivos da verdade" não são fonte da verdade. A fonte da verdade é o código rodando + o STATUS.md atualizado."**

Cada sprint, **antes de implementar**, eu:
1. Leio `docs/04-STATUS.md` (fonte da verdade)
2. Releio o que tá no `docs/02-CHANGELOG.md` (última versão)
3. Releio o `docs/03-ROADMAP.md` (sprint atual)

**Depois de implementar**, eu:
1. Atualizo `docs/04-STATUS.md` (estado atual mudou)
2. Adiciono entrada no `docs/02-CHANGELOG.md` (versão nova)
3. Movo a sprint pra "concluídos" no `docs/03-ROADMAP.md`
4. Crio nota de decisão em `docs/decisoes/v0.X-*.md` se for decisão importante
5. Salvo contexto no scratchpad

---

## 📁 Estrutura padrão (GitHub `kronos-glass/docs/`)

```
docs/
├── README.md                    ← entry point (visão geral, stack, URL)
├── 00-CHECKPOINT-CURRENT.md     ← snapshot completo (estado atual)
├── 02-CHANGELOG.md              ← log de mudanças por versão
├── 03-ROADMAP.md                ← sprints pendentes (backlog)
├── 04-STATUS.md                 ← FONTE DA VERDADE do estado atual
├── 05-AGENT_DOCS.md             ← este arquivo (regras de manutenção)
├── 06-ARQUITETURA.md             ← arquitetura técnica (stack, dados, funções)
├── 07-FUNCIONALIDADES.md         ← features em detalhe (UX, componentes)
├── 08-DECISOES-DESIGN.md         ← decisões de design (por que X, não Y)
├── 09-LINKS.md                  ← links pré-configurados (INITIAL_DATA)
├── 10-CONTEXTO-NEGOCIO.md       ← contexto do Instituto Kronos
└── decisoes/                    ← notas de decisão por versão
    ├── 00-indice.md             ← índice cronológico
    ├── reuniao-11-07-painel.md  ← reunião fundacional
    ├── v0.8-reuniao-11-07.md
    ├── v0.9-notes-colapsaveis.md
    ├── v0.10-busca-extensiva.md
    ├── v0.11-escopo-reorganizado.md
    ├── v0.13-glass-canônico.md
    ├── v0.15-custom-domain.md
    ├── v0.16-mobile-hash.md
    └── v0.17-add-manual-fix.md
```

**Numeração** (00-10): mantém ordem de leitura lógica (visão → estado → regras → arquitetura → features → design → dados → contexto). Os docs `decisoes/` não são numerados — são entries cronológicas.

---

## 🔄 Quando o que atualizar

| Quando | O que mexer |
|---|---|
| Sprint nova começa | Adicionar linha em `docs/03-ROADMAP.md` (prioridade certa) + atualizar "sprint atual" em `docs/04-STATUS.md` |
| Sprint termina (v0.X) | (1) Adicionar entrada em `docs/02-CHANGELOG.md` (2) Mover sprint pra "CONCLUÍDOS" no `docs/03-ROADMAP.md` (3) Atualizar "Sprint v0.X" no `docs/04-STATUS.md` (4) Criar nota de decisão em `docs/decisoes/v0.X-*.md` se for decisão nova importante |
| Bug achado em produção | Adicionar na seção "Sprint v0.X" do `docs/04-STATUS.md` (não criar versão nova a não ser que o fix seja deploy) |
| Conversa importante com Marcelo | Criar nota de decisão em `docs/decisoes/reuniao-*.md` (não atualizar STATUS pra coisas de processo) |
| Decisão de longo prazo | Adicionar em `docs/03-ROADMAP.md` (prioridade ALTA/MÉDIA/BAIXA) + referenciar no `docs/04-STATUS.md` "❌ Pendente (v2+)" |
| Mudança de arquitetura | Atualizar `docs/06-ARQUITETURA.md` + referenciar no `docs/04-STATUS.md` "Stack" |
| Feature nova | Adicionar em `docs/07-FUNCIONALIDADES.md` (com print se possível) |
| Decisão "por que X, não Y" | Adicionar em `docs/08-DECISOES-DESIGN.md` (com data e contexto) |
| Link novo (planilha, doc) | Adicionar em `docs/09-LINKS.md` |

---

## ✍️ Padrão de escrita

### Markdown

- **Headers**: `##` e `###` (não abuse de `#`)
- **Listas**: use `-` (não `*`)
- **Bold**: use `**` (não `__`)
- **Code**: `` ` `` pra inline, ` ``` ` pra bloco
- **Tabelas**: use `|` quando for escaneável
- **Emojis**: use com moderação (status, tipos, alertas)

### Tom

- **Direto**: sem rodeios, sem floreios
- **Técnico quando precisa**: jargão é OK, mas explique quando ambíguo
- **Pessoal quando útil**: "você", "eu" — não "o usuário" ou "desenvolvedor"
- **Decisões com data**: "decisão 11/07/2026" — pra rastreabilidade

### Comprimento

- README: ~500-800 palavras
- STATUS: ~1500-3000 palavras (atualizado a cada sprint)
- ROADMAP: ~500-1000 palavras
- Cada `decisoes/*.md`: ~200-800 palavras
- **Máximo por doc**: 3000 palavras. Se passar, divide.

---

## 🗑 Política de archive

> **Nunca deletar docs.** Mover pra `docs/archive/` com data.

Quando uma versão fica obsoleta:
1. Mover pra `docs/archive/v0.5-FUNCIONALIDADES-2026-07-12.md` (com data)
2. Adicionar link em `docs/archive/README.md` (índice)
3. Atualizar `docs/09-LINKS.md` se o doc tinha links pra outros docs

---

## 🔍 Padrão de "fonte da verdade"

Pra cada decisão importante, **uma** fonte da verdade:

| Decisão | Fonte |
|---|---|
| Estado atual do projeto | `docs/04-STATUS.md` |
| Versão deployada | `docs/02-CHANGELOG.md` (última entrada) |
| Estrutura de pastas | `docs/README.md` |
| Stack técnico | `docs/README.md` + `docs/06-ARQUITETURA.md` |
| Sprints pendentes | `docs/03-ROADMAP.md` |
| Por que X, não Y | `docs/08-DECISOES-DESIGN.md` |
| Links pré-configurados | `docs/09-LINKS.md` |
| Contexto do Instituto | `docs/10-CONTEXTO-NEGOCIO.md` |
| Decisão específica de sprint | `docs/decisoes/v0.X-*.md` |

**Nunca** espalhar a mesma decisão em 3 docs diferentes. Aponta pro doc de fonte.

---

## 💾 Backup

- `localStorage` (chave `kronos_state_v1`) tem o estado runtime
- Backup manual: console → `copy(localStorage.getItem('kronos_state_v1'))`
- Backup automático: não tem (localStorage é single-device)
- **Não confiar em** `localStorage` pra longo prazo — Sincronização com backend é sprint v2+

---

## 🎯 Quando perguntar pro Marcelo vs decidir sozinho

| Perguntar | Decidir sozinho |
|---|---|
| Decisão de design grande (layout, modelo de dados) | Bug fix óbvio |
| Decisão de produto (escopo, prioridade) | Mudança de código interna |
| Decisão de longo prazo (v2+, features) | Mudança de UX secundária |
| Mudança em dados existentes (migração, schema) | Refactor que não muda comportamento |
| Decisão que afeta outros painéis (ESL, FSL, Kairós) | Sprint que está no ROADMAP como priorizada |
| | Mudança em notas/docs pré-populados (se não foi pedido pra não mexer) |

**Regra geral**: se dá pra reverter facilmente e não afeta dados, decide. Se não dá pra reverter, pergunta.

---

## 🤖 Quando invocar o "user" (você, Marcelo)

- Para **conectar** (login em serviços externos, OAuth)
- Para **executar** ações no seu nome (deploy, Git push, delete de projeto, etc)
- Para **clicar** botões em interfaces externas (Vercel, GitHub, etc)
- Para **pagar** ou acessar billing

**Nunca** peço credenciais. **Sempre** espero OK antes de qualquer ação irreversível.

---

## 📞 Pedidos explícitos seus

| Seu pedido | Resposta automática |
|---|---|
| "Não melhore nada sem me autorizar" | Só faço o que você pediu. Se vejo bug, pergunto antes. |
| "Faça sem perguntar" | Quando objetivo é claro. Reporto o que fiz. |
| "Divida em partes" | Tarefas viram `todowrite` explícito (PARTE 1, PARTE 2, ...). |
| "Teste tudo" | Playwright + prints comparativos. |
| "Manda prints" | Imagens em `<media />` na resposta. |
| "Revise tudo" | Releio todos os docs + listo o que falta. |
| "Reformule absolutamente" | Reescrevo do zero, mantendo o que faz sentido. |
| "Não jogado, sem cores demais" | Hierarquia minimalista, sem subdivisões, mono h3, bullets ▫. |
| "Suba tudo no GitHub" | Subo via API REST preservando o que já existe no repo. |

---

## 🚀 Deploy workflow

1. Editar `C:\Users\bueno\Documents\Kronos\layouts\full-glass.html`
2. Push pro GitHub via API:
   ```bash
   gh api repos/asl-international/kronos-glass/contents/index.html -X PUT \
     -f message="Add files via upload" \
     -f branch=main \
     -f sha=<sha_anterior> \
     -F content=@<base64>
   ```
3. Vercel auto-deploya em ~30s
4. Validar via puppeteer em https://painel-kronos.asli.international/

**Token Vercel atual**: `vcp_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX` (substituído por placeholder — pedir token real ao Marcelo)
**Token GitHub**: `gho_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX` (substituído por placeholder — pedir token real ao Marcelo)

> Última atualização: 2026-08-12 por Mavis (revisão completa pós custom domain + mobile + hash routing)
