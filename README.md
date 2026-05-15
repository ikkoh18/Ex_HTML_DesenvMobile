# HABIT — Projeto de Interface HTML/CSS

Reconstrução fiel das telas do sistema **HABIT** a partir dos mockups fornecidos no PDF do exercício.

---

## Telas Implementadas

| Arquivo | Tela |
|---|---|
| `index.html` | Home — hero, categorias populares, todas as categorias, postagens em destaque, escolhas do editor |
| `listagem.html` | Listagem de categoria (Techno) com filtros e grid de cards |
| `destaques.html` | Página de destaques com grid de 9 cards |
| `assinar.html` | Formulário de assinatura da newsletter |
| `busca.html` | Resultados de busca |
| `entrar.html` | Login (e-mail + senha + entrar com Google) |
| `criar-conta.html` | Cadastro de novo usuário |
| `perfil.html` | Perfil do usuário com suas postagens |
| `admin-categorias.html` | Admin — gerenciar categorias |
| `admin-criar-post.html` | Admin — criar novo post |
| `admin-escolhas-editor.html` | Admin — escolhas do editor |
| `admin-usuarios.html` | Admin — gerenciar usuários |
| `admin-fila-revisao.html` | Admin — fila de revisão de posts |
| `admin-fila-comentarios.html` | Admin — fila de revisão de comentários |

---

## Estrutura do Projeto

```
habit-project/
├── index.html
├── listagem.html
├── destaques.html
├── assinar.html
├── busca.html
├── entrar.html
├── criar-conta.html
├── perfil.html
├── admin-categorias.html
├── admin-criar-post.html
├── admin-escolhas-editor.html
├── admin-usuarios.html
├── admin-fila-revisao.html
├── admin-fila-comentarios.html
├── css/
│   └── styles.css
├── assets/
│   └── (imagens — placeholders utilizados via CSS)
└── README.md
```

---

## Decisões de Layout

- **CSS Grid** para o layout geral das páginas admin (sidebar + conteúdo), grid de cards, categorias e footer.
- **Flexbox** para header, botões inline, post cards horizontais e ações de tabela.
- **Sem frameworks** — CSS puro conforme requisito do exercício.
- Paleta extraída diretamente dos mockups: teal `#1a7a6a` como cor primária, laranja-avermelhado `#e05c3a` para o link Admin, cinza `#6b7380` para textos secundários.
- Placeholders de imagem implementados via `background-color` em elementos com classe `.img-placeholder`, evitando dependência de arquivos externos.
- Variáveis CSS em `:root` para cores, tipografia e espaçamento.

---

## Breakpoints Utilizados

| Dispositivo | Breakpoint |
|---|---|
| Celulares pequenos (base) | ≤ 420px |
| Celulares médios/grandes | 481px – 767px |
| Tablets | 768px |
| Notebooks/desktops | 1024px |
| Monitores grandes | 1440px |

Estratégia **mobile-first**: o CSS base cobre telas ≤ 420px e `@media (min-width: …)` expande o layout progressivamente.

---

## Observações de Acessibilidade

- Tags semânticas em todas as páginas: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`.
- Hierarquia de títulos correta: `h1` único por página, seguido de `h2` e `h3`.
- Todos os `<input>` possuem `<label>` vinculado via `for`/`id` (labels com `class="sr-only"` quando o placeholder é suficiente visualmente, mas o label ainda existe para leitores de tela).
- `type` correto em todos os inputs: `email`, `password`, `search`, `text`, `checkbox`.
- `aria-label` em elementos sem texto visível (ícones, placeholders de imagem).
- `aria-current="page"` no link ativo de navegação.
- `role="img"` nos placeholders de imagem com `aria-label` descritivo.
- Contraste entre texto `#1e2329` e fundo branco `#ffffff`: **>** 14:1 (WCAG AA ✔).
- Contraste entre texto mutado `#6b7380` e fundo branco: ≈ 5.1:1 (WCAG AA ✔).
- Estados de foco visíveis: `outline: 2px solid var(--color-primary)` em todos os elementos interativos via `:focus-visible`.
- `:hover` e `:disabled` estilizados em botões e links.
- Tabelas admin com `<thead>`, `<th scope="col">` para leitores de tela.
- `role="tablist"` e `aria-selected` nos filtros de categoria.
