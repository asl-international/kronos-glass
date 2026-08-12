# Painel — Decisões de Design + Histórico de Versões

## Decisões estruturais

### Por que HTML único sem build?
- Marcelo já tem 3 outros painéis (ESL, FSL, Kairós) que são HTMLs únicos
- Consistência de padrão
- Zero fricção pra abrir (file://)
- Backup trivial (1 arquivo só)

### Por que HTML em vez de Notion/ClickUp?
- Customização visual total (identidade dark + rosa reaproveitada)
- Sem dependência externa (se Notion mudar preço/layout, não quebra)
- Performance (HTML é instantâneo, Notion é lento)
- Single source of truth (1 arquivo = 1 backup)
- Custom: notas viram artigos com tipografia específica, sections com hierarquia custom

### Por que localStorage e não backend?
- Painel é pessoal do Marcelo (não compartilhado com o time)
- Sem custos de infra
- Sem preocupação com LGPD (dados ficam no browser)
- Backup manual via console (`copy(localStorage.getItem('kronos_state_v1'))`)
- Backend sync é sprint v2+ (Supabase)

### Por que dark + rosa pink (`#ec4899`)?
- Identidade visual consistente com outros painéis do user (ESL, Kairós)
- Inspirado nos layouts "Workshop Destrava Shopee" e "PSL · Página Super Legal" que o user trouxe como referência
- Glass (v0.13+) adiciona frosted glass + glow

### Por que 5 layouts full (v0.13)?
- Marcelo reclamou "não gostei do Layout C" e pediu opções
- Mavis construiu 5 opções (Bento, Editorial, Dense, Glass, Notion) com painel COMPLETO
- Marcelo escolheu **Glass** em 17/07
- Outros 4 layouts congelados em v0.13, não atualizam mais

## Decisões de UX

### Por que busca fuzzy (não exata)?
- User pediu "barra de busca muito inteligente capaz de poder encontrar, mesmo com poucas palavras ou de modo não literal"
- Permite match por trecho de URL (`datastudio` acha as 3 dashboards do Workshop)
- Permite match em nota (buscar "drive" acha menções no Playbook)
- Levenshtein com threshold 2 permite tolerância a typo

### Por que "section" como tipo de item (não pasta)?
- User descreveu como "pasta" mas já existia a palavra "Biblioteca" no painel (conflito semântico)
- "Section" é mais claro tecnicamente: agrupa outros items

### Por que notas como artigo (não como card)?
- User pediu "estilo doc, notion, blog" e depois "quero apenas que esteja escrito na página, entende?"
- Notas são conteúdo de leitura, não items de uma lista
- Renderizar como `<article>` com h2/h3/h4 dentro flui naturalmente no main

### Por que modal centralizado (não form inline)?
- v0.5 tinha form inline que renderizava LÁ EMBAIXO da lista (longe de onde user clicou)
- User disse "adicionou e não apareceu nada" — era o form escondido embaixo
- Modal centralizado aparece imediatamente, foco no nome, com backdrop visual

### Por que sections sempre abertas (sem toggle)?
- v0.5 tinha toggle ▸/▾ que adicionava fricção
- Sections são como capítulos de doc — fazem sentido sempre visíveis
- Removido o estado `openSections` (era persistente mas perdeu propósito)

### Por que priorizar nome grande (h3 22px) no sub-item nota?
- h3 em 22px + border-bottom cria a divisão de "capítulo" dentro do main
- Contraste com o texto da nota em 16px estabelece hierarquia clara (título vs corpo)
- Mobile-friendly (lê rápido, não vira wall-of-text)
- Diferente de cards de item (que são menores) — nota é conteúdo de leitura, merece peso visual

### Por que bullets hierárquicos no Resumo?
- `//` (rosa) para área = capítulo principal
- `○` (rosa vazio) para sub = seção
- `·` para item = linha
- Hierarquia visual clara, sem confundir com bullets de item (`-`)
- Marcelo pediu "bullets funcionando" (estava sem)

### Por que hash routing?
- Compartilhar URL: "olha esse item: https://.../#/produtos/workshop"
- F5 mantém o lugar
- Browser back/forward funciona
- Não precisa configurar Vercel rewrites (hash não vai pro servidor)
- Funciona em GitHub Pages, file://, qualquer host

### Por que merge automático no loadState?
- Marcelo tem localStorage antigo com STATE de versões anteriores
- Sem merge: state novo fica em "limbo" até user limpar manualmente
- Com merge: items novos do INITIAL_DATA aparecem junto com edições antigas
- Preserva edições do Marcelo (não sobrescreve STATE)
- Cleanup de chaves legacy (aninhadas erradas) evita bugs

### Por que Glass (não Bento/Editorial/Dense/Notion)?
- Marcelo escolheu em 17/07 após comparar os 5
- Glass tem a melhor combinação de: identidade visual (rosa + frosted glass), hierarquia clara, densidade correta, performance

## Histórico de versões

### v0.17 (07-12/08/2026) — Mobile + Hash routing + Add manual fix
- Mobile: nav-burger, drawer, breadcrumb, CSS @media
- Hash routing (deep link compartilhável)
- Add manual: 3 bugs corrigidos (saveAddEdit, bindItemActions, collectAllItems)
- Cleanup legacy no loadState
- Cards "UNDEFINED" corrigidos (type + nome em todos os items)
- Modal Resumo CSS `.show` aceito

### v0.15 (28-29/07/2026) — Custom domain + Home limpa
- Domínio `painel-kronos.asli.international` via Vercel + Cloudflare
- Home sem "X de Y preenchidos"
- Bullets hierárquicos no Resumo
- Merge automático no loadState
- Token Vercel novo

### v0.14 (28/07/2026) — Glass canônico + 28 URLs
- 28 URLs plugadas no INITIAL_DATA
- Cards com type + nome corretos
- Botão Resumo com hierarquia
- TOC lateral (≡ à esquerda)
- Filtro por tipo funcional
- Vazios escondidos

### v0.13 (17/07/2026) — 5 Layouts full
- Bento, Editorial, Dense, Glass, Notion
- 5 repos no GitHub, 5 Vercel URLs
- Glass escolhido pelo Marcelo

### v0.12 (16/07/2026) — Layout C + Docs locais + Resumo
- Layout C (Craft minimal) — texto puro, divisores
- 8 docs locais adicionados (Contrato, Avatar, Produtos, Onboarding, Roteiros, Briefing, Relatório)
- Botão Resumo no topnav
- 6 atas de reunião NÃO incluídas (histórico → Sheets)

### v0.11-teste (15/07) — Escopo reorganizado
- Header de resumo, filtro por tipo, agrupamento, vazios escondidos

### v0.10-teste (15/07) — Busca extensiva
- Stemmer PT, 200+ sinônimos, navegação por teclado

### v0.9-teste (13/07 noite) — Notes como cards colapsáveis
### v0.8-teste (13/07 tarde) — 10 mudanças da reunião 11/07
### v0.7-teste (13/07 manhã) — Migração Asaas + Track record
### v0.6 (12/07 noite) — Canônico LEGADO (modal centralizado)
### v0.5 (12/07 noite) — Sem formato de nota
### v0.4 (12/07 noite) — Notas como ARTIGO
### v0.3 (12/07 noite) — 10 bug fixes
### v0.2 (12/07 tarde) — Busca + notes + sections + 30 links
### v0.1 (12/07 manhã) — Esqueleto

## Bugs corrigidos que NÃO voltam

| Bug | Causa | Fix |
|---|---|---|
| Editar section não permitia mudar nome | Form só renderizava pra items não-section | Modal genérico com nome+type |
| Editar sub-item não tinha nome nem tipo | Condição `!parentId` escondia | Modal genérico |
| Editar nota não tinha nome nem Apagar | Mesma coisa | Modal genérico |
| Galerias da Ju sem nome | INITIAL_DATA sem campo `nome` | Adicionado |
| Busca fuzzy gerava falsos positivos | Algoritmo "letras em ordem" | Substituído por Levenshtein |
| Breadcrumb "Operação" levava pra Comercial | Hardcoded | Adicionado tipo `operacao-aggregated` |
| `openSections` não persistia | Set em memória | Salvo no `kronos_ui_v1` |
| `+` da section só aparecia quando aberta | Condicional `isOpen` | Removido condicional |
| Contador Produtos ignorava STATE | Iterava só ESTRUTURA | Refatorado STATE + ESTRUTURA |
| Form inline de adicionar renderizava embaixo | Dentro do loop de items | Modal centralizado |
| Adicionar/Editar sem aparecer nada | Modal escondia form | Modal centralizado |
| Cards com "UNDEFINED" no Resumo | Items sem `type` e `nome` | Adicionados em todos |
| Modal Resumo não abria | CSS esperava `.open`, JS usava `.show` | CSS `.show,.open` aceito |
| Add manual não salvava | `saveAddEdit` usava chave aninhada | Flat com ponto `scope.sub` |
| Add manual não renderizava | `collectAllItems` só varria ESTRUTURA | Junta STATE + ESTRUTURA |
| `bindItemActions` não passava parentId | Argumento faltando | Passa `currentSubScope` |
| STATE legacy com chaves aninhadas | Bug antigo do saveAddEdit | Cleanup no loadState |
| Mobile sem nav (escondida) | CSS @media escondia | Nav-burger + drawer |
| Mobile sem "voltar" | Não tinha breadcrumb | Breadcrumb "← Voltar" |
| Botão TOC ≡ grande no mobile | 30x46 fixo | 22x32 no mobile |
| URL não refletia onde estava | Sem hash routing | `location.hash` atualiza |
| Deep link não funcionava | Sem parsing de hash | `parseHashAndNavigate` |

## Decisões que foram revertidas

| Decisão original | Por que reverteram |
|---|---|
| Notas com fundo cinza e mono (v0.2) | "feio, contra-intuitivo, quero artigo" |
| Notas com border-left amarela + colapso (v0.3) | "ainda feio, pouco intuitivo, quero apenas escrito na página" |
| Section com toggle ▸/▾ pra expandir (v0.4) | "feio, pouco intuitivo, não quero adicionar como bloquinhos" |
| Form inline pra adicionar (v0.5) | "adicionou e não apareceu nada" (form renderizava embaixo) |
| Modal de Mover (v0.2) | Marcelo preferiu drag-and-drop futuro (ainda pendente) |
| Vazios visíveis por padrão (v0.13) | "O que é vazio não precisa aparecer" (v0.14) |

## Princípios seguidos

1. **Visual consistente com os outros painéis** (ESL, Kairós)
2. **Simplicidade > features**: menos botões, mais fluxo
3. **Conteúdo escrito, não items de lista** quando for texto longo
4. **Sem placeholder visual feio** — vazios escondidos por padrão
5. **Modal centralizado** pra qualquer criar/editar, não inline
6. **Cards compactos** pra items de lista (link, planilha, doc)
7. **Texto flui na página** pra notas, sem wrapper
8. **Backdrop blur** em modais
9. **Contadores em tempo real** na sidebar
10. **Highlight (pulse rosa)** quando item é criado/pesquisado
11. **Hash routing** pra deep link compartilhável
12. **Merge automático** pra compatibilidade com STATE antigo
13. **Glass** como layout definitivo (escolha do Marcelo)
14. **Custom domain** pra identidade profissional
