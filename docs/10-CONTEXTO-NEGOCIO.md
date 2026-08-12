# Instituto Kronos — Contexto de Negócio

## Quem é

**Instituto Kronos** é uma empresa de educação/mentoria pra lojistas da Shopee, fundada pela **Juliana Magalhães** ("Ju"). Atua principalmente com a **Mentoria Kairós** (programa principal) e o **Workshop Destrava Shopee** (evento/lançamento).

A operação é administrada pela **ASL-I** (gestora de operações de diferentes especialistas).

## Time

| Papel | Responsável | Função |
|---|---|---|
| Expert / Estratégia | **Juliana** (Ju) | Aulas, oficinas, análise estratégica, sessões individuais |
| CS / Customer Success | **Roberta** (Roh) | Onboarding, follow-up, triagem WhatsApp, CRM |
| Contratos / Financeiro | **Marina** | Geração de contratos e assinaturas |
| Acessos / TI | **Gabriel** | Liberação de Drive, Zouti, plataformas |

> **Natália Limiro** também é citada pelo user no contexto de outros projetos, mas o papel específico dela no Instituto Kronos não ficou detalhado. **Marcelo Bueno** é o próprio user (auxiliar de tecnologia), não membro do time da Ju.

## Produtos

### 1. Mentoria Kairós (programa principal)
- **Duração**: 12 meses
- **Público-alvo**: Lojistas, fabricantes, revendedores com vendas travadas na Shopee
- **Ponto de partida**: Errando na precificação, operando com prejuízo/margem apertada
- **Ponto de chegada**: Vendendo R$50 mil/mês com margem saudável e operação organizada pra escalar
- **Plataforma de alunos**: **Zouti** (área de membros) + **Drive** (caixa de ferramentas)
- **Disparos automáticos**: **ManyChat** (e-mail + WhatsApp no momento do pagamento)
- **Canal principal com aluno**: WhatsApp (atendimento seg-sex 9h-18h)
- **Marcos**: Mês 6 (check-in meio), Mês 10 (conversa de continuidade/renovação)

#### Jornada do aluno (6 fases)

```
Fase 0: Onboarding (72h) → Fase 1: Margem → Fase 2: Loja e Oferta
   → Fase 3: Crescimento → Fase 4: Escala → Fase 5: Encerramento e Retenção
```

#### Cadência operacional
- **Diário (CS)**: Triagem WhatsApp 9h-18h + atualizar CRM
- **Semanal (CS)**: Varredura de alunos sumidos + lembretes de sessões
- **Quinzenal (time + Ju)**: Reunião com status por fase + alertas
- **Mensal**: Revisão de retenção e resultados

#### Régua de saúde do aluno
- 🟢 **Ativo** — participa, atualiza painel, executa
- 🟡 **Atenção** — faltou 1 encontro ou atrasado na execução
- 🔴 **Risco** — sumiu há 2+ semanas, painel parado

#### Scripts prontos (19)
Biblioteca de textos-modelo pra CS usar no WhatsApp (boas-vindas, agendamento, follow-up, resgate, etc).

### 2. Workshop Destrava Shopee
- Evento/lançamento
- Tem 3 dashboards de performance (Looker + Sheets)
- Material de divulgação em Drive

### 3. Eventos Presenciais
- "Planejando 2026" é o evento conhecido
- Tem galeria de fotos

### 4. Minicurso
- (Pouco definido ainda — slot vazio no painel)

### 5. Comunidade
- (Pouco definido ainda — slot vazio no painel)

## Ferramentas do time

| Ferramenta | Uso |
|---|---|
| Google Sheets | Planilhas operacionais (leads, respostas, dashboards) |
| Google Docs | Documentos (Playbook, Avatar, Roteiros de criativos) |
| Google Drive | Assets (fotos, logos, materiais) |
| Looker Studio | Dashboards de performance |
| Zouti | Área de membros dos alunos |
| Asaas | Gateway de pagamento (substituindo Zouti na migração) |
| ManyChat | Disparos automáticos (e-mail + WhatsApp) |
| WhatsApp | Canal principal com aluno |
| Vercel (kairos-roteiros) | App de roteiros da Kairós |
| Cloudflare Pages (int-kronos) | Landing pages (pré-diagnóstico) |
| Canva | Templates visuais |
| Pagius (paginas.institutokronos) | Páginas institucionais |
| Forms.gle | Formulários Google |
| Pay.zouti | Checkout parcelado (durante migração) |
| Exposure (amarifoto) | Galerias de fotos profissionais |

## Regra de ouro (do Playbook)

> "Aluno sem contrato assinado não avança. Nenhum acesso é liberado antes da assinatura confirmada."

A operação da Kairós tem um rigor muito forte em:
- Não responder WhatsApp fora do horário (9h-18h)
- CS resolve dúvidas operacionais; Ju resolve estratégicas (em lote, não em tempo real)
- Acolhimento > pressa (Script 7: aluno com margem negativa recebe acolhimento, não bronca)

## O que dá dinheiro (numbers que importam)

- **Meta de venda do Workshop** = 500 vendas (no período do evento)
- **Workshop ativo**: 07/07/2026 a 08/08/2026 (33 dias, 24 úteis)
- **Meta diária**: ~15,2 vendas/dia (20,8 em dia útil)
- **Ticket médio Kairós**: R$ alto (não detalhado pelo user)
- **Objetivo Kairós**: aluno saí vendendo R$50k/mês com margem saudável

## Sinais de alerta mapeados (8)

Do doc oficial:
1. Não acessou a Zouti em 72h
2. Não respondeu boas-vindas
3. Não entrou no grupo em 48h
4. Faltou sessão
5. Mais de 5 dias sem resposta
6. Monossilábico (resposta curta/genérica)
7. Dificuldade com parcelas
8. "Está corrido" (frescura pra sair)

**Ação preferida**: ligar (não só mensagem).

## O que o user (Marcelo) cuida vs Ju

Marcelo é o user principal da nossa conversa. Ele tem outros projetos:
- **ESL** (Meta Ads): dashboard de ads, planilhas Google Sheets via Apps Script
- **Kairós / OSL** (Onboarding): sistema de onboarding de alunos em HTML único
- **FSL** (CRM): painel de leads e agendamentos
- **KSL** (este painel): hub agregador de tudo da operação

A relação dele com o Instituto Kronos parece ser:
- Auxiliar na operação/tecnologia
- Constrói ferramentas pra time da Ju
- Mantém o painel atualizado com links, docs e assets

---

## Como o Instituto Kronos aparece no painel

O painel `kronos-glass.vercel.app` / `painel-kronos.asli.international` é o **hub agregador de TUDO** que a operação usa. Ele não é um app pro aluno — é pra Ju, Roberta, Marina, Gabriel e o próprio Marcelo terem um único lugar pra achar qualquer coisa.

Por isso a estrutura do painel reflete a operação:
- **Gestão** = visão macro (OKRs, KPIs, roadmap) — **ainda vazio**
- **Operação** = 7 áreas funcionais (Comercial, Marketing, Produto, CS, Tráfego, Financeiro, RH)
- **Produtos** = 5 ofertas (cada uma com sua "caixa de ferramentas")
- **SOPs** = como fazer as coisas
- **Biblioteca** = assets pra consulta
- **Conhecimento** = aprendizados históricos

Cada item de produto ou área é um link externo (Sheets, Docs, Drive, Looker, etc) — o painel é o **índice**, não a fonte de verdade.

## Estado atual (v0.17)

- **28 items com URL** pré-populados
- **86 items vazios** (escondidos por padrão)
- **Layout Glass** (frosted glass + glow) escolhido
- **Custom domain**: `painel-kronos.asli.international`
- **Mobile OK** com nav-burger + drawer + breadcrumb
- **Hash routing** pra deep link compartilhável
- **Add manual de items** funciona (v0.17 fix)

## O que ainda falta desenvolver (mencionado em conversa)

- **3 docs pendentes** que Marcelo precisa subir Drive:
  - `roteiro_ja_vende_v3.docx`
  - `roteiro_sessao_nao_vende_v3.docx`
  - `produtos_kairos.docx` (NOVA, 20/07)
- **90+ items vazios** esperando URLs (Gestão 10, CS 7, Produto 6, Tráfego 7, Financeiro 5, RH 4, Kairós 7, SOPs 9, Biblioteca 10, Conhecimento 10)
- **ASL-I OS replicável**: user mencionou que a ASL-I opera com diferentes especialistas, mas isso ainda é prematuro (só 1 cliente)
- **Playbook expandido**: 6 fases × 4 blocos (cliente vive / time faz / sinais / critério) já documentadas, mas operacionalização ainda em construção
