# Para a professora Roberta

Homenagem de Dia do Professor (15 de outubro de 2026) para a Roberta Oliveira, professora do ensino fundamental.

A página é uma lousa: o texto vai sendo escrito a giz, palavra por palavra, com o giz acompanhando a mão, e um apagador limpa o quadro entre uma "aula" e outra.

**Ver online:** _adicione o link depois do deploy_

## O que tem na lousa

1. **Abertura:** a data no alto, como em qualquer sala de aula, e o nome dela com uma estrelinha desenhada a giz.
2. **Aula 1, Português:** o verbete "pro·fes·so·ra".
3. **Aula 2, Matemática:** um problema sobre quantos "bom dia, professora!" ela responde por ano.
4. **Aula 3, Ciências:** um experimento observando a professora depois da aula.
5. **Aula 4, História:** sobre a história que ela ajuda a escrever.
6. **Dever de casa:** a mensagem final, com um coração desenhado.

Tocar na lousa durante a escrita mostra o texto inteiro de uma vez. Tocar depois que terminou apaga o quadro e passa para a próxima aula. No teclado, espaço, Enter ou → fazem o mesmo.

## Como foi feito

Um único `index.html`, sem build e sem dependências: HTML, CSS e JavaScript puro, com a fonte [Caveat](https://fonts.google.com/specimen/Caveat) do Google Fonts.

- **Escrita palavra por palavra:** o JavaScript quebra o texto de cada lousa em palavras e revela cada uma com `clip-path` pela Web Animations API. Cada frase vira uma sequência agendada de uma vez, e o giz segue as palavras numa única animação.
- **Textura do giz:** uma `mask-image` com ruído SVG (`feTurbulence`) deixa as falhas no traço. Por ser uma imagem, o navegador calcula o ruído uma vez, não a cada quadro.
- **Desenhos:** a estrela e o coração são `path` SVG traçados com `stroke-dashoffset`, e o giz acompanha o traço com `getPointAtLength`.
- **Resto de giz:** ao apagar, uma cópia bem apagadinha da lousa fica no fundo, como numa lousa de verdade.
- **Celular:** o tamanho do texto se ajusta à tela, e no celular em pé a letra fica maior para aproveitar a altura.
- **Acessibilidade:** com `prefers-reduced-motion` ativado, o texto aparece direto, sem animação.

## Rodando localmente

Basta abrir o `index.html` no navegador. Se preferir um servidor local:

```bash
npx serve .
```

## Editando os textos

Cada `<section class="aula">` no `index.html` é uma lousa. É só escrever o texto normalmente, porque o JavaScript separa as palavras sozinho.

```html
<section class="aula" hidden>
  <header class="cabecalho"><span class="materia">Aula 5 · Geografia</span></header>
  <span class="risco"></span>
  <p>Texto da lousa, com <span class="amarelo">giz amarelo</span> onde quiser.</p>
</section>
```

- **Cores de giz:** `amarelo`, `rosa` e `azul` (o padrão é branco).
- **Traço sob o título:** `<span class="risco"></span>`.
- **Nova lousa:** copie uma `section` e mantenha o atributo `hidden`, porque só a primeira lousa começa visível. A ordem no HTML é a ordem das aulas.

## Deploy na Vercel

Como é um site estático, não precisa de configuração.

- **Pelo GitHub:** importe o repositório em [vercel.com/new](https://vercel.com/new), deixe o Framework Preset como **Other** e publique.
- **Pela linha de comando:** dentro da pasta do projeto, rode `npx vercel --prod`.

---

Feito pelo Víctor César, com muito carinho, para a Roberta.
