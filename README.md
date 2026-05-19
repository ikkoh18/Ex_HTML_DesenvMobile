# Exercicio HTML/CSS Desenvolvimento Mobile

## Telas Implementadas

O projeto reconstrói fielmente 14 telas a partir dos mockups fornecidos no PDF do exercício. As telas públicas são: Home (`index.html`), Listagem de categoria (`listagem.html`), Destaques (`destaques.html`), Assinar newsletter (`assinar.html`), Resultados de busca (`busca.html`), Login (`entrar.html`), Criar conta (`criar-conta.html`) e Perfil do usuário (`perfil.html`). As telas administrativas são: Categorias (`admin-categorias.html`), Criar Post (`admin-criar-post.html`), Escolhas do Editor (`admin-escolhas-editor.html`), Usuários (`admin-usuarios.html`), Fila de revisão (`admin-fila-revisao.html`) e Fila de comentários (`admin-fila-comentarios.html`).

---

## Decisões de Layout

O layout foi construído inteiramente com CSS puro, sem o uso de frameworks como Bootstrap ou Tailwind, conforme exigido pelo exercício.

Para a estrutura das páginas, utilizamos CSS Grid nos casos em que o layout envolve múltiplas colunas independentes, como o grid de cards (listagem e destaques), o painel administrativo com sidebar à esquerda e conteúdo à direita, a grade de categorias da home e o rodapé. O Flexbox foi utilizado para componentes lineares, como o header, os botões agrupados, os cards horizontais de postagem e as ações das tabelas.

Todas as cores, tamanhos de fonte e espaçamentos estão definidos como variáveis CSS no seletor `:root`. Isso garante consistência visual em todo o projeto e facilita qualquer alteração futura, já que basta modificar o valor da variável para que a mudança se propague automaticamente. A escala tipográfica segue os valores recomendados no enunciado (h1 em 2.5rem, h2 em 2rem, h3 em 1.5rem, body em 1rem e small em 0.875rem), e a escala de espaçamento usa tokens nomeados de `xs` a `2xl`.

Como o projeto não possui imagens reais, os placeholders de imagem foram implementados diretamente via CSS usando `background-color`, sem nenhuma dependência de arquivo externo.

---

## Breakpoints Utilizados

A abordagem adotada foi mobile-first: o CSS base cobre telas de até 420px, e os estilos para telas maiores são adicionados progressivamente com `@media (min-width: …)`.

O breakpoint de 420px é o ponto de partida para celulares pequenos, onde o layout é de coluna única, a navegação quebra linha e o campo de busca ocupa a largura total. Em 481px, o grid de cards passa para duas colunas e o footer reduz de cinco para três colunas. Em 768px, o hero recupera sua segunda coluna para a imagem e o grid de categorias populares volta a três colunas. Em 1024px, o grid de cards passa para três colunas e o layout de postagens em destaque recupera a sidebar lateral. Em 1440px, o container central é levemente alargado para aproveitar melhor monitores grandes.

---

## Observações de Acessibilidade

A acessibilidade foi tratada como requisito ao longo de todo o desenvolvimento, não como um passo adicional.

Todas as páginas utilizam tags semânticas corretas: `<header>` para o cabeçalho, `<nav>` para os menus de navegação, `<main>` para o conteúdo principal, `<section>` para blocos temáticos, `<article>` para cards e postagens individuais, `<aside>` para conteúdo complementar e `<footer>` para o rodapé. A hierarquia de títulos é respeitada em todas as páginas: cada página possui um único `<h1>`, seguido de `<h2>` para seções e `<h3>` para subseções.

Todos os campos de formulário possuem um `<label>` vinculado via `for`/`id`. Nos casos em que o placeholder já comunica visualmente o propósito do campo, o label recebe a classe `.sr-only`, que o torna invisível na tela mas mantém o texto acessível para leitores de tela. O atributo `type` foi definido corretamente em todos os inputs (`email`, `password`, `search`, `text`, `checkbox`), o que ativa os teclados adequados em dispositivos móveis e melhora a validação nativa do navegador.

Elementos sem texto visível receberam `aria-label` descritivo, incluindo os placeholders de imagem, os campos de busca e os ícones de ação. O link ativo na navegação recebe `aria-current="page"`. As tabelas administrativas utilizam `<thead>` com `th scope="col"` para que leitores de tela consigam associar os dados às colunas corretamente.

O contraste entre o texto principal (`#1e2329`) e o fundo branco supera 14:1, bem acima do mínimo de 4.5:1 exigido pelo nível AA da WCAG 2.1. O texto secundário (`#6b7380`) mantém contraste de aproximadamente 5.1:1, também dentro do padrão. Todos os elementos interativos possuem estado de foco visível implementado via `:focus-visible`, garantindo navegação por teclado funcional em todo o projeto.
