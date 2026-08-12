# Painel — Arquitetura & Dados

## Stack

- **HTML único**: `index.html` (~93KB, ~3000 linhas)
- **CSS**: embutido em `<style>` no `<head>`, variáveis CSS no `:root`
- **JS**: vanilla no `<script>` no fim do `<body>`, sem build, sem bundler
- **Dependências externas**: Google Fonts (Inter + Space Grotesk + IBM Plex Mono)
- **Persistência**: `localStorage` (chave `kronos_state_v1`)
- **Deploy**: Vercel, auto-deploy via GitHub push
- **Domínio custom**: `painel-kronos.asli.international` (CNAME → `cname.vercel-dns.com`)
- **SSL**: Vercel automático (Let's Encrypt)
- **Servidor local**: `python start.py` → http://127.0.0.1:8773/

## Estrutura de arquivos

```
C:\Users\bueno\Documents\Kronos\
├── index.html                  # LEGADO (v0.6, não mexer)
├── index-teste.html             # LEGADO (v0.11 backup)
├── index-teste-v11-backup.html  # LEGADO
├── layouts/
│   └── full-glass.html          # CANÔNICO deployed
├── start.py                     # servidor local
├── ksl-main/                    # documentação técnica (será movida pra docs/ no GitHub)
│   ├── README.md
│   ├── 00-CHECKPOINT-CURRENT.md
│   ├── 02-CHANGELOG.md
│   ├── 03-ROADMAP.md
│   ├── 04-STATUS.md
│   ├── 05-AGENT_DOCS.md
│   ├── 06-ARQUITETURA.md         # este arquivo
│   ├── 07-FUNCIONALIDADES.md
│   ├── 08-DECISOES-DESIGN.md
│   ├── 09-LINKS.md
│   ├── 10-CONTEXTO-NEGOCIO.md
│   └── docs/decisoes/
└── artifacts/                   # prints de validação (local only, não vai pro GitHub)
```

## Estrutura do código (dentro do `layouts/full-glass.html`)

```html
<head>
  └── <style> ... </style>  # CSS (variáveis, layout glass, modais, @media)
<body>
  ├── <nav class="topnav">       # Topnav com brand, links, search, resumo, nav-burger
  ├── <div class="nav-drawer">   # Drawer lateral (mobile)
  ├── <div class="toc-panel">    # TOC lateral (desktop)
  ├── <div class="toc-toggle">   # Botão ≡ do TOC
  ├── <main>
  │   ├── <section id="view-home">      # Visão geral
  │   ├── <section id="view-content">   # Páginas internas (renderScope)
  │   └── ...
  ├── <div id="modal-add-edit">   # Modal Adicionar/Editar
  ├── <div id="modal-resumo">     # Popup Resumo
  ├── <div id="modal-about">      # Modal Sobre
  ├── <div id="toast">            # Notificação flutuante
  └── <script> ... </script>      # JS
       ├── ESTRUTURA              # Constante imutável (slots)
       ├── INITIAL_DATA           # Links pré-configurados
       ├── STATE                  # Estado runtime
       ├── loadState/saveState    # Persistência
       ├── parseHashAndNavigate   # Hash routing
       ├── navigate               # Mudar view
       ├── buildNav/renderHome/renderScope
       ├── collectAllItems        # STATE + ESTRUTURA
       ├── getScopeCount
       ├── buildResumo            # Markdown Resumo
       ├── openResumo
       ├── buildToc/openToc/closeToc
       ├── openNavDrawer/closeNavDrawer
       ├── openAddEdit/saveAddEdit/deleteItem
       ├── fuzzyScore             # Busca fuzzy
       ├── performSearch
       └── copy/download           # Resumo actions
```

## Modelo de dados

### 1. ESTRUTURA (constante, imutável)

Define a "casca" do painel: quais camadas, áreas funcionais, produtos, e os itens **padrão** que aparecem como slots vazios.

```js
const ESTRUTURA = {
  gestao: { titulo, eyebrow, descricao, items: [{id, nome}, ...] },
  operacao: { areas: { comercial: {titulo, items: [...]}, marketing: {...}, ... } },
  produtos: { items: { workshop: {titulo, items: [...]}, eventos: {...}, ... } },
  sops: { items: [...] },
  biblioteca: { items: [...] },
  conhecimento: { items: [...] }
};
```

### 2. INITIAL_DATA (constante, primeiro seed)

Pré-popula o STATE com 28 links do Instituto Kronos. Pode ser restaurado via botão "Restaurar padrão".

```js
const INITIAL_DATA = {
  'operacao.comercial': {
    'agendamento-1-1': { type: 'sheet', nome: 'Agendamento 1:1', url: '...' },
    'pre-diagnostico': { type: 'link', nome: 'Página de pré-diagnóstico', url: '...' },
    // ... 12 items total
  },
  'operacao.marketing': { /* 10 items */ },
  'operacao.cs': { 'acompanhamento': { type: 'sheet', nome: '...', url: '...' } },
  'produtos.workshop': { 'dash-1': { type: 'link', nome: 'Dashboard 1', url: '...' }, ... },
  'produtos.eventos': { 'manual-participante': { ... } },
  'sops': { 'playbook-kairos': { type: 'doc', nome: '...', url: '...' } }
};
```

**Convenção de chaves STATE**: `scopeKey + '.' + subScope` (flat com ponto) — ex: `operacao.comercial`, `produtos.workshop`. **NUNCA** aninhado (`operacao.comercial.workshop` seria errado).

### 3. STATE (runtime, mutável, persiste)

Espelha a estrutura do INITIAL_DATA + items custom. Salvo no localStorage a cada ação.

```js
let STATE = {
  'operacao.comercial': {
    'agendamento-1-1': { type: 'sheet', nome: '...', url: '...' },
    // ... 12 items do INITIAL_DATA
  },
  'operacao.marketing': { /* 10 items */ },
  'operacao.cs': { 'acompanhamento': {...} },
  'produtos.workshop': {
    'dash-1': { ... },
    // ... 3 items do INITIAL_DATA
    'meu-custom-123': { type: 'link', nome: 'Meu link', url: '...' },  // user-added
  },
  // ...
};
```

### 4. localStorage

| Chave | Conteúdo |
|---|---|
| `kronos_state_v1` | JSON do STATE completo |

Salvo via `saveState()` (chamado após criar/editar/apagar).

## Funções principais

| Função | O que faz |
|---|---|
| `loadState()` | Lê localStorage, merge com INITIAL_DATA, cleanup legacy |
| `saveState()` | Salva STATE no localStorage |
| `parseHashAndNavigate()` | Lê `location.hash` e navega (deep linking) |
| `navigate(scope, sub)` | Muda view + atualiza hash + renderiza |
| `buildNav()` | Renderiza topnav + nav-drawer |
| `renderHome()` | Renderiza visão geral (6 cards) |
| `renderScope()` | Renderiza página de escopo (header + subtabs + items) |
| `collectAllItems(scope)` | Junta items da ESTRUTURA + items custom do STATE |
| `getScopeCount(scope)` | Conta items preenchidos |
| `buildResumo()` | Gera markdown com hierarquia de links |
| `openResumo()` | Abre popup Resumo |
| `buildToc()` | Renderiza árvore do TOC |
| `openToc()` / `closeToc()` | Abre/fecha painel TOC |
| `openAddEdit()` / `saveAddEdit()` | Modal Adicionar/Editar item |
| `deleteItem()` | Apaga item do STATE |
| `clearAllCustom()` | Restaura INITIAL_DATA |
| `fuzzyScore()` / `performSearch()` | Busca fuzzy com stemmer + sinônimos |
| `toast(msg)` | Notificação flutuante |

## Tema visual (Glass)

- **Background**: `#0a0612` (preto profundo com gradiente radial rosa+roxo+azul)
- **Cards**: `rgba(255,255,255,0.04)` com `backdrop-filter: blur(12px) saturate(180%)`
- **Topnav**: `backdrop-filter: blur(20px) saturate(180%)`
- **Modais**: blur(8px) no backdrop
- **Bordas**: `rgba(255,255,255,0.08)` default
- **Cor primária (rosa)**: `#ec4899` (com glow)
- **Cor secundária (roxo)**: `#a78bfa`
- **Texto**: `#f5f5f7` (off-white)
- **Texto dim**: `#d4d4dc`
- **Texto faint**: `#5a5a6e` (labels mono)
- **Fontes**: Inter (texto) + Space Grotesk (títulos) + IBM Plex Mono (labels, eyebrows)

## Tipos de item suportados

| `type` | Render | Campos obrigatórios |
|---|---|---|
| `link` | Card compacto com ícone azul | `url` |
| `sheet` | Card compacto com ícone verde | `url` |
| `doc` | Card compacto com ícone amarelo | `url` |
| `note` | Artigo (texto fluindo) | `note` (texto longo) |
| `section` | h2 com sub-items | `items: { ... }` |

**Importante**: TODOS os items no `INITIAL_DATA` devem ter `type` e `nome` (a falta desses causa bugs visuais como "UNDEFINED").

## Hash routing

- `location.hash` muda conforme o usuário navega
- `#/` — home
- `#/operacao/comercial` — Operação > Comercial
- `#/produtos/workshop` — Produtos > Workshop
- `#/sops` — SOPs
- Ao abrir URL com hash, navega direto pro escopo
- `parseHashAndNavigate()` no boot e em `hashchange` event
