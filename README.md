# Prática de Computação: desenvolvendo jogos com Phaser

## Descrição

Foco no desenvolvimento do ponto de vista da lógica de programação que possibilita o funcionamento desejado no jogo: inserção e modificação de elementos, identificação de colisões, controles de movimento e eventos, paralax e física no jogo.

## Assuntos relacionados

Design de interação

Lógica algorítmica

## Inserção e modificação de elementos:

Em um jogo, você pode criar, inserir e modificar elementos. Elementos são personagens, objetos e cenários. A aula de UX vai lhe trazer o máximo de conceitos sobre esse tema.

### Criação de Elementos:

A criação de elementos é o processo de gerar novos elementos HTML na página web usando JavaScript. Isso permite construir interfaces dinâmicas e interativas. As principais ferramentas para isso são:

* document.createElement(tagName): Cria um novo elemento HTML com a tag especificada. Cria elementos HTML como divs, imagens e canvas.

* document.createTextNode(text): Cria um novo nó de texto com o conteúdo especificado.

Exemplo:
```
JavaScript
const div = document.createElement('div');
div.textContent = 'Olá mundo!';
document.body.appendChild(div);
```

### Inserção de Elementos:

Depois de criar um elemento, você precisa inseri-lo na estrutura do DOM (Document Object Model) para que ele seja visível na página. As principais formas de fazer isso são:

* parentNode.appendChild(childNode): Insere um elemento como filho de outro elemento.

* parentNode.insertBefore(newNode, referenceNode): Insere um elemento antes de outro elemento filho.

* element.innerHTML = htmlString: Substitui o conteúdo HTML interno de um elemento.

Exemplo:

```
JavaScript
const div1 = document.getElementById('div1');
const div2 = document.createElement('div');
div2.textContent = 'Nova div';

div1.appendChild(div2); // Insere 'div2' como filho de 'div1'
```

### Manipulação de Atributos:

Além de criar e inserir elementos, você pode usar JavaScript para modificar seus atributos, como posição, tamanho, cor, etc. Isso inclui:

* **element.setAttribute(attributeName, attributeValue):** Define um atributo para um elemento.

* **element.getAttribute(attributeName):** Obtém o valor de um atributo de um elemento.

* **element.removeAttribute(attributeName):** Remove um atributo de um elemento.

Exemplo:

```
JavaScript
const div = document.getElementById('div');
div.setAttribute('id', 'nova-id'); // Altera o ID da div
div.getAttribute('class'); // Obtém a classe da div
div.removeAttribute('style'); // Remove o estilo da div
```

### 4. Estilização Dinâmica:

Você pode usar JavaScript para modificar dinamicamente as propriedades CSS de um elemento. Isso permite criar animações e efeitos visuais interativos. As principais ferramentas para isso são:

* **element.style.propertyName = value;:** Define uma propriedade CSS para um elemento.

* **getComputedStyle(element).getPropertyValue(propertyName):** Obtém o valor de uma propriedade CSS de um elemento.

Exemplo:

```
JavaScript
const div = document.getElementById('div');
div.style.backgroundColor = 'red'; // Altera a cor de fundo da div
div.style.width = '100px'; // Altera a largura da div
getComputedStyle(div).getPropertyValue('font-size'); // Obtém o tamanho da fonte da div
```

### Considerações Importantes:

* **Desempenho:** Criar e inserir muitos elementos pode afetar o desempenho da página. Use técnicas de otimização como reutilização de elementos e fragmentação de documentos.

* **Acessibilidade:** Certifique-se de que os elementos inseridos dinamicamente sejam acessíveis a todos os usuários, incluindo aqueles que usam tecnologias assistivas.

* **Segurança:** Valide os dados inseridos dinamicamente para evitar ataques de script entre sites (XSS).

### Recursos Adicionais:

Documentação do DOM: https://developer.mozilla.org/pt-BR/docs/Web/API/Document_Object_Model
Tutoriais de JavaScript: https://www.w3schools.com/js/default.asp


### Identificação de Colisões em Jogos JavaScript

A detecção de colisões é um componente fundamental em jogos JavaScript, permitindo que objetos interajam uns com os outros de forma realista. Detectar colisões entre elementos do jogo pode ser implementada de diferentes tipos, como detectar se um retangular bateu em outro, se um círculo bateu em outro, etc.

Exploremos as diferentes técnicas e seus pontos fortes e fracos:

#### Métodos de Detecção de Colisões:

* getBoundingClientRect: Retorna um objeto com as coordenadas e dimensões do elemento.

* Vantagens: Simples de implementar, funciona com qualquer elemento HTML.

* Desvantagens: Baixa precisão, não detecta colisões complexas.

* checkCollision: Função personalizada que verifica se dois elementos colidem.

* Vantagens: Permite implementar diferentes tipos de colisões.

* Desvantagens: Mais complexa de implementar, requer conhecimento de geometria.

#### Tipos de Colisões:

* Colisão de Ponto: Verifica se um ponto está dentro de um elemento. Útil para detectar cliques em botões ou áreas específicas.

* Colisão de Retângulo: Verifica se dois retângulos se interceptam. Esse é o método mais comum para detectar colisões em jogos simples.

* Colisão de Polígono: Verifica se dois polígonos se interceptam. Permite detectar colisões mais complexas, como personagens com formas irregulares.

* Colisão de Círculo: Verifica se dois círculos se interceptam. Útil para detectar colisões entre objetos circulares, como planetas ou bolas.

### Bibliotecas de Detecção de Colisões:

* Matter.js: Biblioteca popular que oferece física realista e facilita a detecção de colisões complexas.

* Cannon.js: Biblioteca focada em física 3D, ideal para jogos com objetos tridimensionais.

* PolyK: Biblioteca leve para detectar colisões de polígonos com alta performance.

### Considerações Importantes:

* Precisão: Escolha o método de detecção de colisão adequado ao nível de precisão necessário no seu jogo.

* Desempenho: A detecção de colisões pode ser cara em termos de performance. Otimize seu código para evitar gargalos.

* Complexidade: Equilibre a necessidade de precisão com a complexidade da implementação.


c) Controles de movimento e eventos:

Cria controles para mover personagens e objetos, implementando eventos para interagir com o jogo, do tipo: clique, toque, teclado. 

Eventos de Teclado:

* keydown: Detecta quando uma tecla é pressionada.

* keyup: Detecta quando uma tecla é solta.

* keypress: Detecta quando um caractere é digitado.

Eventos de Mouse:

* click: Detecta quando o mouse é clicado em um elemento.

* mousedown: Detecta quando o botão do mouse é pressionado em um elemento.

* mouseup: Detecta quando o botão do mouse é solto em um elemento.

* mousemove: Detecta o movimento do mouse sobre um elemento.

Movimento de Elementos:

* setInterval: Atualiza a posição de um elemento a cada intervalo de tempo.

* requestAnimationFrame: Atualiza a posição de um elemento de forma suave.

Exemplo:

1. Configurando o Phaser:

```
const config = {
  type: Phaser.AUTO,
  width: 800,
  height: 600,
  physics: {
    default: 'arcade',
    arcade: {
      gravity: { y: 300 }
    }
  },
  scene: {
    preload: preload,
    create: create,
    update: update
  }
};

const game = new Phaser.Game(config);
```


2. Carregando Recursos:

```
function preload() {
  this.load.image('player', 'assets/player.png');
}
```


3. Criando o Cenário e o Jogador:

```
function create() {
  // Cria o cenário
  const background = this.add.image(0, 0, 'background');
  background.setOrigin(0, 0);

  // Cria o jogador
  this.player = this.physics.add.sprite(100, 100, 'player');
  this.player.setCollideWorldBounds(true);

  // Define as teclas de controle
  this.cursors = this.input.keyboard.createCursorKeys();
}
```


   
5. Atualizando o Jogo:

```
function update() {
  // Controla o movimento do jogador
  if (this.cursors.left.isDown) {
    this.player.setVelocityX(-160);
  } else if (this.cursors.right.isDown) {
    this.player.setVelocityX(160);
  } else {
    this.player.setVelocityX(0);
  }

  if (this.cursors.up.isDown) {
    this.player.setVelocityY(-160);
  } else if (this.cursors.down.isDown) {
    this.player.setVelocityY(160);
  } else {
    this.player.setVelocityY(0);
  }

  // Adiciona lógica adicional para o seu jogo
}
```

```
// Cria as animações do jogador
this.anims.create({
  key: 'walk',
  frames: this.anims.generateFrameNumbers('player', { start: 0, end: 3 }),
  frameRate: 10,
  repeat: -1
});

this.anims.create({
  key: 'run',
  frames: this.anims.generateFrameNumbers('player', { start: 4, end: 7 }),
  frameRate: 10,
  repeat: -1
});

this.anims.create({
  key: 'jump',
  frames: this.anims.generateFrameNumbers('player', { start: 8, end: 10 }),
  frameRate: 10,
  repeat: -1
});

function update() {
  // Controla o movimento do jogador
  if (this.cursors.left.isDown) {
    this.player.setVelocityX(-160);
    this.player.anims.play('walk', true);
  } else if (this.cursors.right.isDown) {
    this.player.setVelocityX(160);
    this.player.anims.play('walk', true);
  } else {
    this.player.setVelocityX(0);
    this.player.anims.play('idle');
  }

  if (this.cursors.up.isDown && this.player.body.onFloor()) {
    this.player.setVelocityY(-300);
    this.player.anims.play('jump', true);
  }

  // Adiciona lógica adicional para o seu jogo
}
```
Colisões

```
// Cria um objeto com o qual o jogador pode colidir
const platform = this.physics.add.sprite(400, 300, 'platform');
platform.setImmovable(true);

function update() {
  // Controla o movimento do jogador
  // ...

  // Detecta colisão entre o jogador e a plataforma
  this.physics.collide(this.player, platform);

  // Adiciona lógica para o que acontece quando o jogador colide com a plataforma
  if (this.physics.collide(this.player, platform)) {
    // O jogador pousou na plataforma
  }

  // Adiciona lógica adicional para o seu jogo
}
```

Saltos

```
function update() {
  // Controla o movimento do jogador
  // ...

  // Permite que o jogador pule
  if (this.cursors.up.isDown && this.player.body.onFloor()) {
    this.player.setVelocityY(-300);
  }

  // Simula o salto
  this.player.body.applyGravity();

  // Adiciona lógica para o que acontece quando o jogador pousa
  if (this.player.body.onFloor()) {
    // O jogador pousou no chão
  }

  // Adiciona lógica adicional para o seu jogo
}
```

7. 









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
