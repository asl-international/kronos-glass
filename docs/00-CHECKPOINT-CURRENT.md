# Instituto Kronos · Checkpoint Atual (v0.17 — Glass canônico + custom domain)

> **Última atualização**: 12/08/2026
> **Status**: v0.17 deployado · custom domain ativo · mobile OK · add manual OK
> **URL oficial**: https://painel-kronos.asli.international/
> **Repositório**: https://github.com/asl-international/kronos-glass

---

## 🆕 v0.17 (07-12/08/2026) — Mobile + Hash routing + Add manual fix

### O que mudou

1. **Mobile polish** (v0.16+): nav-burger, drawer lateral, breadcrumb "← Voltar"
2. **Hash routing** (v0.16): URLs tipo `/#/produtos/workshop` deep-link compartilháveis
3. **Add manual de items** (v0.17): bug do `saveAddEdit` corrigido (chave flat com ponto)
4. **Cleanup automático** de STATE legacy no `loadState`
5. **Card "UNDEFINED"** corrigido (items agora têm `type` e `nome` no INITIAL_DATA)
6. **Modal Resumo** com CSS `.show` aceito (era `.open`)

### Validação
- 28/28 URLs no Resumo (testado via puppeteer)
- Mobile iPhone 14 Pro (393x852): TOC, Resumo, Comercial, add OK
- Add manual: `STATE['produtos.workshop']` cresce, item aparece na lista
- 0 erros de console (exceto favicon 404)

---

## 🆕 v0.15 (28-29/07/2026) — Custom domain + Home limpa

### O que mudou
1. **Domínio custom**: `painel-kronos.asli.international` configurado na Vercel
2. **Home sem "X de Y preenchidos"** no lead e no meta — só `atualizado DD/MM, HH:MM`
3. **Bullets hierárquicos** no Resumo (`// área > ○ sub > · item`)
4. **Merge automático** no `loadState` (localStorage legacy + INITIAL_DATA novo)
5. **Token Vercel novo** (o anterior expirou): `vcp_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX` (substituído por placeholder — pedir token real no AGENT_DOCS local)

---

## 🆕 v0.13 (17/07/2026) — Layout C (Glass) escolhido

### Decisão
Marcelo escolheu **Glass** entre 5 opções:
- Bento, Editorial, Dense, **Glass (escolhido)**, Notion

### O que mudou
1. **5 layouts full** (~85KB cada) deployados em 5 URLs Vercel separadas
2. **5 repos** no GitHub: `kronos-{bento,editorial,dense,glass,notion}`
3. **Glass promovido** pra canônico (`index.html` no `kronos-glass`)
4. **Glass tem identidade visual**: frosted glass + glow + rosa pink + gradientes radiais
5. **Outros 4 layouts** congelados em v0.13 (não atualizam mais)

### Glass characteristics
- `body::before` com gradiente radial (rosa + roxo + azul)
- `body::after` com grid sutil de pontos
- Cards com `backdrop-filter: blur(12px) saturate(180%)`
- Topnav com `backdrop-filter: blur(20px) saturate(180%)`
- Modais com blur mais forte
- Fontes: Inter + Space Grotesk + IBM Plex Mono

---

## Estado técnico (v0.17)

- **Tamanho**: ~93KB single-file HTML
- **Servidor local**: `python start.py` → http://127.0.0.1:8773/
- **Deploy**: Vercel, auto-deploy via GitHub push (~30s)
- **Domínio**: `painel-kronos.asli.international` (canônico), `kronos-glass.vercel.app` (legado)
- **SSL**: Vercel automático (Let's Encrypt)
- **Persistência**: localStorage (`kronos_state_v1`)
- **0 erros** no console (validado Playwright/puppeteer)
- **0 "undefined"** em todos os escopos (depois do fix em v0.14)

## Estrutura de navegação (28 items com URL)

```
Visão Geral (home) — 6 cards das camadas
├── Gestão (0/0 vazios) — slot sem URLs pré-populadas
├── Operação (7/7 com URL):
│   ├── Comercial (12): Agendamento 1:1, Pré-diagnóstico, Formulário, Live, 3 respostas,
│   │                  À vista (Asaas), Parcelado (Zouti), Contrato, Produtos/Negociação, Avatar
│   ├── Marketing (10): Roteiros Kairós, Raio X vende/não vende, Roteiros criativos,
│   │                  Galeria 1/2, Logo WDS, Elementos, Fotos evento, Captações Juliana
│   ├── CS (1): Acompanhamento geral de mentorados
│   └── (4 sub-áreas vazias: Produto, Tráfego, Financeiro, RH)
├── Produtos (4/4 com URL):
│   ├── Workshop (3): Dashboard 1, 2, 3
│   ├── Eventos (1): Manual do Participante
│   └── (3 produtos vazios: Kairós, Minicurso, Comunidade)
├── SOPs (1/1 com URL): Playbook Kairós
├── Biblioteca (0/0) — todas vazias
└── Conhecimento (0/0) — todas vazias
```

**Total: 28 items com URL · 86 items vazios (escondidos por padrão)**

## Decisões de UX (Layout Glass)

- **Bullets hierárquicos** no Resumo: `// área` (rosa) > `○ sub` (rosa vazio) > `· item`
- **Filtro** por tipo: Todos / Notas / Links / Planilhas / Documentos
- **Vazios escondidos** por padrão (`showEmpty=false`)
- **Modal** de item com `backdrop-filter: blur(8px)`
- **Cards glass**: rgba 0.04, blur 12px, border rgba 0.08
- **Topnav glass**: backdrop blur 20px
- **Sem tooltip noise** — drag handle `⋮⋮` só no hover
- **TOC lateral** (`≡`): painel 300px, hierarquia 3 níveis, sem bullets
- **Hash routing**: URL muda conforme navega, deep link compartilhável

## Status do Resumo (validado 28/07)

| Seção | Items |
|---|---|
| Operação | 23 (Comercial 12 + Marketing 10 + CS 1) |
| Produtos | 4 (Workshop 3 + Eventos 1) |
| SOPs | 1 (Playbook) |
| **Total** | **28** |

**Testes automáticos**: 28/28 links da lista do Marcelo presentes e clicáveis.

## Custom domain

- **Apex**: `asli.international` (gerenciado no Cloudflare)
- **Subdomínio**: `painel-kronos` → `painel-kronos.asli.international`
- **CNAME**: `painel-kronos.asli.international` → `cname.vercel-dns.com` (proxy: **DNS only / cinza**, NÃO laranja)
- **SSL**: automático via Vercel
- **Vercel dashboard**: https://vercel.com/dashboard → projeto `kronos-glass` → Settings → Domains

## Próximos passos

1. **3 docs pendentes** (Marcelo precisa subir Drive):
   - `roteiro_ja_vende_v3.docx`
   - `roteiro_sessao_nao_vende_v3.docx`
   - `produtos_kairos.docx` (NOVA, 20/07) — substitui `1D2PB3m`?
2. **Contrato Kairós**: mantém `1q_0e-iJt` ou tem versão mais nova?
3. **Desativar `kronos-glass.vercel.app`** legado? (recomendo sim)
4. **Botão de busca no mobile** (search ainda escondida no header mobile)
5. **90+ items vazios** esperando URLs (Gestão 10, CS 7, Produto 6, Tráfego 7, Financeiro 5, RH 4, Kairós 7, SOPs 9, Biblioteca 10, Conhecimento 10)

## Memória persistida

- `C:\Users\bueno\.minimax\agents\mavis\memory\MEMORY.md` (preferências Marcelo + estado Kronos)
- `C:\Users\bueno\.mavis\artifacts\kronos-prints\` (80+ PNGs de auditoria visual ao longo do projeto)
