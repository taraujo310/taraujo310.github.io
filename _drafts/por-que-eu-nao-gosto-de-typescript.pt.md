---
layout: post
title: Porquê eu não gosto de TypeScript
author: Thiago Ururay
image: js-vs-ts.png
comments: false
lang: pt
tags:
  [
    'TypeScript',
    'JavaScript',
    'Type Checking',
    'Linguagens de Programação',
    'Opinion',
  ]
---

## O Problema

Recentemente vi um tweet, no X, explicando porque o método `Object.keys()` tem retorno do tipo `string[]` em sua assinatura no TypeScript.

Em outras palavras, um objeto em TypeScript deveria ter todos as suas propriedades com tipos conhecidos. Mas há situações em que é possível adicionar propriedades desconhecidas em um objeto. Por não conseguir ter certeza sobre a presença de propriedades desconhecidas, o TypeScript adota uma posição defensiva para dar conta desses casos.

Eu não julgo essa posição defensiva pois é sabido que em qualquer software, precisamos avaliar os tradeoffs e tomar decisões que melhor se alinham com o seu objetivo.

Um outro usuário questiona por que o TypeScript não segue o comportamento padrão já definido pelo JavaScript, permitindo strings como chaves por padrão. Afinal, com TypeScript, um desenvolvedor poderia forçar uma tipificação mais rígida, caso quisesse. Essa é a questão central do debate.

<div class='twitter-element'>
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">The annoying part that isn&#39;t explained is why disallow using string as index signature for objects? <br><br>If you can&#39;t tell if object has hidden keys, then allow string indices by default.<br><br>If users want more rigid types they can cast to them.</p>&mdash; 𝕃𝕏𝔼 • e/acc (@lxe) <a href="https://twitter.com/lxe/status/1819062897936683272?ref_src=twsrc%5Etfw">August 1, 2024</a></blockquote>
<p class='twitter-caption'>
  Element implicity has an `any` type because expression of type `string` can’t be used to index type `{ a: number; b: number; }`.<br />
  No index signature with a parameter of type `string` was found on type `{ a: number; b: number; }`.
</p>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

## Por quê JavaScript é dinâmicamente tipado?

Aqui neste blog tem outro artigo defindo o que é checagem de tipos, tipagem dinâmica, estática, e os prós e contras de cada um. Se você não conhece esses conceitos ou os prós e contras, aconselho a dar um corre lá antes de continuar.

Gosto não se discute, cada cabeça tem sua sentença. É uma questão de preferência pessoal. Mas é importante reconhecer que a tipagem dinâmica oferece maior flexibilidade, o que pode ser vantajoso em determinados contextos.

Quando JavaScript foi projetado, a conexão com a internet era lenta e fraca e qualquer interação com uma página precisava do recarregamento da página. Imagina preencher um formulário e enviar os dados, demorar minutos para ter uma resposta (e até arriscar perder a conexão e, consequemente os dados) só para descobrir que algo estava inválido.

Para isso, a Netscape decidiu criar uma linguagem de script que permitisse uma interação com páginas web diretamente no navegador. Assim nasceu o Mocha, depois LiveScript e depois JavaScript.

JavaScript foi projetada para ser uma linguagem que

- pudesse interagir com a árvore DOM, que é altamente dinâmica;
- ser fácil de ler e escrever até por programadores inexperientes;
- pra ser simples, um código rapidamente escrito;
- precisava poder ser interpretado pelo navegador (i.e., sem compilação);
- ser muito tolerante a erros do programador.

Esses objetivos alinham com tipagem dinâmica, afinal, ela resulta em um código mais simples, conciso, de fácil leitura e entendimento e que lida muito bem com coisas que mudam (como a árvore DOM), além de não haver o processo de compilação.

## Por que utilizar TypeScript (ou outro type checker)?

Com o passar do tempo, os sites ficaram maiores e mais complexos. Desenvolvedores passaram a procurar por alternativas que

- reduzissem as possibilidades de erros em tempo de execução (capturando eles antes);
- recursos como autocomplete e navegação de código que são facilitados pelo amarração de tipos;
- explicitação de como difentes partes do código integram entre si;
- amarrasse a arquitetura de sistemas complexos, prevenindo erros humanos (principalmente de desenvolvedores iniciantes).

## Entendendo o mercado de software atual

A popularidade do TypeScript cresceu significativamente nos últimos anos e isso faz todo sentido! Ao longo da última década vivemos crises econômicas e a ascensão do trabalho remoto. Houve um aumento significativo de cursos vendendo uma ilusão financeira no curto prazo e, com isso, muitas pessoas enxergaram no desenvolvimento de software uma saída para suas finanças pessoais e migraram para a área. Isso resultou na entrada de muitos programadores inexperientes e na necessidade de proteger o software de erros humanos.

Paralelamente a isso, os softwares ficaram cada vez mais complexos, necessitando de maior robustez e performance. Algo que a tipagem estática gera uma maior sensação de segurança.

E apesar de esses serem bons motivos para a adoção de uma linguagem com tipagem estática, frequentemente vejo argumentos menos atraentes e que focam em gostos pessoais ou apenas na prevenção de erros.

## TypeScript vs JavaScript

Para debater sobre isso com fundamentos, vou fazer uma breve comparação entre TypeScript e JavaScript e depois debater o porquê eu evito escolher TypeScript, se isso for possível.

O TypeScript...

- Transpila o código para JavaScript onde não há definição de tipos. Sendo assim, todo o sistema de tipos se perde em tempo de execução, perdendo a garantia da prevenção de erros;
- É um super-conjunto do JavaScript e por isso sua performance só pode ser tão boa quanto a do próprio JavaScript;
- Continua sendo uma dependência a ser gerenciada, podendo gerar conflito de versão, necessidade de manutenção (breaking change hell), aumentar o tamanho do projeto, etc. Gerenciar dependências requer tempo e recursos;
- Muitas vezes, a tipagem estática leva a um código burocrático, aumentando a verbosidade, especialmente em projetos menores ou com requisitos menos complexos;
- Apesar de prevenir erros de sintaxe e semântica, não impede erros lógicos. Para isso, se fazem necessárias outras técnicas como testes unitários e de integração, seguir convenções de estilo de código usando linters, ativamente manter uma documentação, ter um CI/CD configurado, entre outras coisas que são padrões em comunidades de desenvolvimento de linguagens dinâmicas.

## Conclusão

Ou seja, as vantagens do TypeScript são principalmente sobre a experiência do desenvolvedor. Isto é, aumenta as ferramentas da linguagem (classes, tipos, interfaces, etc.), aumenta as ferramentas de editores de texto (refactoring automático, autocomplete, etc.), documentação diretamente no código (a declaração de variável explicita seu tipo e a assinatura de funções dizem exatamente os tipos dos parâmetros e o retorno). Essas vantagens são ótimas em times grandes, em projetos muito complexos e com programadores inexperientes. Mas o TypeScript não tem de fato as vantagens de uma linguagem estaticamente tipada.

Em contrapartida, ele restringe a flexibilidade do JavaScript (uma das principais características da linguagem), sendo que ainda mantém a necessidade de técnicas de linguagens dinâmicas. E ainda gera a necessidade de alocar tempo e recurso para gerenciá-lo como dependência.

A não ser que seja um projeto grande, complexo, com muitos desenvolvedores ou com desenvolvedores distribuídos geograficamente ou com desenvolvedores inexperientes, eu não vejo a real necessidade do uso de TypeScript.

## Referências

- [TypeScript vs. JavaScript: Your Go-to Guide](https://www.toptal.com/TypeScript/TypeScript-vs-JavaScript-guide)
- [Brendan Eich - JavaScript at 20 - BrazilJS 2015](https://www.youtube.com/watch?v=bM79WQ9iMZQ)
- [A Trip Back in Time: the History of JavaScript](https://softteco.com/blog/history-of-JavaScript)
