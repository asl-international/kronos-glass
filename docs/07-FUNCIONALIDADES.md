# Painel — Funcionalidades

Documentação das features em detalhe. Última atualização: 12/08/2026 (v0.17).

---

## 1. Topnav (navegação)

- **Brand "Instituto Kronos"** + tag `// PAINEL` (escondida no mobile)
- **Links das 6 camadas** (Visão Geral, Gestão, Operação, Produtos, SOPs, Biblioteca, Conhecimento) com contador `X/Y`
- **Busca global** (campo "Buscar..." com atalho `⌘K` no desktop)
- **Botão nav-burger** (☰) — só no mobile/tablet
- **Botão "≡ Resumo"** (rosa) — abre popup com todos os links

## 2. Visão Geral (Home)

- **Eyebrow rosa**: `// VISÃO GERAL`
- **Título**: "Painel de controle" (com "controle" em rosa gradient)
- **Lead**: "Hub agregador do Instituto Kronos. Tudo é link externo pra Sheets, Docs, Drive, Looker, Zouti, Asaas."
- **6 cards** grandes (1 por camada) com:
  - Eyebrow rosa (`// GESTÃO`, `// OPERAÇÃO`, etc)
  - Título da camada
  - Descrição curta
  - Contador `X/Y preenchidos` no rodapé
- **Click no card** → navega pra camada

## 3. Camadas (Gestão, Biblioteca, Conhecimento)

- **Eyebrow** + **título** + **lead** (descrição)
- **Breadcrumb** "← Voltar" (aparece só se tiver sub-escopo)
- **Header de resumo** com pills: "X notas · Y links · Z planilhas · W docs · X/Y preenchidos"
- **Filtro** por tipo: Todos / Notas / Links / Planilhas / Documentos
- **Cards de items** agrupados por tipo, cada um com:
  - Ícone de tipo colorido (link=azul, sheet=verde, doc=amarelo, note=roxo)
  - Número do item (01, 02, ...)
  - Nome do item + tag de tipo
  - Descrição (opcional)
  - URL encurtada (se houver)
  - Hover: ícone →, glow rosa, ações (✎ editar, × apagar)
- **Botão "+ adicionar item"** no final
- **Zona perigosa**: "Restaurar padrão" + "Limpar custom"

## 4. Operação

- **Eyebrow** + **título** "Operação" + lead
- **7 sub-abas** (tabs pill): Comercial, Marketing, Produto, CS, Tráfego, Financeiro, RH
- Click na sub-aba → filtra items dessa área
- Cada sub-aba mostra:
  - Breadcrumb "← Operação" (clicável, volta pra lista de sub-áreas se tiver)
  - Header de resumo + filtro (mesmo das camadas simples)
  - Items da sub-área
- **CS** (= Sucesso do Cliente) é a 4ª sub-aba
- 4 sub-áreas (Produto, Tráfego, Financeiro, RH) estão vazias (slots só)

## 5. Produtos

- **Eyebrow** + **título** "Produtos" + lead
- **5 sub-abas**: Mentoria Kairós, Workshop Destrava Shopee, Eventos Presenciais, Minicurso, Comunidade
- **Mentoria Kairós** (vazia por enquanto — 7 slots: Landing Page, Oferta, Criativos, Produto, Dashboards, Pesquisa, Financeiro)
- **Workshop Destrava Shopee** (3 dashboards pré-populados)
- **Eventos Presenciais** (1 item: Manual do Participante)
- **Minicurso, Comunidade** (sem items no ESTRUTURA)

## 6. SOPs

- **Eyebrow** + **título** "SOPs" + lead
- 9 SOPs (slots vazios) + 1 Playbook Kairós (Doc) com 10 sub-notas
- **Playbook** renderiza como nota interna (artigo com h3/h4)
- 9 SOPs conhecidos mas não populados (Como subir anúncio, Como criar campanha, etc)

## 7. Busca fuzzy (header, desktop)

- **Input no topnav** com placeholder "Buscar..." e atalho `⌘K`
- Dropdown com top 8 resultados ao digitar (mín 2 chars)
- Cada resultado: ícone do tipo + nome + breadcrumb do escopo
- Click no resultado → navega + scrollIntoView + pulse rosa no item
- **Algoritmo**: match exato (1000) > prefixo (500) > substring (300) > token (80/50/30) > Levenshtein ≤ 1 (40) ou ≤ 2 (15). Bônus +100 se todos tokens matched.
- **Normaliza acentos** (lowercase + strip diacritics)
- **Stemmer em PT** (plural, gerúndio, passado, -mente)
- **200+ sinônimos** (`mentorado=aluno=cliente`, `kairos=kairós=mentoria`, etc)
- ESC fecha dropdown
- ⏸ Não implementado no mobile ainda (escondida no @media 700px)

## 8. Resumo (popup topnav)

Botão "≡ Resumo" abre modal fullscreen com:
- **Filtro** de busca em tempo real
- **Botão "Copiar"** — copia markdown pro clipboard
- **Botão "Baixar .md"** — baixa `kronos-resumo.md`
- **Botão "Fechar"** (rosa)
- **Hierarquia com bullets**:
  - `// OPERAÇÃO (23)` (rosa, mono)
    - `○ Comercial` (sub-área, rosa vazio)
      - `· Agendamento 1:1` (item, link)
      - `· Página de pré-diagnóstico`
      - ...
- **Só items com URL** aparecem (vazios escondidos)

## 9. TOC lateral (botão ≡ à esquerda)

- **Botão** `≡` fixo à esquerda, opacity 0.35 (default) → 1 (on hover)
- **Painel** 300px, blur 20px, slide-in da esquerda
- **Hierarquia 3 níveis**:
  - VISÃO GERAL
  - GESTÃO
  - OPERAÇÃO
    - Comercial
      - Agendamento 1:1
      - ...
    - Marketing
      - ...
- **Só items com URL** (sem bullets `●/○` — só o nome limpo)
- **Click em item** → navega + scrollIntoView + fecha TOC
- **Fechar com X** ou **ESC**

## 10. Hash routing (deep link compartilhável)

- `location.hash` muda conforme usuário navega:
  - `/#/` — home
  - `/#/gestao` — Gestão
  - `/#/operacao/comercial` — Operação > Comercial
  - `/#/produtos/workshop` — Produtos > Workshop
  - `/#/sops` — SOPs
- **Abrir URL com hash** → navega direto pro escopo
- `parseHashAndNavigate()` no boot + listener `hashchange`
- Útil pra mandar link no chat: "olha esse item: https://painel-kronos.asli.international/#/produtos/workshop"

## 11. Mobile (v0.16+)

- **Viewport < 1100px** (tablet) e < 700px (mobile)
- **Topnav reduzido**:
  - Brand "Instituto Kronos" (tag `// PAINEL` escondida)
  - Botão `☰` (hamburger)
  - Botão `≡ Resumo`
- **Nav-drawer** (lateral direita, 300px, blur 20px):
  - Lista de áreas (Visão Geral, Gestão, Operação, etc) com contadores
  - Botão X pra fechar
  - ESC fecha
- **Breadcrumb "← Voltar"** em sub-escopos (Operação > Comercial → "← Operacao / Comercial")
- **TOC ≡** menor (22x32px no mobile, opacity 0.5)
- **Subtabs** com padding menor
- **Items** com padding reduzido
- **Modal** com max-width 96vw e overflow-y
- **Filtros** em wrap

## 12. Modal Adicionar/Editar (v0.6+)

Centralizado, com backdrop blur.

**Campos**:
- **Nome** (input grande, autofocus)
- **Tipo** (pills clicáveis: ◆ Nota · ↗ Link · ⊞ Sheet · ▤ Doc · ▾ Seção)
- **URL** (se tipo for link/sheet/doc)
- **Descrição** (opcional, mesmo caso)
- **Conteúdo da nota** (textarea grande, se tipo for nota)

**Botões**:
- `Cancelar`
- `Salvar` (rosa) / `Adicionar`

**Atalhos**:
- ESC fecha
- Click fora fecha

**Após salvar**:
- Modal fecha
- Item aparece na lista
- Toast "Salvo" / "Atualizado"

**Validação**:
- Nome é obrigatório (toast "Nome obrigatório" se vazio)
- URL é livre (não validado)

## 13. Persistência (localStorage)

- Chave: `kronos_state_v1`
- `saveState()` chamado após criar/editar/apagar
- `loadState()` no boot:
  1. Lê localStorage
  2. Cleanup legacy (chaves aninhadas `produtos`, `operacao` que não servem)
  3. Merge com INITIAL_DATA (adiciona items novos que faltam)
  4. Se localStorage vazio, usa INITIAL_DATA puro
- **Hash routing** NÃO persiste — é só URL

## 14. Atalhos de teclado

- **ESC**: fecha modal (Resumo, Add, About, TOC, Nav-drawer)
- **Enter no campo nome**: submete modal Add
- **⌘K / Ctrl+K**: foca no campo de busca
- **↑/↓** nos resultados de busca: navega entre matches
- **Enter** num resultado: vai pro item

## 15. Zona perigosa (footer de cada escopo)

- **"Restaurar padrão"**: copia INITIAL_DATA pro STATE (sobrescreve custom, preserva)
- **"Limpar custom"**: remove items custom do escopo atual (preserva INITIAL_DATA)
- Confirmação via `confirm()` antes de executar
- Toast "Restaurado" / "Apagado"
