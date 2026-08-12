# Changelog — Instituto Kronos · Painel

> Log de mudanças por versão. Cada versão lista: data, mudanças concretas, e o que foi validado.
> Versão canônica deployada: **v0.17** (Glass, custom domain `painel-kronos.asli.international`)
> Formato: `[v0.X]` + data + resumo + lista de mudanças

---

## v0.17 — 07-12/08/2026 — Mobile + Hash routing + Add manual fix

**Status**: deployado
**Arquivo**: `C:\Users\bueno\Documents\Kronos\layouts\full-glass.html`
**URL**: https://painel-kronos.asli.international/

### O que mudou
1. **Mobile (v0.16)** — nav-burger, drawer lateral, breadcrumb "← Voltar"
2. **Hash routing** — `location.hash` reflete onde está, deep link compartilhável
3. **Add manual de items** — bug do `saveAddEdit` corrigido (chave flat com ponto)
4. **Cleanup automático** de STATE legacy no `loadState` (chaves aninhadas)
5. **Cards "UNDEFINED"** corrigidos (todos os items agora têm `type` e `nome`)
6. **Modal Resumo** — CSS `.show` aceito (antes só `.open`)
7. **Vazios escondidos** por padrão (`showEmpty=false`)
8. **Botão "atualizado..."** removido da home

### Validação
- 28/28 URLs no Resumo (testado puppeteer)
- Mobile iPhone 14 Pro (393x852): TOC, Resumo, Comercial, add OK
- Add manual: `STATE['produtos.workshop']` cresce, item aparece na lista
- 0 erros de console (exceto favicon 404)

---

## v0.15 — 28-29/07/2026 — Custom domain + Home limpa

**Status**: deployado
**Arquivo**: `layouts/full-glass.html`
**URL**: https://painel-kronos.asli.international/

### O que mudou
1. **Domínio custom** `painel-kronos.asli.international` configurado na Vercel
2. **Home sem "X de Y preenchidos"** no lead e no meta
3. **Bullets hierárquicos** no Resumo (`// área > ○ sub > · item`)
4. **Merge automático** no `loadState` (localStorage legacy + INITIAL_DATA novo)
5. **Token Vercel novo** (o anterior expirou em 28/07)

### Validação
- HTTP 200 em `painel-kronos.asli.international`
- Server: Vercel, X-Vercel-Cache: HIT
- SSL válido (Let's Encrypt via Vercel)
- 28/28 links no Resumo

---

## v0.14 — 28/07/2026 — Glass canônico + 28 URLs + Resumo + TOC

**Status**: deployado
**Arquivo**: `layouts/full-glass.html`
**URL**: https://kronos-glass.vercel.app

### O que mudou
1. **28 URLs finais** plugadas no `INITIAL_DATA` (lista completa do Marcelo)
2. **Cards de items** com `type` e `nome` próprios (não mais "UNDEFINED")
3. **Botão Resumo** com hierarquia clean, busca, copy, download .md
4. **TOC lateral** (`≡` à esquerda, opacity 0.35→1 on hover) com hierarquia 3 níveis
5. **Filtro de items** por tipo (Todos / Notas / Links / Planilhas / Documentos)
6. **Sem botões de debug** no Resumo ("X vazios" removido, vazios escondidos)
7. **Botão "mostrar vazios"** removido

### Validação
- 28/28 URLs no Resumo (script validador rodado)
- Cada item com `type` correto (link/sheet/doc)
- Cards exibem nome, URL, tipo
- TOC lateral abre/fecha com X ou ESC

---

## v0.13 — 16-17/07/2026 — 5 Layouts full HTML

**Status**: 5 deploys completos
**Arquivos**: `layouts/full-{bento,editorial,dense,glass,notion}.html`

### O que mudou
1. **5 layouts full** (~85KB cada) com painel COMPLETO (não só a home de Gestão)
2. **Cada um com ESTRUTURA + INITIAL_DATA + PLAYBOOK + STATE** persistido no localStorage
3. **5 repos no GitHub**: `kronos-{bento,editorial,dense,glass,notion}`
4. **5 Vercel URLs ativas** (lista abaixo)
5. **Comparativo visual** (prints em `artifacts/compare-layout-*.png`)

| Layout | URL | Conceito |
|---|---|---|
| Bento | https://kronos-bento.vercel.app | Apple/Linear |
| Editorial | https://kronos-editorial.vercel.app | Stripe Press / Medium |
| Dense | https://kronos-dense.vercel.app | Admin / power-user |
| **Glass** (escolhido) | https://kronos-glass.vercel.app | Frosted glass + glow |
| Notion | https://kronos-notion.vercel.app | Sidebar persistente |

### Validação
- Todos: 0 erros no console, 200 OK
- Glass escolhido pelo Marcelo em 17/07

---

## v0.12 — 16/07/2026 — Layout C + Docs locais + Resumo

**Status**: superseded por v0.13 (foi layout C só na home)
**Arquivo**: `index-teste.html`

### O que mudou
1. **Layout C (Craft minimal)** — texto puro, divisores, sem card bg, max-width 1200px
2. **Drag handle `⋮⋮` só no hover**
3. **8 docs locais adicionados**: Contrato Kairós, Avatar, Produtos/Negociações, Onboarding v2, Roteiros (3), Briefing Conteúdo, Relatório Pesquisa
4. **Botão Resumo** no topnav
5. **6 atas de reunião** NÃO incluídas (histórico → Sheets)

### Validação
- 0 erros no console (Playwright)
- 0 "undefined" / 0 "[object Object]" / 0 "NaN" em 17 escopos

---

## v0.11-teste — 15/07/2026 (tarde) — Escopo reorganizado

**Status**: superseded
**Doc de decisão**: `docs/decisoes/v0.11-escopo-reorganizado.md`

### O que mudou
1. **Header de resumo no topo de cada escopo**: "X notas · Y links · Z planilhas · W vazios"
2. **Filtro por tipo** (pills): Todos / Notas / Links / Planilhas / Documentos
3. **Agrupamento visual por tipo**: NOTAS, LINKS, PLANILHAS, DOCS, OUTROS, VAZIOS
4. **Vazios escondidos por padrão** (toggle "Mostrar vazios")
5. **Cards de items** reformulados: ícone de tipo colorido

---

## v0.10-teste — 15/07/2026 (tarde) — Busca extensiva

**Status**: validado
**Doc de decisão**: `docs/decisoes/v0.10-busca-extensiva.md`

### O que mudou
1. **Stemmer em PT** — `presenciais`→`presenci`, `opções`→`opcao`, gerúndio, plurais
2. **200+ sinônimos do domínio** — `mentorado=aluno=cliente`, `zapi=wpp=whatsapp`, `kairos=kairós=mentoria`
3. **Indexação de títulos de áreas/produtos** — "presencial" → "Eventos Presenciais"
4. **Navegação por teclado** — Enter (vai), ↑/↓ (navega), Esc (fecha)

### Validação (10 queries)
"presencial"→Eventos Presenciais ✓ · "evento"→Eventos ✓ · "Kairos"→Mentoria Kairós ✓ · "time"→Time ✓ · "margem"→Fase 1 Margem ✓ · "venda"→Metas workshop ✓ · "aluno"→Régua de saúde ✓ · "criativ"→Criativos ✓ · "roas"→Fase 3 Crescimento ✓ · "assinatu" (typo!)→Fase 0 ✓

---

## v0.9-teste — 13/07/2026 (noite) — Notes como cards colapsáveis

**Status**: validado
**Doc de decisão**: `docs/decisoes/v0.9-notes-colapsaveis.md`

### O que mudou
1. **Notes viraram CARDS COLAPSÁVEIS** — fechado por padrão
2. **Click no card** → expande (chevron vira rosa)
3. **Toolbar "Expandir/Colapsar todas"** em escopos com 2+ notes
4. **5 notes novas** baseadas no `10-CONTEXTO-NEGOCIO.md`

---

## v0.8-teste — 13/07/2026 (tarde) — 10 mudanças da reunião 11/07

**Status**: validado
**Doc de decisão**: `docs/decisoes/v0.8-reuniao-11-07.md`

### O que mudou
1. **Header: seletor "Projeto ativo"** — cosmético em v0.8
2. **Botão "Sobre esta estrutura"** → modal centralizado
3. **Gestão > Track record** pré-populado com template
4. **Comercial > Captação > "Origem dos leads"** (note)
5. **Comercial > "Aplicação (só evento)"** (sub-seção nova)
6. **Comercial > Checkouts > Migração Asaas** (3,99% + R$ 0,50, boleto/PIX R$ 1,99)
7. **Operação > Financeiro > "Financeiro 2 níveis"** (note)
8. **Conhecimento > "Workshops — comparecimento, retenção, conversão"** (note)
9. **Banner rosa de padrão de sub-área** (dashboard/planejamento/processos/execução)
10. **Footer** com versão

---

## v0.7-teste — 13/07/2026 (manhã) — Superseded (v0.8 absorveu)

### O que mudou
1. Track record adicionado em `ESTRUTURA.gestao.items`
2. Comercial > Checkouts renomeado + URLs marcadas com "(Zouti)"
3. Comercial > Checkouts > "Migração pra Asaas" (sub-item note)

---

## v0.6 — 12/07/2026 (noite) — Canônico (LEGADO)

**Status**: superseded pelo Glass v0.13+
**Arquivo original**: `index.html` (legado, antes do Glass)

### O que mudou
1. Modal centralizado pra Adicionar/Editar (substitui form inline)
2. Backdrop com blur(8px)
3. Pills clicáveis pra tipo
4. Atalho ESC + Enter
5. Item aparece com pulse rosa + scrollIntoView ao adicionar

### Validação
- Gestão 0/10, Operação 9/52, Produtos 8/15, SOPs 1/9, Biblioteca 2/10, Conhecimento 0/10
- 0 erros no console

---

## v0.1 a v0.5 — Resumo cronológico

- **v0.1** (12/07 manhã) — Esqueleto: 4 camadas + Produtos + SOPs, sidebar + cards simples
- **v0.2** (12/07 tarde) — Busca fuzzy + sections + notas internas + 30 links pré-configurados + Playbook Kairós
- **v0.3** (12/07 noite) — 10 bugs corrigidos (form, contadores, breadcrumb, persistência, +)
- **v0.4** (12/07 noite) — Notas como ARTIGO (max-width 780px, line-height 1.8, h4 rosa mono)
- **v0.5** (12/07 noite) — Sem wrapper de nota, texto flui direto
