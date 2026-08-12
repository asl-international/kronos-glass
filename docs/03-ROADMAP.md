# ROADMAP — Instituto Kronos · Painel

> **Backlog de sprints pendentes.** Se conflitar com `04-STATUS.md`, o STATUS vence (atualizado a cada sprint). Marcelo decide o que entra na próxima sessão; Mavis lembra o que tá aberto.

---

## ✅ Sprints CONCLUÍDOS (resumo)

- **v0.1** (12/07 manhã) — Esqueleto
- **v0.2** (12/07 tarde) — Busca + sections + notes + 30 links
- **v0.3** (12/07 noite) — 10 bug fixes
- **v0.4** (12/07 noite) — Notas como ARTIGO
- **v0.5** (12/07 noite) — Sem wrapper de nota
- **v0.6** (12/07 noite) — Canônico LEGADO (modal centralizado)
- **v0.7-teste** (13/07 manhã) — Migração Asaas + Track record (absorvido pela v0.8)
- **v0.8-teste** (13/07 tarde) — 10 mudanças da reunião 11/07
- **v0.9-teste** (13/07 noite) — Notes colapsáveis + 5 notes novas
- **v0.10-teste** (15/07 tarde) — Busca extensiva (stemmer + 200+ sinônimos)
- **v0.11-teste** (15/07 noite) — Escopo reorganizado
- **v0.12** (16/07) — Layout C + 8 docs locais + Resumo
- **v0.13** (17/07) — 5 Layouts full + escolha do Glass
- **v0.14** (28/07) — Glass canônico + 28 URLs + Resumo + TOC
- **v0.15** (28-29/07) — Custom domain `painel-kronos.asli.international`
- **v0.16** (07/08) — Mobile polish: nav-burger, drawer, breadcrumb, hash routing
- **v0.17** (07-12/08) — Fix add manual de items + cleanup legacy

---

## 🔴 ALTA (próximas sprints)

### #1 — 3 docs pendentes do Marcelo
- `roteiro_ja_vende_v3.docx` (Drive URL)
- `roteiro_sessao_nao_vende_v3.docx` (com correções de preço da v3)
- `produtos_kairos.docx` (NOVA, 20/07) — substitui `1D2PB3m`?
- **Esforço**: 5min (só plugar URLs)

### #2 — Contrato Kairós: confirmar URL
- Atualmente: `1q_0e-iJt4_NIueOv-Ie2hxzB4DbOX7yz`
- Marcelo precisa confirmar se mantém ou tem versão mais nova
- **Esforço**: 2min

### #3 — Desativar `kronos-glass.vercel.app` legado
- Deixar só `painel-kronos.asli.international` como oficial
- Vercel permite remover alias
- **Esforço**: 1min

### #4 — Embelezamento por IA
- Decisão 11/07: "passar em outra IA de embeleza, contando que ela não regace com o HTML"
- Ferramentas: Gamma, Relume, v0.dev
- **Regra**: não mexer em estrutura funcional, só em cores/espaçamentos/tipografia
- **Esforço**: 2-3h
- **Pode virar v0.18 ou v0.19**

### #5 — Botão de busca 🔍 no mobile
- Search ainda escondida no header mobile
- Adicionar botão 🔍 no nav-drawer que abre busca fullscreen
- **Esforço**: 30min

### #6 — Tags livres nos items
- Hoje: agrupamento só por tipo (link/sheet/nota)
- Com tags: agrupar por projeto (workshop 4, black friday), urgência (bloqueante), categoria pessoal
- Filtro multi-tag (AND/OR) + tags indexadas na busca
- **Esforço**: 1,5h

---

## 🟡 MÉDIA (curto-médio prazo)

### #7 — Preencher 90+ items vazios
- Gestão 10, CS 7, Produto 6, Tráfego 7, Financeiro 5, RH 4
- Kairós 7, SOPs 9, Biblioteca 10, Conhecimento 10
- **Esforço**: depende do Marcelo (enviar URLs)

### #8 — Drag-and-drop pra reordenar
- Hoje: ordem do ESTRUTURA ou de criação
- DnD HTML5 nativo (sem dep)
- Entre escopos (mover Comercial → Marketing) + dentro de section
- **Esforço**: 2h

### #9 — Export/Import do localStorage
- Hoje: se limpar localStorage, perde tudo
- Botão "Baixar backup" (JSON) + "Restaurar de JSON"
- Zona Perigosa com confirmação
- **Esforço**: 1h

### #10 — Tema light alternativo
- Hoje: dark + rosa (combina com ESL/FSL/Kairós)
- Em ambientes claros (sala de reunião) cansa
- Toggle dark/light com persistência
- **Esforço**: 1h

### #11 — Métricas de origens em planilha + dashboard
- Decisão 11/07: dados precisam estar visíveis pra operação
- Planilha dedicada (Sheets) + dashboard (Looker ou Sheets)
- **Não vai pro painel** — planilha tem o dado bruto, painel tem o link
- **Esforço**: 3h

### #12 — Track record: levantar cases existentes
- Note `Track record` em Gestão tem o template
- Trabalho: coletar cases reais com Ju e Roberta, formatar
- **Esforço**: 2h coleta + 30min formatação por case

### #13 — Workshops debrief: template + piloto
- Note `Workshops` em Conhecimento tem o template
- Pegar dados brutos dos Workshops 1-4, criar painel visual
- **Esforço**: 3h

### #14 — Reconfigurar automações ManyChat pós-12/07
- Decisão 11/07: "todas as automações ativas sempre conduzir para a ação vigente do workshop, exceto se forem relacionados à mentoria"
- Hoje: automações pausadas
- **Esforço**: 1h

---

## 🟢 BAIXA (longo prazo)

### #15 — Sincronização com backend
- localStorage é volátil (limpar browser, trocar, perder laptop)
- Backend mínimo (Supabase) com auth + sync
- Custo: free tier ou $25/mês pro
- Requer decisão de auth (só Marcelo? time? magic link? senha?)
- **Esforço**: 4-5h

### #16 — Sincronização em tempo real entre abas
- `BroadcastChannel` API — 2 abas do painel sincronizam
- Útil com 2 monitores
- **Esforço**: 1h

### #17 — Permissões por papel
- Decisão 11/07: "Roberta só vê Operação"
- Hoje: single-user, sem auth
- Marcelo admin, Ju/Gabriel operacionais, Roberta operacional com escopo reduzido
- **Esforço**: 5h
- **Pré-requisito**: backend #15

### #18 — Multi-projeto com STATE separado
- Decisão 11/07: mesma arquitetura 4+camadas serve pra qualquer projeto da ASL-I
- Hoje: seletor "Projeto ativo" é cosmético
- Quando virar real: `kronos_state_<projeto>` por projeto
- **Esforço**: 3h
- **Pré-requisito**: backend #15

---

## ❌ Decidido que NÃO entra

- **Mobile-first redesign** — operação usa desktop; toggle de sidebar ajuda em mobile mas não redesign
- **Sync em tempo real entre devices nesta fase** — localStorage é local por design
- **OAuth/magic link nesta fase** — single-user; auth entra com backend (#15)
- **Integração com Notion API** — HTML único é por controle total do layout, sem SaaS

---

## 📋 Como adicionar sprint nova

1. Adiciona na seção de prioridade com nome, esforço, descrição de 1-2 frases
2. Se for ALTA, marca como "Top 3 recomendados" no topo
3. Atualiza `04-STATUS.md` marcando que a sprint foi iniciada
4. Ao concluir: move pra "Sprints CONCLUÍDOS", adiciona entrada no `02-CHANGELOG.md`, cria nota de decisão em `docs/decisoes/` se não-trivial
5. Atualiza `04-STATUS.md` removendo de "Pendente"
