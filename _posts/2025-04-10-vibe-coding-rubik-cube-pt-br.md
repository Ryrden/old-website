---
layout: post-pt-br
title: Como criei um Cubo mágico 3D usando Vibe Coding
seo_title: ""
seo_description: ""
exerpt: ""
cover_image: ""
canonical_url: "https://ryan.dev.br/2025-04-10-vibe-coding-rubik-cube-pt-br"
image_alt: ""
tags:
  - vibe coding
  - typescript
author: Ryan Souza
devto_url: "https://dev.to/ryrden/"
tabnews_url: null
comments: true
lang: pt-br
locale: pt_BR
published: false
---

- [Introdução](#introdução)
- [Prompts Iniciais](#prompts-iniciais)
- [Passo 1 - Setup do projeto](#passo-1---setup-do-projeto)
- [Passo 2 - Criar um cubo simples com todas as faces coloridas](#passo-2---criar-um-cubo-simples-com-todas-as-faces-coloridas)
- [Passo 3 - Construir um Cubo Rubik 3x3x3](#passo-3---construir-um-cubo-rubik-3x3x3)
- [Passo 4 - Adicionar Controles de orbita e controle manual na rotação do cubo](#passo-4---adicionar-controles-de-orbita-e-controle-manual-na-rotação-do-cubo)
- [Passo 5 - Rotacionar cada face individualmente](#passo-5---rotacionar-cada-face-individualmente)
  - [Passo 5.1 - Arrumando um pequeno warning](#passo-51---arrumando-um-pequeno-warning)
- [Passo 6 - Rotacionando todas as faces](#passo-6---rotacionando-todas-as-faces)
  - [Passo 6.1 - Debugando](#passo-61---debugando)
  - [Passo 6.2 - A Solução](#passo-62---a-solução)
- [Passo 7 - Adicionar Adesivos com cores reais](#passo-7---adicionar-adesivos-com-cores-reais)
- [Passo 8 - Representação lógica e inicio do Solver](#passo-8---representação-lógica-e-inicio-do-solver)
- [Passo 8.1 - Descorrompendo o cubo mágico](#passo-81---descorrompendo-o-cubo-mágico)
- [Fim e próximos passos](#fim-e-próximos-passos)

## Introdução

Recentemente em meu trabalho ao conversar com um colega de trabalho, fui surpreendido com uma feature simples na venda de um produto físico na loja virtual, o que me surpreendeu era basicamente que era possível ver o produto de maneira 3D, isso mesmo, eu podia rotacionar o produto e ver todos os seus angulos antes de prosseguir com a compra, isso me intrigou bastante porque em minha experiência de desenvolvimento (que não é tão longa) eu fui acostumado a codificar sites utilizando HTML, CSS e JS puro e nunca tinha pensando em codar algo 3D, claro que, nos ultimos anos alguns portfolios 3D ficaram famosos como o do [Bruno Simon](link) mas nunca fui de me comparar pois sempre acreditei que esse tipo de desenvolvimento envolvesse modelagem e habilidades de design as quais eu não tenho.

Entretanto, conversando com meu colega de trabalho, descobri o framework [Three.JS](link) que é basicamente o que permite criar todas as essas coisas 3D na web, fiquei bastante curioso e queria de fato aprender essa tecnologia, afinal, é javascript, não deve ser tão díficil!

Como todo bom programador sabe, a melhor maneira de aprender é fazendo, logo, pensei em criar algum projeto simples, fui correndo no Youtube ver se achava algum video aleatório de um projeto simples feito por alguém, geralmente da India, e de fato encontrei, me deparei com este video aqui:

![Video Solver Rubik Cube]()

Basicamente um site que resolve um cubo mágico 3D e mostra todos os passos! Me surpreendi de primeiro momento e fui na descrição procurar o código fonte e pra minha surpresa, o dono do video não tinha disponibilizado...

Então pensei: "Se existe video mostrando, então é possível fazer" (Sabemos que nem tudo é assim, cof cof pessoal das demos), e ai decidi juntar o assunto quente do momento que é o "Vibe Coding" e unir isso a minha iniciativa de codar um Cubo Mágico com o framework Three.Js.

## Prompts Iniciais

Após definir que ia usar essa tal Vibe coding, admito que não botei muita fé mas lá fui eu entrar no GPT 4o e escrevi meu primeiro prompt, fiz favor de fazer tudo em inglês pois acredito na eficiência do GPT neste modo:

> Let's assume I don't know anything about Three.JS but I want to build a Rubik cube solver, to turn this simple I want to > build a functional rubik cube first with three JS.
>
> Could you help me on this journey with the step by step

E então o GPT montou o seguinte roteiro pra mim

```text
🧭 Step-by-Step Roadmap

Step 1: Set Up Your Project
Install the tools (Node.js, a basic HTML/JS project structure, and Three.js).

Set up a basic scene: camera, renderer, and lighting.

Step 2: Create a Single Cubelet
Learn how to build a single colored cube (the building block of the Rubik’s Cube).

Use BoxGeometry and MeshBasicMaterial with colors.

Step 3: Build the 3x3x3 Rubik’s Cube
Arrange 27 cubelets in a 3D grid.

Group cubelets for ease of manipulation.

Step 4: Add Camera Controls
Use OrbitControls so you can view the cube from all angles.

Step 5: Implement Face Rotation
Detect and rotate individual cube faces (groups of cubelets).

Add basic UI or keyboard/mouse input to trigger rotations.

Step 6: Add Shuffle & Reset
Randomly shuffle the cube.

Create a reset button to return to the solved state.

Step 7: Build the Solver (Advanced)
Represent the cube's state in code.

Implement or adapt a solving algorithm (like Kociemba’s algorithm).
```

Admito que fiquei animado e lá fui eu seguir cada passo sugerido por ele

## Passo 1 - Setup do projeto

> A partir daqui, a fim de não complicar o artigo com inumeras linhas de código vou apenas mostrar o resultado e um link para o commit referente a esta etapa.

Inicialmente, apenas uma casaca de um index.html apontando para um script javascript chamado main.js

Aqui eu pedi educamente pro GPT utilizar typescript daqui em diante e ele o fez.

Após essa configuração inicial, este foi o resultado:

![imagem-resultado-01]()

Sim, um cubo vazio com as arestas em vermelho, não vai ser meu objetivo destrinchar o que o código faz aqui e isso eu vou deixar para outro artigo, afinal, não seria "Vibe Coding" se eu tentasse entender o código né?

[commit](link)

## Passo 2 - Criar um cubo simples com todas as faces coloridas

Aqui basicamente o GPT modifica o código para que na criação do cubo, ao inves de deixar uma casca vazia, ele pinte as faces utilizando cores em Hexadecimal

Achei completamente aceitável e lógico o que foi feito e este aqui foi o resultado:

![imagem-resultado-02]()

Assim que vi o resultado comecei a pensar que eu de fato iria chegar em algum lugar com apenas prompts mas mantive a calma até o próximo passo.

[commit](link)

## Passo 3 - Construir um Cubo Rubik 3x3x3

Aqui que as coisas começam a ficar nebulosas, assim que vi todo o código gerado a primeira coisa que pensei foi:

> Com certeza tem algum bug ai, impossível ele ter acertado tudo

Tentando seguir a ideia de "Vibe", apenas copiei oq ele disse e colei na minha IDE, rodei o projeto e pra minha supresa, lá estava um cubo 3x3x3 com todas as divisões bem definidas

![imagem-resultado-03]()

Aqui não pude me segurar, fiquei animado demais, comecei a mandar mensagens pra amigos devs falando o que estava por vir e assim q mandei todas as mensagens, tentei me recompor e pensei "Calma lá Ryan, é só um cubo com divisões, ele nem sequer funciona ainda", e ai me recompus e continuiei seguindo a "Vibe".

[commit](link)

## Passo 4 - Adicionar Controles de orbita e controle manual na rotação do cubo

Ate este momento o cubo ficava girando infinitamente no espaço, mas não vou conseguir mostrar isso aqui.

Esse passo foi apenas para permitir que eu como usuário pudesse rotacionar este cubo em todos os ângulos.

Mais uma vez, ele gerou o código e eu o aceitei copiando e colando na minha IDE e o resultado não foi diferente, eu podia girar o cubo, dar zoom e movimentar a minha tela me afastando do cubo ou não.

[commit](link)

## Passo 5 - Rotacionar cada face individualmente

Aqui eu achei interessante a maneira que o GPT estava abordando o problema, ele podia claramente permitir a rotação de todas as faces do cubo ao mesmo tempo, mas ele preferiu validar a ideia em uma face primeiro, no caso, a escolhida foi a face superior, o Topo do cubo.

e lá foi ele executar isso, me gerou o código, eu copiei, colei e rodei:

![imagem-gif]()

Assim que vi a face girando, respeitando a animação, as cores de cada face e tudo isso sem apresentar nenhum bug aparente eu fui a loucura, fiquei extremamente entusiasmado e completamente incrédulo de onde eu estava chegando com apenas "prompts bem escritos"

[commit](link)

### Passo 5.1 - Arrumando um pequeno warning

Aqui eu decidi parar os prompts para informar o GPT que um warning de tipagem do Typescript surgiu, ele sugeriu um código e isso simplesmente não funcionou, utilizei o copilot que esta presente na minha IDE e ele sugeriu utilizar o seguinte tipo de casting do typescript:

```typescript
const mesh = ...<instância>... as unkown as <Tipo_desejado>
```

Dei uma googlada em alguns foruns e vi que essa prátia era comum no typescript quando você conhece bem a tipagem, como eu não conhecia nada, apenas orei e deixei um comentário informando q essa linha pode esconder um bug.

[commit](link)

## Passo 6 - Rotacionando todas as faces

Aqui o negócio fica sério e mais interessante ainda, o GPT decide retornar na função declarada anteriormente e diz que vai "generalizar" ela para permitir que possa rotacionar qualquer face, achei interessante a decisão e lá fui eu copiar e colar o código na minha IDE

Assim que vou executar o projeto, percebo que nenhuma face esta rotacionando mais, nem mesmo face superior (feita no passo anterior). Começo a coçar a cabeça neste momento e me questiono o que esta errado, aqui meu instinto de programador disse pra mim mesmo: "Não vai ter jeito, vc vai ter q entender o código, esquecer esse vibe coding e debugar" e eu estava prestes a fazer isso mesmo até q pensei em delegar essa tarefa de debugar a ele, afinal, o chat que eu estava era detentor de todo o conhecimento por trás do código gerado, ele mesmo é a melhor pessoa para debugar.

### Passo 6.1 - Debugando

Foi ai então que fiz um prompt pedindo para o GPT colocar console.debug estratégicos em meu código para entender onde está a potencial falha

Ele adiciona os consoles.log e eu executo o projeto novamente, assim que executo um dos console.warn dele me aparece no console com a seguinte mensagem (escrita pelo GPT inclusive):

> ⚠️ Expected 9 cubelets but found 0. Check layer selection logic.
> rotateFace @ main.ts:87
> (anonymous) @ main.ts:149

Então lá vou eu novamente com esse warning, informo o GPT que esta acontecendo isso e aqui algum surpreendente acontece

### Passo 6.2 - A Solução

O GPT fica em estado de "Thinking" por pelo menos 10 segundos até que ele surge com a seguinte mensagem:

```text
🚨 Problem Root Cause

Math.abs(c.userData.initialPosition[axis] - value) < 0.01

This line checks if the cubelet is exactly on the layer like y = 1, but due to floating-point imprecision when using .applyMatrix4(...), the initialPosition might slightly drift from 1.00 to something like 0.999999.

✅ Robust Fix: Round Logical Positions Before Filtering
We’ll round the positions to the nearest integer (since cubelets are at -1, 0, or 1), so we always get perfect matching.

🧠 Replace this line:
const match = Math.abs(pos[axis] - value) < 0.01;

✅ With this:
const rounded = Math.round(pos[axis]);
const match = rounded === value;

✅ Why This Works
- Rounding keeps your logical layer detection accurate (-1, 0, 1).
- This makes the cube reliable even after many rotations where tiny floating-point errors accumulate.
```

Aqui eu admito que comecei a rir de nervoso, um conjunto de emoções surgiram sobre mim que eu apenas parei de digitar por uns 3 minutos e refleti tudo que estava acontecendo, eu simplesmente deleguei do começo ao fim uma ideia que tinha, não me coloquei em nenhum momento como força pensadora de fato na ideia que tinha e apenas criei prompts que orientavam um possível caminho solução. Eu me senti como se estivesse ajudando alguem que começou an programação e que este tem muito potencial de modo que eu ao apenas trazer recursos mínimos de apoio, este desbravasse todo o resto por conta própria da maneira mais auto didata possível...

Bom, ao final de tudo isso, o resultado foi esse aqui:

![gif-resultado](link)

[commit](link)

> Obs: um pouco antes de começar a debugar, traduzi os movimentos do cubo para teclas mais familiares para mim como WASD porque eu realmente acreditei que teria que por a mão na massa.

## Passo 7 - Adicionar Adesivos com cores reais

Pelo nome do passo e pelo estado que eu fiquei com a etapa anterior, nem liguei muito pelo o que estava por vir, apenas aceitei que ia dar certo de algum jeito.

Aqui basicamente o GPT queria melhorar a aparência do cubo mágico para que ficasse mais fiel a um verdadeiro cubo tendo cores internas, bom, então ele foi lá, gerou o código eu copiei e eu colei

O resultado foi esse:

![imagem](link)

Novamente, de se impressionar né? Ficou bem bonito e sofisticado, bora pra próxima etapa q ta chegando no final

[commit](link)

## Passo 8 - Representação lógica e inicio do Solver

Aqui o gpt queria criar uma estrutura de dados que representasse todos os estados de cada face do cubo para iniciar a códificado do Solver provavelmente, porém apesar de muito desafiador essa parte e animador também, eu não dei continuidade na mesma porque eu encontrei um bug no cubo.

O bug se tratava de que quando um movimento de rotação de face ocorre ao mesmo tempo que outra face esta rotacionando e elas se cruzam, o cubo se corrompe, tornando a imagem uma coisa horrenda.

## Passo 8.1 - Descorrompendo o cubo mágico

Expliquei pro GPT o que estava acontecendo e aqui fiz favor de me colocar em um papel atual de pensador, ao invés de apenas falar o que  aconteceu e esperar sua milagrosa resposta, sugeri que houvesse uma Fila para executar os movimentos e que houvesse um sistema de locking na função de rotação do cubo para evitar sobreposição, deste modo, nenhuma rotação de face poderia acontecer sem que a anterior tivesse sido executada

Dito e feito, ele gerou um código maravilhoso, não exatamente como eu esperava por que o Javascript não tem a estrutura de dados Fila implementada nativamente, tendo que usar de apoio o comando `.shift()` que é bem lento na verdade, mas pro problema em questão não me importei (entrada pequena)

Adicionei o código no script, que por sinal ja estava batendo suas 200 linhas e lá estava, um cubo sem defeito de corrupção agora!

![resultado-final]()

[commit](link)

## Fim e próximos passos

Aqui eu dediquei o resto do chat pra modularizar o código e para criar o README do projeto de modo que ficasse claro o que estava acontecendo, por sinal, utilizei meu template de README que uso em quase todos os projetos, você pode ver e usar ele [aqui](link).

Enfim, cheguei ao fim, vai ser dificil acreditar mas ate a etapa 7, tudo isso que eu narrei aconteceu em incriveis 1 horas, sim, apenas 1 hora escrevendo prompts, copiando e colando código eu cheguei em um cubo mágico funcional e não tenho dúvida de que se eu continuar esse projeto seja com vibe coding ou não, vai ser completamente possível implementar um solver nele, pois, ao olhar o código do GPT (após modularizado) você percebe que ele está bem escrito e que é possível entender oque está acontecendo.

Essa parte do que esta acontecendo no código de fato eu vou escrever em outro artigo, pois não aceito delegar 100% do meu trabalho como programador para uma IA e acredito que você que esteja lendo e que programe também concorde comigo.

Se você esta lendo esse atigo agora, saiba que ainda não escrevi o destrinchando o código gerado e vale me cobrar se eu ainda não tiver o feito.

Minha conclusão de toda essa experiência que tive é a seguinte: Não, a IA não vai substituir os bons programadores mas pode vir a substituir aqueles que durante a execução de um projeto esteja lá apenas para executar requisitos de tech como criar um CRUD por exemplo, isso a IA tira de letra, entretanto, regras de negócio traduzir problemas reais em código, tenho certeza que IA não é capaz ainda, afinal, é necessário alguém para estar descrevendo detalhadametne tudo que precisa ser feito.

Quanto ao Vibe coding, não vejo isso como uma potencial nova área dentro de tecnologia mas sinto que essa vai ser uma habilidade requisitada nos próximos anos para ser um dev mais eficiente, veja meu caso por exemplo, tive uma ideia e a partir de prompts e boas orientações eu consegui chegar onde queria, mas tudo isso só foi possível porque eu já tenho experiência e sei me virar bem.

---

Espero que tenha gostado do artigo e que ele tenha feito você refletir ao menos um pouquinho. Se tiver alguma dúvida ou sugestão, deixe um comentário abaixo ou entre em contato comigo pelo [LinkedIn](https://www.linkedin.com/in/ryan25/) ou pela aba de [contato](https://ryan.dev.br/contact/) do meu site.
