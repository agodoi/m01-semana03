# Prática de Computação: desenvolvendo jogos com Phaser

## Descrição

Foco no desenvolvimento do ponto de vista da lógica de programação que possibilita o funcionamento desejado no jogo: inserção e modificação de elementos, identificação de colisões, controles de movimento e eventos, paralax e física no jogo.

## Assuntos relacionados

Design de interação

Lógica algorítmica

a) Inserção e modificação de elementos:

Criar e adicionar elementos ao jogo (personagens, objetos, cenários).
Modificar propriedades de elementos (posição, tamanho, cor, etc.).
b) Identificação de colisões:

Detectar colisões entre elementos do jogo.
Implementar diferentes tipos de colisões (retangulares, circulares, etc.).
c) Controles de movimento e eventos:

Criar controles para mover personagens e objetos.
Implementar eventos para interagir com o jogo (clique, toque, teclado).
d) Parallax:

Criar um efeito de profundidade no cenário.
Implementar diferentes tipos de parallax (multicamadas, scroll parallax).
e) Física no jogo:

Aplicar conceitos básicos de física (gravidade, força, movimento).
Simular comportamentos físicos no jogo (queda de objetos, saltos, etc.).
f) Exemplo de código em JavaScript:

Implementar os tópicos acima em um jogo simples.
Recursos:

HTML: Estrutura básica da página.
CSS: Estilos visuais do jogo.
JavaScript: Lógica de programação do jogo.
Canvas: Elemento HTML para renderizar gráficos.
Bibliotecas: Ferramentas para facilitar o desenvolvimento de jogos (p5.js, Phaser, etc.).
Conteúdo da Aula:

1. Introdução:

Apresentação dos tópicos da aula.
Demonstração de exemplos de jogos.
2. Inserção e modificação de elementos:

Criar elementos usando createElement.
Adicionar elementos ao DOM usando appendChild.
Modificar propriedades de elementos usando style.
3. Identificação de colisões:

Verificar colisões entre elementos usando getBoundingClientRect.
Implementar diferentes tipos de colisões.
4. Controles de movimento e eventos:

Criar controles usando eventos de teclado e mouse.
Implementar eventos para interagir com o jogo.
5. Parallax:

Criar diferentes camadas de parallax.
Implementar scroll parallax.
6. Física no jogo:

Aplicar conceitos básicos de física.
Simular comportamentos físicos no jogo.
7. Exemplo de código em JavaScript:

Desenvolvimento de um jogo simples utilizando os tópicos da aula.
Atividades:

Criar um jogo simples utilizando os tópicos da aula.
Implementar diferentes tipos de colisões.
Criar um efeito de parallax.
Simular um comportamento físico no jogo.
Recursos Adicionais:

Tutoriais online:
https://www.w3schools.com/js/default.asp
https://developer.mozilla.org/en-US/docs/Web/JavaScript
Bibliotecas de jogos:
https://p5js.org/
https://phaser.io/
Observações:

Esta aula é um ponto de partida para o desenvolvimento de jogos com JavaScript.
É importante aprofundar os conhecimentos em JavaScript e nas bibliotecas de jogos para criar jogos mais complexos.
Exemplo de código:


// Criação de um elemento canvas
const canvas = document.createElement('canvas');
canvas.width = 500;
canvas.height = 500;
document.body.appendChild(canvas);

// Contexto de desenho
const ctx = canvas.getContext('2d');

// Personagem
const personagem = {
  x: 100,
  y: 100,
  velocidadeX: 5,
  velocidadeY: 5,
};

// Função para atualizar o jogo
function atualizar() {
  // Limpar tela
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // Atualizar posição do personagem
  personagem.x += personagem.velocidadeX;
  personagem.y += personagem.velocidadeY;

  // Desenhar personagem
  ctx.fillStyle = 'red';
  ctx.fillRect(personagem.x, personagem.y, 50, 50);

  // Solicitar a próxima atualização
  requestAnimationFrame(atualizar);
}

// Iniciar atualização do jogo
atualizar();









Aula de JavaScript para Desenvolvimento de Jogos
Introdução
Nesta aula, exploraremos a lógica de programação em JavaScript para criar jogos simples, abrangendo os seguintes tópicos:

Inserção e modificação de elementos: Criar e manipular elementos visuais no jogo.
Identificação de colisões: Detectar quando objetos se chocam no jogo.
Controles de movimento e eventos: Implementar movimentos e responder a eventos do jogador.
Parallax: Criar a ilusão de profundidade no cenário.
Física no jogo: Simular as leis da física no seu jogo.
a) Inserção e modificação de elementos
Para inserir elementos no jogo, usaremos a função createElement. Podemos criar elementos como divs, imagens e canvas. Para modificar elementos, podemos usar propriedades como style.left, style.top e innerHTML.

Exemplo:

JavaScript
const div = document.createElement('div');
div.style.left = '100px';
div.style.top = '100px';
div.innerHTML = 'Olá mundo!';
document.body.appendChild(div);
Use o código com cuidado.
b) Identificação de colisões
Para identificar colisões, podemos usar o método getBoundingClientRect. Este método retorna um objeto com as coordenadas do elemento. Podemos comparar as coordenadas de dois elementos para verificar se há colisão.

Exemplo:

JavaScript
const div1 = document.getElementById('div1');
const div2 = document.getElementById('div2');

const rect1 = div1.getBoundingClientRect();
const rect2 = div2.getBoundingClientRect();

if (rect1.left < rect2.right &&
    rect1.right > rect2.left &&
    rect1.top < rect2.bottom &&
    rect1.bottom > rect2.top) {
  // Colisão detectada!
}
Use o código com cuidado.
c) Controles de movimento e eventos
Para implementar movimentos, podemos usar eventos como keydown e keyup. Podemos usar a função setInterval para atualizar a posição dos elementos a cada intervalo de tempo.

Exemplo:

JavaScript
const player = document.getElementById('player');

document.addEventListener('keydown', (event) => {
  if (event.key === 'ArrowLeft') {
    player.style.left = parseInt(player.style.left) - 10 + 'px';
  } else if (event.key === 'ArrowRight') {
    player.style.left = parseInt(player.style.left) + 10 + 'px';
  }
});
Use o código com cuidado.
d) Parallax
Para criar parallax, podemos usar várias camadas de imagens com velocidades diferentes. As camadas mais próximas do jogador se movem mais rápido que as camadas mais distantes.

Exemplo:

JavaScript
const background1 = document.getElementById('background1');
const background2 = document.getElementById('background2');

document.addEventListener('scroll', () => {
  background1.style.left = -window.scrollX / 10 + 'px';
  background2.style.left = -window.scrollX / 20 + 'px';
});
Use o código com cuidado.
e) Física no jogo
Para simular física no jogo, podemos usar bibliotecas como Matter.js. Esta biblioteca fornece ferramentas para criar objetos físicos com massa, velocidade e gravidade.

Exemplo:

JavaScript
const Engine = Matter.Engine;
const World = Matter.World;
const Bodies = Matter.Bodies;

const engine = Engine.create();
const world = World.create(engine);

const player = Bodies.rectangle(100, 100, 50, 50);
World.add(world, player);

Engine.run(engine);
Use o código com cuidado.
f) Exemplo de código em JavaScript
JavaScript
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');

// Cria o jogador
const player = {
  x: 100,
  y: 100,
  width: 50,
  height: 50,
};

// Desenha o jogador
function drawPlayer() {
  ctx.fillStyle = 'red';
  ctx.fillRect(player.x, player.y, player.width, player.height);
}

// Atualiza a posição do jogador
function updatePlayer() {
  if (keydown.left) {
    player.x -= 5;
  } else if (keydown.right) {
    player.x += 5;
  }
}

// Loop do jogo
