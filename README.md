# Landing page — I Maratona de Programação UCDBits

Página de divulgação da **I Maratona de Programação UCDBits**, competição de programação em equipes
da Universidade Católica Dom Bosco (UCDB), em Campo Grande – MS, nos dias **4 e 5 de dezembro de 2026**.

A página apresenta o evento, a programação, as categorias e os links para inscrição (Even3) e para o edital em PDF.

## Estrutura

```
.
├── README.md
└── landing/
    ├── index.html                          # página única (HTML + CSS + JS inline)
    └── assets/
        ├── logo_ucdbits.svg                # logo do evento (abertura)
        ├── logo_ucdb.svg                   # logo da universidade (topo e rodapé)
        └── edital-i-maratona-ucdbits.pdf   # edital oficial
```

Site estático, sem build, sem dependências e sem framework. As únicas requisições externas são as
fontes do Google Fonts (Allura, Archivo e JetBrains Mono).

## Como rodar localmente

Basta abrir `landing/index.html` no navegador. Para servir via HTTP (recomendado, evita diferenças
de comportamento com `file://`):

```bash
cd landing
python -m http.server 8000
# acesse http://localhost:8000
```

## Seções da página

| Seção | Conteúdo |
|---|---|
| Topo | Logo da UCDB e localização |
| Abertura | Logo UCDBits, título, data/local, botões de inscrição e edital, prazo |
| Sobre | Formato da prova (padrão Maratona SBC/ICPC), números (3 por equipe, 7 problemas, 3 h, 1 computador) e os balões A–G |
| Programação | Cronograma de sexta (treino livre) e sábado (credenciamento, prova, premiação) |
| Inscrições | Período, regras de inscrição e categorias (Geral, Feminina, Café com Leite) |
| Rodapé | Realização e links do evento |
| Barra fixa (celular) | Botões de inscrição/edital que aparecem quando os botões da abertura saem da tela |

## Como editar

Todo o conteúdo está em `landing/index.html`.

- **Link de inscrição** — a URL do Even3 aparece em **4 lugares** (abertura, seção Inscrições, rodapé e
  barra fixa). Ao trocar, procure por `even3.com.br` e atualize todas as ocorrências.
- **Edital** — substitua `landing/assets/edital-i-maratona-ucdbits.pdf` mantendo o mesmo nome, ou
  atualize os 4 links que apontam para ele.
- **Datas e horários** — ficam no bloco `.quando` (abertura), no parágrafo `.prazo`, na seção
  Programação (`.dia`) e em `.datas-insc`. Atualize também a `<meta name="description">`.
- **Cores e fontes** — definidas como variáveis CSS em `:root` (`--papel`, `--tinta`, `--azul`,
  `--amarelo`, `--ucdb`, `--f-texto` etc.), derivadas do logo UCDBits. As cores dos balões A–G estão
  inline em cada `<span class="balao">`.

## Responsividade e acessibilidade

- Pontos de quebra: até **720px** (celular, coluna única e barra fixa inferior) e **721–980px** (tablet).
- Respeita `safe-area-inset` (telas com notch) e `prefers-reduced-motion`.
- Seções com `aria-labelledby`, imagens com `alt`, foco visível nos botões.
- A barra fixa usa `IntersectionObserver`; em navegadores sem suporte ela fica sempre visível.

## Publicação

Por ser estática, a pasta `landing/` pode ser publicada como está em qualquer hospedagem de arquivos
(GitHub Pages, Netlify, servidor da universidade etc.). Os caminhos dos assets são relativos, então a
página funciona em subdiretórios.
