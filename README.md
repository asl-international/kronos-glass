# Instituto Kronos · Painel — Layout Glassmorphism

Hub agregador do Instituto Kronos num único arquivo HTML.

- **Versão**: v0.13-teste · Layout Glassmorphism
- **Inspiração**: Apple Vision Pro / iOS 26 — frosted glass (backdrop-filter blur 20px), gradiente radial pink/purple no fundo, glow shadows no hover, bordas com luz
- **Conteúdo**: 6 camadas (Gestão/Operação/Produtos/SOPs/Biblioteca/Conhecimento) + 7 sub-áreas de Operação + 5 produtos + Playbook Mentoria Kairós com 10 notas
- **Persistência**: localStorage (`kronos_state_v1`)

## Como rodar

```bash
python -m http.server 8000
# abrir http://localhost:8000
```

Single-file, sem build, sem dependências. Funciona offline.

## Funcionalidades

- Frosted glass em todos os cards (backdrop-filter blur forte)
- Gradiente radial pink/purple no background
- Glow shadows rosa no hover dos items
- Tipografia Space Grotesk display + Inter body + IBM Plex Mono
- Botão primário com gradient pink→roxo
- Busca com stemmer + 200+ sinônimos
- Botão Resumo (todos os links/docs/notas em uma página)
- 4 abas: Gestão / Operação / Produtos / SOPs / Biblioteca / Conhecimento
