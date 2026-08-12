# Instituto Kronos · Painel de Controle

> Hub agregador da operação. **Não é app de aluno, não tem checkout, não tem área logada.** É o índice centralizado pra achar qualquer coisa que a operação produziu, hospeda ou precisa.

**URL oficial**: https://painel-kronos.asli.international/
**Repositório**: https://github.com/asl-international/kronos-glass
**Layout canônico**: **Glass** (frosted glass + glow + rosa pink), escolhido pelo Marcelo em 17/07/2026.

---

## O que é

- **Hub de links** — Sheets, Docs, Drive, Looker, Zouti, Asaas. Tudo link, nada embutido.
- **Exceção**: Playbook Mentoria Kairós vive como notas internas (precisa de busca + visualização colapsável).
- **Single-user, single-device** por design (Marcelo). Multi-user é v2+.
- **Estrutura replicável** entre projetos da ASL-I (KSL/HSL/VSL/LSL/PPSL/PSL/RSL/CSL/FSL).

## Stack

- **HTML único** (`index.html` ~85KB), vanilla JS, CSS embutido
- **Sem build, sem bundler, sem framework**
- **localStorage** (chave: `kronos_state_v1`)
- **Google Fonts** (Inter + IBM Plex Mono + Space Grotesk) — única dep externa
- **Deploy**: Vercel, auto-deploy via GitHub push
- **Domínio custom**: `painel-kronos.asli.international` (CNAME → `cname.vercel-dns.com`)

## Como funciona

### Abrir no navegador
```
https://painel-kronos.asli.international/
```

### Local (dev)
```bash
cd C:\Users\bueno\Documents\Kronos
python start.py
# abre http://127.0.0.1:8773/
```

### Atualizar o deploy
```bash
# editar C:\Users\bueno\Documents\Kronos\layouts\full-glass.html
# push pro GitHub
gh api repos/asl-international/kronos-glass/contents/index.html -X PUT ...
# Vercel auto-deploya em ~30s
```

## Layouts (escolha)

5 layouts full foram construídos em 17/07. **Glass** foi o escolhido:

| Layout | URL | Conceito | Status |
|---|---|---|---|
| **Glass** (escolhido) | https://kronos-glass.vercel.app | Frosted glass + glow + rosa | **Canônico, atualizado** |
| Bento | https://kronos-bento.vercel.app | Apple/Linear | Congelado v0.13 |
| Editorial | https://kronos-editorial.vercel.app | Stripe Press / Medium | Congelado v0.13 |
| Dense | https://kronos-dense.vercel.app | Admin / power-user | Congelado v0.13 |
| Notion | https://kronos-notion.vercel.app | Sidebar persistente | Congelado v0.13 |

## Funcionalidades principais

- **6 camadas** (Visão Geral, Gestão, Operação, Produtos, SOPs, Biblioteca, Conhecimento)
- **7 sub-áreas de Operação** (Comercial, Marketing, Produto, CS, Tráfego, Financeiro, RH) com tabs
- **5 Produtos** (Mentoria Kairós, Workshop Destrava Shopee, Eventos, Minicurso, Comunidade) com tabs
- **Busca fuzzy** com stemmer PT + 200+ sinônimos
- **Botão Resumo** no header — popup com todos os 28 links, hierarquia `// área > ○ sub > · item`, busca + copy + download .md
- **TOC lateral** (botão ≡ à esquerda) — índice completo clicável
- **Hash routing** — URLs tipo `/#/produtos/workshop` pra deep link compartilhável
- **Adicionar/editar items** via modal centralizado
- **Mobile** — nav-burger, drawer lateral, breadcrumb "← Voltar"
- **Vazios escondidos** por padrão (só aparecem items com URL)

## Onde achar o que

| Preciso de... | Vai em |
|---|---|
| Estado atual do projeto | `docs/04-STATUS.md` |
| Última versão deployada | `docs/02-CHANGELOG.md` |
| Sprints pendentes | `docs/03-ROADMAP.md` |
| Arquitetura técnica | `docs/06-ARQUITETURA.md` |
| Features em detalhe | `docs/07-FUNCIONALIDADES.md` |
| Por que X, não Y | `docs/08-DECISOES-DESIGN.md` |
| Links pré-configurados | `docs/09-LINKS.md` |
| Contexto do Instituto | `docs/10-CONTEXTO-NEGOCIO.md` |
| Decisão específica de sprint | `docs/decisoes/v0.X-*.md` |

## Histórico de versões

- **v0.1 a v0.6** (12/07) — Esqueleto, busca, notes, modal centralizado
- **v0.7 a v0.11** (13-15/07) — Track record, Asas, busca extensiva, escopo reorganizado
- **v0.12-v0.13** (16-17/07) — 5 layouts full HTML
- **Glass escolhido como canônico** (17/07)
- **v0.14** (17-20/07) — Glass canônico + 28 URLs plugadas + Resumo + TOC + bullets
- **v0.15** (28-29/07) — Custom domain `painel-kronos.asli.international`
- **v0.16** (07/08) — Mobile: nav-burger, drawer, breadcrumb, hash routing
- **v0.17** (07/08) — Fix add manual de items (bug saveAddEdit + collectAllItems)

Detalhe completo em `docs/02-CHANGELOG.md`.
