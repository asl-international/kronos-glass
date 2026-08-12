# STATUS — Instituto Kronos · Painel

> **Fonte da verdade.** Atualizado a cada sprint. Canônico deployado: **v0.17 Glass** em `painel-kronos.asli.international`.

---

## ✅ v0.17 — Mobile + Hash routing + Add manual fix (07-12/08/2026)

**Contexto**: Marcelo reclamou que o mobile tava ruim (sem nav, sem voltar, sem busca) e não conseguia adicionar item manualmente.

**O que mudou**:
- **Mobile polish**: nav-burger (☰), drawer lateral com áreas, breadcrumb "← Voltar", CSS @media 1100px/700px
- **Hash routing**: `location.hash` muda conforme navega (`#/produtos/workshop`), `parseHashAndNavigate` no boot
- **Add manual fix**: bug do `saveAddEdit` (chave aninhada errada) + `bindItemActions` (passava `currentSubScope` como `parentId`) + `collectAllItems` (não incluía items custom do STATE) + cleanup legacy no `loadState`
- **Cards UNDEFINED** corrigidos: items no INITIAL_DATA agora têm `type` e `nome`
- **Modal Resumo** com CSS `.show` aceito
- **Botão "atualizado..."** removido da home

**Validação**:
- 0 erros de console (exceto favicon 404)
- 28/28 URLs no Resumo
- Mobile iPhone 14 Pro: tudo funciona
- Add manual: 4/4 items em Produtos > Workshop

**Doc**: `docs/decisoes/v0.17-add-manual-fix.md` (a criar)

---

## ✅ v0.15 — Custom domain + Home limpa (28-29/07/2026)

**Contexto**: Marcelo queria domínio `painel-kronos.asli.international` em vez do `kronos-glass.vercel.app`.

**O que mudou**:
- **Domínio custom** configurado via Vercel API (CNAME `painel-kronos.asli.international` → `cname.vercel-dns.com`)
- **SSL** automático via Vercel (Let's Encrypt)
- **Token Vercel novo**: o anterior `ZfH4g0MQu9LZpuMUfWszu4zb` expirou em 28/07; novo: `vcp_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX` (substituído por placeholder — pedir token real no AGENT_DOCS local)
- **Home sem "X de Y preenchidos"** — só o lead + atualizado
- **Bullets hierárquicos** no Resumo (`//` > `○` > `·`)

**Validação**:
- HTTP 200 em `painel-kronos.asli.international`
- Server: Vercel, X-Vercel-Cache: HIT
- 0 erros no console

**Doc**: `docs/decisoes/v0.15-custom-domain.md` (a criar)

---

## ✅ v0.14 — Glass canônico + 28 URLs + Resumo + TOC (28/07/2026)

**Contexto**: Marcelo escolheu Glass entre 5 layouts. Precisava dos 28 links da lista dele plugados.

**O que mudou**:
- **28 URLs** finais plugadas no `INITIAL_DATA` com `type` e `nome` próprios
- **Cards de items** com tipo correto (link/sheet/doc)
- **Botão Resumo** com hierarquia clean, busca, copy, download .md
- **TOC lateral** (`≡` à esquerda) com hierarquia 3 níveis
- **Filtro** por tipo funcional
- **Vazios escondidos** por padrão
- **Botão "mostrar vazios"** removido

**Validação**:
- 28/28 URLs no Resumo (testado via puppeteer)
- Sem "UNDEFINED" em nenhum card

---

## ✅ v0.13 — 5 Layouts full HTML (17/07/2026)

**Contexto**: Marcelo pediu "5 layouts full pra comparar" depois da escolha inicial de C (Craft minimal) ter resultado em algo que ele não gostou.

**O que mudou**:
- **5 layouts full** (`layouts/full-*.html`, ~85KB cada) com painel COMPLETO
- **5 repos** no GitHub: `kronos-{bento,editorial,dense,glass,notion}`
- **5 Vercel URLs ativas** com SSL
- **Glass escolhido** pelo Marcelo em 17/07

**Validação**:
- Todos: 0 erros, 200 OK
- Comparativo visual em `artifacts/compare-layout-*.png`

---

## ✅ v0.12 — Layout C + Docs locais + Resumo (16/07/2026)

**Contexto**: reclamação "não gostei do quadrado cinza" + "todos os links na nuvem" + "revise tudo".

**O que mudou**:
- **Layout C (Craft minimal)** — texto puro, divisores, sem card bg
- **8 docs locais adicionados**
- **Botão Resumo** no topnav
- **6 atas de reunião** NÃO incluídas (histórico → Sheets)

**Validação**: 0 erros no console. 0 "undefined" em 17 escopos.

---

## ✅ v0.10-teste — Busca extensiva (15/07/2026 tarde)

**Contexto**: reclamação "busca não pegou 'presencial' → Eventos Presenciais".

**O que mudou**:
- **Stemmer em PT** (plural/gerúndio/passado)
- **200+ sinônimos do domínio** (`mentorado=aluno`, `kairos=kairós`, etc)
- **Indexação de títulos sintéticos**
- **Navegação por teclado** (Enter, ↑/↓, Esc)

**Validação (10 queries)**: presencial, evento, Kairos, time, margem, venda, aluno, criativ, roas, "assinatu" (typo) — todas OK.

---

## ✅ v0.9-teste — Notes como cards colapsáveis (13/07/2026 noite)

**Contexto**: "nessa aba vai ficar tudo aberto e com a informação jogada".

**O que mudou**:
- **Notes viraram CARDS COLAPSÁVEIS** (fechado por padrão)
- **5 notes novas** (Time, Sinais alerta, Régua saúde, Ferramentas, Metas workshop)

---

## ✅ v0.8-teste — 10 mudanças da reunião 11/07 (13/07/2026 tarde)

**Contexto**: transcrição 89KB filtrada pra 23KB de sinal puro. Marcelo pediu "tudo que puder, sem perguntar".

**O que mudou** (10 itens): seletor projeto ativo, Sobre modal, Track record, Origem leads, Aplicação só evento, Migração Asaas, Financeiro 2 níveis, Workshops debrief, Banner rosa, Footer.

---

## ✅ v0.6 — Canônico LEGADO (12/07/2026 noite)

**Status**: superseded pelo Glass v0.13+. Arquivo original `index.html` antes do Glass.

**O que mudou**: modal centralizado, backdrop blur, pills de tipo, atalhos, pulse rosa.

---

## 🚧 Pendente

**3 docs que Marcelo precisa subir Drive**:
- `roteiro_ja_vende_v3.docx`
- `roteiro_sessao_nao_vende_v3.docx`
- `produtos_kairos.docx` (NOVA, 20/07) — substitui `1D2PB3m`?

**Confirmações**:
- Contrato Kairós — mantém `1q_0e-iJt` ou tem versão mais nova?
- Desativar `kronos-glass.vercel.app` legado? (recomendo sim)

**90+ items vazios** esperando URLs (Gestão 10, CS 7, Produto 6, Tráfego 7, Financeiro 5, RH 4, Kairós 7, SOPs 9, Biblioteca 10, Conhecimento 10).

**Mobile polish**:
- Botão de busca 🔍 no mobile (search ainda escondida no header mobile)

**Backlog ALTA** (de `docs/03-ROADMAP.md`):
- Embelezamento por IA
- Tags livres nos items
- Drag-and-drop pra reordenar
- Export/Import do localStorage
- Tela cheia pra leitura de notas longas

**Backlog MÉDIA**:
- Tema light alternativo
- Métricas de origens em planilha + dashboard
- Track record: levantar cases existentes
- Workshops debrief: template + piloto
- ManyChat reconfigurar

**Backlog BAIXA**:
- Backend sync (Supabase)
- Permissões por papel
- Multi-projeto com STATE separado

Detalhes em `docs/03-ROADMAP.md` e `docs/decisoes/`.
