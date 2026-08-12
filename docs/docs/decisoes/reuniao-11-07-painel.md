# Reunião 11/07/2026 — Decisões sobre o painel

> **Nota de arquivo**: Esta é a transcrição processada da reunião de 11/07/2026 que originou várias mudanças no painel. Foi movida de `06-contexto-conversa.md` (versão antiga) pra cá, seguindo o padrão VSL de `docs/decisoes/` para notas específicas de decisão.

**Quem**: Marcelo + Natália + Gabriel
**Duração**: ~1h30
**Transcrição**: 89KB (854 linhas) → processada e filtrada
**Filtro aplicado**: removido vida pessoal, piadas, comentários sobre IAs concorrentes, conversa fiada. Mantido: estrutura, decisões, regras de negócio, dúvidas, metáforas.

---

## 1. Estrutura organizacional (4 camadas)

### Decisão: estrutura top-down por departamentos primeiro, depois encaixar recursos
- **Natália**: "Eu tenho um pouco mais de facilidade de tentar olhar tudo e aí ir encaixando o que tem... seria a gente pegar e separar todos como se fossem departamentos. E aí vai criando todos esses espaços de departamentos, e a partir disso a gente vai olhar 'ah, esse aqui já tem', aí coloca. 'Esse aqui tem', coloca. 'Ah, o que que falta nesse daqui', coloca."
- **Marcelo**: "Eu vejo isso em três níveis assim: primeiro, é um nível assim painel de controle, que é onde a gente vai acessar tudo. Segundo, são as páginas individuais onde a gente vai ver cada coisa: 'ah, aqui é planejador, aqui é financeiro, aqui é dashboard'. Terceiro, base de dados."

### Estrutura 4 camadas (aprovada com nome mantido "Conhecimento" após discussão)

- **Natália**: "em vez de começar por departamentos, começar pelas funções do negócio, porque aí... a gente define os responsáveis com departamento e pessoa. Porque aí você evita aquele erro de a empresa crescer, os departamentos mudarem e os processos permanecerem. Então se tudo tiver organizado pela estrutura organizacional, logo fica desatualizado."
- Camadas: **Gestão, Operação, Biblioteca, Conhecimento**
- Discussão sobre trocar "Conhecimento" por "Repositório de benchmarks" ou "Biblioteca" → **Natália**: "Conhecimento, quer dizer." (mantido o nome "Conhecimento")

### Estrutura replicável (multi-cliente ASL-I)
- **Natália**: "fazer o mais genérico possível. Pra atrelar ao projeto da Ju."
- **Marcelo**: "Como se fosse um um um padrão que a gente vai replicar pra qualquer projeto e as especificidades vêm depois."
- **Marcelo**: "tudo que a gente tá tentando fazer agora não faria nem sentido fazer de outro jeito, tem que ser assim mesmo."

## 2. Gestão (camada 1)

### Itens definidos
- **Natália**: "Gestão: tudo que serve para acompanhar a empresa: OKRs e metas, dashboard geral, KPIs, financeiro, fluxo de caixa, planejamento trimestral, organograma, reuniões, scorecard, roadmap de projetos."
- **Marcelo**: "Gestão: tudo que serve para comprar a empresa. Caixa, dashboards de ROI..."
- **Scorecard semanal**: **Natália**: "Tipo de pontuação. Tipo uma saúde semanal. 'Ah, essa semana está 10 de 10. Essa semana, ó, 6 de 10.'"
- **Track record**: **Natália**: "Track record faltou." (decisão: adicionar — virou item novo em v0.8)

### Diferenciação Gestão vs Operação
- **Marcelo**: "gestão seria, tudo que serve para acompanhar a empresa, então os OKRs, dashboard geral, KPIs, financeiro, fluxo de caixa, planejamento, organograma, reuniões, score semanal e tal. E operação é os processos, aí dentro de operação esse é o mais... Talvez a gente tava pensando antes só nessa parte da operação, que seria separando já em comercial, marketing, produto, sucesso do cliente, tráfego, financeiro, RH. Então, o operacional é essa parte que como se fosse os departamentos e o de gestão é o que olha para tudo."
- **Natália**: "Macro, né?"
- **Marcelo**: "dependendo da pessoa, ela não vai nem ter acesso ao de gestão, só o da operação. Tipo assim, a Roberta, ela não vai ter acesso à gestão. Ela vai ter acesso só à operação." (FUTURO: permissões por papel)

## 3. Operação (camada 2)

### 7 sub-áreas (aprovadas)
- **Marcelo**: "Comercial, marketing, produto, sucesso do cliente, tráfego, financeiro, RH. É isso, são sete."
- Discussão sobre mesclar: **Natália**: "Será que algum desses aí dá para entrar dentro do outro?"
- **Marcelo**: "Não. Assim, RH a gente meio que não tem, mas é bom porque ali tem manual de cultura, essas coisas."
- **Marcelo**: "Talvez, por exemplo, talvez tráfego pode estar dentro de marketing." (mantido separado)
- **Marcelo**: "Comercial, marketing, produto, sucesso do cliente. Talvez sucesso do cliente pode estar dentro de produto. Tráfego e financeiro e RH." (decisão final: 7 separados)

### Itens por sub-área

**Comercial**: CRM, pipeline, scripts, objeções, contratos, diagnóstico, fechamento

**Marketing**: **Natália**: "Marketing com calendário, estratégia, criativos, copies, bancos de anúncios, biblioteca de VSL, SEO, landing pages."

**Produto**: **Natália**: "Produto: mentoria, workshop, minicurso, comunidade, conteúdo das aulas, atualizações."

**Sucesso do Cliente**: **Natália**: "Sucesso do cliente com onboarding, atendimento, financeiro, cobrança, suporte, NPS, comunidade, eventos."

**Tráfego**: **Natália**: "Tráfego com meta, Google, TikTok, todo que for, com dashboards de tráfego, pixel, públicos, blá, criativos vencedores."

**Financeiro**: **Natália**: "Financeiro com receitas, custos, pagamentos, comissão, relatórios."

**RH**: **Marcelo/Natália**: "RH com SOPs, contratações, treinamentos, manual de cultura." / **Natália**: "Procedimento operacional padrão. Standard operation procedure." / **Marcelo**: "É documento com instruções passo a passo para padronizar tarefas rotineiras de uma empresa. É tipo o documento da Roberta, por exemplo."

### Financeiro: dois níveis (geral + por aluno)
- **Natália**: "porque, por exemplo, eu acho que precisa ter sim, por... dentro do financeiro. Tem que ter o financeiro geral que tem todo o o amontoado ali de tudo que entra, tudo que sai, toda a composição ali do financeiro, mas também vai ter que ter um sub com individuais. Ah, do workshop um, workshop dois, workshop três, direto por sessão a um, e isso e aquilo."
- **Natália**: "O financeiro de cada aluno, né? Fica separado?"
- **Gabriel**: "Fica, eu acho que fica no... no negócio do financeiro. De qualquer forma, acho que tem que constar lá a ficha de participação."
- **Natália**: "Isso, é que é isso que eu quis dizer. O acompanhamento de cada aluno seria aquela planilha de cada aluno?"

### Fontes de leads (métrica visível)
- **Natália**: "a gente precisa olhar pra ele e ver 'ah, entraram tantos, tantos são do workshop, tantos são do sessão a um, tantos são da... é da sessão a um mas veio da live, é da sessão a um mas veio do direct, do link da bio'."
- **Natália**: "Esses dados eles precisam estar visíveis em algum lugar, e eu sei que provavelmente eles estão em bancos de dados e planilhas agora, mas eles não estão visíveis pra... pra gente, pra... pra operação no dia a dia. Tem que ser aquela coisa assim 'ah, eu vou... se eu preciso desse dado eu pergunto e vocês vão conseguir trazer a resposta'."
- **Marcelo**: "Uhum."
- **Natália**: "Mas não é um dado que que está visível."

### Central de Produtos (não é uma camada, é um desdobramento)
- **Natália**: "Central de produtos ao invés de misturar tudo. Então Instituto Cronos, produtos, aí Mentoria, landing page, oferta, criativo, produto, dashboard. Workshop destrava shop, Eventos presenciais, Minicurso, Comunidade."
- **Natália**: "a gente ficou de fazer o outro presencial da Ju que não seja o de alunos, que ela fazia todo mês e tal, eu pedi para ela parar de fazer, mas a gente vai ter que fazer algum. E que seja maiorzinho e tal."
- Cada produto é um sub-container com seus materiais (landing page, oferta, criativo, produto, dashboard, etc).

### Operações (SOPs) — camada separada
- **Marcelo**: "Outra coisa que ele faria eh, uma área chamada Operações, onde vivem todos os SOPs."
- **Natália**: "Playbooks, isso. Ah, isso é legal, porque aí fica tudo ali que poderia ser algo consultável, né? Tipo assim, a pessoa pesquisa, aí ela não sabe nem onde procurar em cada, em qual que é o departamento que eu procuraria isso daqui. Então teria um que é só de desses negócios."
- **Marcelo**: "Como subir um anúncio? Como criar uma campanha? Como lançar o workshop? Como abrir carrinho? Como fazer onboarding? Isso é muito legal."

## 4. Biblioteca (camada 3)

### Itens
- **Marcelo**: "logotipos, brandbook, que inclusive já tem brandbook, gracinha. Fotos da Ju, vídeos b-roll, templates do Canva, fontes, assets, documentos jurídicos, contrato, certificado."
- **Natália**: "Sem edição, né, tipo, na íntegra, só o b-roll." (sobre vídeos b-roll)
- **Marcelo**: "São imagens suplementares ou alternativas intercaladas com a cena principal. É tipo uma VSL que vai passar um monte de vidinho no meio, sabe?"
- **Marcelo**: "Você está falando: 'Ah, quando você toma o café da manhã...' Aí aparece um velho bebendo a xícara e já acorda. Isso é um b-roll."
- **Natália**: "Ou seja, coisas para consulta. E isso aqui, por exemplo, o contrato, não é o contrato do aluno fulano, mas é o contrato base. Coisa assim."

## 5. Conhecimento (camada 4)

### Itens
- **Natália**: "a área de conhecimento, que seria a parte que quase ninguém faz. Tudo que a empresa aprendeu. Exemplos: testes de anúncios, criativos vencedores, headlines vencedoras, CPLs históricos, benchmarks. Eu acho que aqui vai entrar muito a questão de histórico mesmo, né? Não é um conhecimento, tipo assim, o que que a gente aprende, mas o que a gente aprendeu com o projeto, tudo que for... tipo um, um, uma documentação mesmo do que já aconteceu. Aprendizado de lançamentos, relatórios pós-eventos, tipo assim, é todo... isso aqui, um absurdo que a gente nunca fez. Um, um debriefão dos lançamentos."
- **Marcelo**: "Biblioteca de benchmarking."
- Itens finais: testes de anúncios, criativos vencedores, headlines vencedoras, CPLs históricos, benchmarks, aprendizado de lançamentos, relatórios pós-eventos, pesquisa com alunos, ICP atualizado, objeções novas.

## 6. Como o painel vai funcionar

### Decisão: links externos, não documentos internos
- **Marcelo**: "ele não precisa ser interno dentro do sistema ali. Ele pode ser só o acesso. A questão é, ali tem que ter, eu consigo chegar nessa planilha."
- **Natália**: "imagino que muita coisa, sei lá, dash financeiro, seja uma, um sistema à parte que aí dentro dessa coisa vai estar linkado, né? Tipo, entra ali no financeiro, clica no link e abre um sistema, porque eu imagino que o tanto de coisa que está envolvido não dá para colocar tudo no projeto só, senão quebra tudo, lasca tudo, né?"
- **Marcelo**: "Não, tudo que é ferra- por isso que eu falei, é a gente olhar para tudo e falar: esse aqui a gente já tem, esse aqui a gente já tem, se já tem, é um link."
- **Natália**: "talvez a gente não precisa colocar o documento lá, coloca o link do Drive. Coloca o link do Drive, não, coloca um botãozinho lá que você clica e cai no Drive, por exemplo."
- **Marcelo**: "Pela experiência que eu tive, naquele HTML lá do roteiros, que não... ontem não tava abrindo a apresentação, ele estava dentro lá do GitHub lá, na base."
- **Marcelo**: "Talvez pelo Drive seja um pouco mais seguro. Não, aí a partir do momento que eu fui lá, mudei o código, coloquei pro pro Drive, nunca mais vai ter esse problema. A pessoa vai clicar e vai cair no Drive."
- **Marcelo**: "Fora que, tipo, se tá interno, é 300 documentos que uma hora ou outra pode dar pau em algum, alguma coisa. Se tá externo, é só se o Drive cair. Mas se o Drive cair, aí a humanidade já foi extinta e aí a gente já vai ter outras preocupações, não é?"

### Decisão: visualizador interno pra playbooks, link externo pra resto
- **Marcelo**: "Uma coisa que eu acho que não é legal ter só o link seria, por exemplo, os playbooks. E playbook já tem muitos lá daqueles, por exemplo, do da CS, tudo, meio que já tem vários lá na naquele negócio que a Lê fez. Então, talvez, só baixa e sobe de novo no nosso."
- **Marcelo**: "Tô pensando se isso não pode pesar as coisas. Porque, qual que é a diferença entre ter o documento lá pra gente acessar e visualizar lá, ou de ter um botão pra pessoa pra gente clicar e abrir uma nova aba e aparecer o mesmo documento?"
- **Gabriel**: "Eu acho que talvez dê pra colocar algum tipo de função que você consiga até clicar num num botão dentro lá do desse sistema em que você posta uma coisa como se fosse um post mesmo, sabe? Eu não sei como é que esses playbooks eles estão, se são PDFs e tals, se são documentos de Word. Porque se for documento de Word é mais fácil da gente copiar e colar lá dentro, já fica ali como se fosse um post, numa comunidade..."

## 7. Estratégia Comercial

### Ancoragem de preço (R$15k → R$12k)
- **Marcelo**: "A apresentação que você tá usando tá com a ancoragem?"
- **Natália**: "Tá sim. De 15 mil, né?"
- **Marcelo**: "Eu já vou mudar a entrada já, já, já coloco. 15 mil, mas hoje aqui comigo a gente tem uma oferta especial pra você e esse valor é de R$ 12.000,00. Ou você tem esse valor à vista?"
- **Marcelo**: "Esse é o valor, R$ 12.000,00. Você tem esse valor à vista? Ah, eu não tenho, não sei o quê. Quanto você tem à vista? Quanto você poderia pagar à vista desse valor? Ah, eu poderia pagar 2 mil. Ah, ótimo. E limite no cartão de crédito, você tem?"

### Desconto à vista (R$2k)
- **Marcelo**: "No nosso caso, o desconto do parcelamento é 2 mil, né? Te dando R$ 2.000,00 de desconto, eu tiro todo o juros pra você. Talvez nem falar de juros, né? Não, não é juros... Juros? É desconto."

### Limite de cartão + Pix = total
- **Marcelo**: "O 10, que é o valor do à vista. Lembra que a gente falava 'Mil de entrada mais 9 mil à vista?' Não é 9 mil, é 10."

### Cash collect 50% no primeiro mês
- **Marcelo**: "A gente tem que, assim, tentar o máximo de, que eles chamam de cash collect, né, que é esse, essa coleta inicial nos primeiros 30 dias, o máximo que a gente conseguir. Aí, é porque ontem a gente teve um plantão de dúvidas só de comercial. Só de vendas. E aí, eu perguntei sobre isso, né? E aí ele trouxe isso, que eles aumentaram de eu tipo mandei, né, meu bem, de quanto? Cinco para 52% de recebimento no primeiro mês. Porque antes o receb, imagina lá, né, o valor que é o, a mentoria, eles tinham a aplicação e no máximo uma parcela da pessoa no primeiro mês, e eles conseguiram puxar para 50% do valor de contrato pro primeiro mês."
- **Natália**: "É muito vantajoso."

### Plataforma Asas (substitui Zouti/Hotmart)
- Discussão detalhada sobre Asas como plataforma de pagamento
- **Marcelo**: "tem duas coisas lá, né, na, no. Gente, é impressionante o como eu não consigo uma linha, eu tenho um monte de aspas no meio de tudo que eu tô falando. Mas enfim. Aspas não, parênteses, né? Eh lá tem MasterMind e mentoria. Ontem era um plantão da mentoria. E aí, ele, na mentoria, normalmente não é um, você não pode trazer coisas muito complexas, porque a maioria das pessoas estão começando, primeiro produto, muitos, o perfil ideal do, do FHT, nem é quem já é do digital."
- **Marcelo**: "Ó, isso aqui, usem com sabedoria, não é algo que eu traria normalmente aqui num, num plantão de, da mentoria, mas vamos lá. Ele falou: 'Ó, ó, hoje, dentro dessa estrutura, se você não tem nada, você não sabe isso e aquilo, beleza, usa lá a Hotmart, e vai parcelar, e não sei quê, do jeito que é.' Aí eu falei: 'Nossa, e a gente nem Hotmart usa, a gente já usa uma coisa que tem uma taxa mais baixa. Mas, mesmo assim, ainda é muito inviável.' Aí, ele falou do negócio, que foi aquilo, não sei se vocês viram eu perguntei lá no grupo ontem da, da Zouti, se tem a opção de fazer, como que chama o, o negócio? de não ter a obrigatoriedade da antecip- eh eh sem antecipação compulsória."
- **Marcelo**: "Ele falou exatamente isso: 'Olha, eu não usaria uma plataforma que me obrigue a fazer essa antecipação, porque é nessa antecipação que eles ganham tanto.' Vocês viram, fica mai- acho que 20% fica em taxas, porque eles adiantam. Então, assim, é você pensar que se uma pessoa pagar em 10 vezes, a empresa lá, quem recebe o dinheiro dela, vai receber em 10 vezes, porque é quando ela coloca o dinheiro. Se eles estão adiantando pra gente, que é o que acontece, a gente recebe o crédito em quantos dias?"
- **Marcelo**: "Acho que o crédito é sete dias. A gente recebe em sete dias. Como que a gente recebe em sete dias uma coisa que eles vão receber em 10 meses? É eles adiantando, e pra eles adiantarem, eles cobram caro por isso. Então, se a gente tem uma plataforma, uma, um sistema, a gente use de algum sistema que não nos obrigue a fazer essa antecipação, a gente vai receber conforme eles a pessoa pagar, então ela pagou em 10 vezes, eu recebo em 10 vezes."
- **Marcelo**: "Nesse caso aqui, fazendo uma, uma, recebendo do jeito dele. Ó, tá vendo? Cre- R$ 10.000 seria o parcelamento, crédito em 10 vezes, ele tem o- as taxas variam nessa, nessa plataforma aqui, que foi uma que ele indicou. Eh tipo assim, em à vista é uma taxa, de um a ce- de duas, sei lá, uma a seis vezes é outra taxa, de sete a 12 é outra, de de 13 a não sei quantos, é outra. Então varia nisso. Essa taxa de 3.99, que é a nossa taxa na Zouti hoje, exatamente a mesma, eh seria em 10 vezes. Se que é a mesma em até acho que 12 vezes é a mesma taxa, esse 3.99 mais R$ 0,50."
- **Marcelo**: "O boleto bancário R$ 1,99 por transação. Real, né? É. Não é porcentagem, é R$ 1,99. Então imagina uma aplicação que a gente paga, é... Dá uma agonia, R$ 1,99 real. É. R$ 1,99 reais. Ainda é R$ 1,00, entendeu?"
- **Marcelo**: "Só que aí a gente já vai deixar de ter essa aplicação. E aí, no por exemplo, no workshop não vai fazer sentido a gente colocar, vai ter que continuar com as outras, pagando mais mesmo, porque não é direto, né, é um para muitos."

### Aplicação só pra evento (não pra mentoria)
- **Marcelo**: "Ah, inclusive, a gente precisa fazer as alterações já. Eu ia chamar vocês antes para falar. Eh, inclusive, lá na na apresentação, que que é o ponto? Eh, a gente tentar não fazer eh... tirar aquele negócio de aplicação. Aplicação ser uma coisa só pra evento, de um para muitos."

## 8. Automações

### Redirecionar para workshop vigente
- (próximas etapas): "Reconfigurar automações: Reconectar as automações pausadas para que todos os gatilhos e checklists conduzam para a ação vigente do workshop, exceto se forem relacionados à mentoria."

## 9. Ferramentas de Documentação

### Documentação VSL como referência
- **Natália**: "De preferência uma documentação da VSL, que é sempre a mais elogiada. Ela fala assim: 'Olha, lê a documentação aí da VSL, e se inspire nela, siga, siga o método dessa documentação, alguma coisa assim, tá?'"
- **Marcelo**: "E sempre se ligar no ponto de pedir pra IA documentar e documentar e documentar. Saiu o deploy, você fala: 'Documenta'. Seguindo o padrão dos outros, é só pedir pra ler a documentação no no GitHub."

### Embelezamento por IA especializada (NÃO mexer agora)
- **Marcelo**: "Eu estava pensando, justamente nisso, depois que a gente terminar essas ferramentas passar em uma outra IA de embeleza, embeleza... Embelezamento. Acho que é uma boa ideia, contando que ela não regace com o HTML."
- **Natália**: "Sim, esse é meu medo."
- (Implicação: não passar o HTML por IA de embelezamento agora; terminar primeiro, depois passar.)

## 10. Comentários organizacionais (a manter)

### Não pode ficar muito complexo
- **Marcelo**: "Tipo assim, não pode ficar muito complexo demais."
- **Marcelo**: "Eu acho que não, eu acho que isso aqui, nossa, para mim, eu olhei e falei: nossa, isso aqui vai simplificar demais. Você não acha?"
- **Natália**: "Isso aí é pensando na IA, entendeu? Que vai construir."

### Simplicidade > complexidade
- **Natália**: "dentro de cada um deles vai ter, não vai ter 100.000 coisas, às vezes vai ser um, três, três documentos e, não é? O que que tem de sucesso do cliente? Não tem 70 pastas. E outra coisa, né? Você costuma usar depois, fica automático também."

### UX: barra de pesquisa
- **Marcelo**: "com a barra de pesquisa pra poder pesquisar um... alguma coisa assim. Eh, assim, nesse sentido que a gente tá buscando fazer. Eu acho que é super, plenamente viável da gente fazer isso."

---

## Resumo executivo (pra STATUS.md e CHANGELOG)

**Decisões de arquitetura**:
1. 4 camadas + Central de Produtos + SOPs (mantido)
2. Nome "Conhecimento" mantido
3. 7 sub-áreas de Operação separadas
4. Links externos, não documentos (playbooks são exceção)
5. Estrutura replicável entre projetos ASL-I
6. Toda sub-área segue: dashboard, planejamento, processos, execução

**Decisões de conteúdo**:
7. Track record adicionado em Gestão
8. Workshops (comparecimento, retenção, conversão) em Conhecimento
9. Origem dos leads como métrica visível
10. Aplicação só pra evento
11. Financeiro em 2 níveis (geral + individual)

**Decisões de comercial**:
12. Ancoragem R$ 15k → R$ 12k (interno, não vai pro painel)
13. Cash collect 50% no 1º mês (interno)
14. Migração Zouti → Asas (3,99% + R$ 0,50, sem antecipação compulsória)
15. Aplicação só pra evento (1-para-muitos), não pra mentoria

**Processo**:
16. Embelezamento por IA especializada é pra depois
17. Sempre documentar após deploy (padrão VSL)
18. Doc VSL como modelo
19. Reconfigurar automações ManyChat pós-reunião
