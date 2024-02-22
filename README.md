# Horários de Atendimento do Prof. André Godoi

* Plantão de dúvidas, toda terça e quinta-feira, das 8h30 às 10h, e das 14h às 15h30.

* Demais dias, deixar mensagem no Slack que respondo assim que possível, pois o professor não é 40h no Inteli, e por isso, assim que possível, ele responderá as mensagens.

* Finais de semana: é dia de maldade, sem atendimento urgente!

* Monitorias:
  *   Turma 11: Filipi Kikuchi (filipi.kikuchi@sou.inteli.edu.br), que atenderá quartas e sextas-feiras, das 8h30 às 9h30 e das 12h45 às 13h45 no ateliê da turma.
  *   Turma 13: Fernando Vasconcellos (fernando.vasconcellos@sou.inteli.edu.br), atenderá nas segundas e quartas-feiras, das 8h30 às 9h30 no ateliê da turma e outras 2h de atendimento será por pedidos feitas no e-mail dele.

# Prática de Computação: desenvolvendo jogos com Phaser

## 1. Descrição

Foco no desenvolvimento do ponto de vista da lógica de programação que possibilita o funcionamento desejado no jogo: inserção e modificação de elementos, identificação de colisões, controles de movimento e eventos, paralax e física no jogo.

## 2. Assuntos relacionados

Design de interação

Lógica algorítmica

## 3. Do que é feito um código-fonte de jogo?

* **HTML:** estrutura básica da página.

* **CSS:** estilos visuais do jogo.

* **JavaScript:** lógica de programação do jogo.

* **Canvas:** elemento HTML para renderizar gráficos.

* **Bibliotecas:** ferramentas para facilitar o desenvolvimento de jogos, que no nosso caso será o Phaser, mas existem outras como:

1. **Phaser:** Phaser é uma estrutura de jogo rápida e poderosa que permite o desenvolvimento de jogos HTML5 e JavaScript. Ele oferece uma ampla gama de recursos para criação de jogos 2D, incluindo física, animação, áudio e suporte a várias plataformas.

2. **Three.js:** Se você está interessado em desenvolver jogos 3D para a web, o Three.js é uma ótima opção. Ele é uma biblioteca JavaScript 3D que facilita a criação de gráficos 3D interativos e imersivos no navegador.

3. **Babylon.js:** Assim como o Three.js, o Babylon.js é uma biblioteca JavaScript 3D para o desenvolvimento de jogos e aplicativos interativos 3D na web.

4. **PixiJS:** PixiJS é uma biblioteca 2D rápida e leve para renderização de gráficos interativos. É amplamente utilizado para criar jogos 2D de alto desempenho para desktop e dispositivos móveis.

5. **CreateJS:** CreateJS é uma suíte de bibliotecas JavaScript que inclui módulos para criação de gráficos vetoriais, áudio, animação e interação com sprites. É útil para desenvolver jogos 2D e aplicativos interativos.

6. **Cocos2d-JS:** Cocos2d-JS é uma estrutura de desenvolvimento de jogos 2D baseada em JavaScript que é uma adaptação do popular motor de jogo Cocos2d-x. Oferece suporte para várias plataformas, incluindo web e móvel.

7. **ImpactJS:** ImpactJS é um motor de jogo HTML5 e JavaScript que facilita o desenvolvimento de jogos 2D de alta qualidade para navegadores da web e dispositivos móveis.

**Informação:**

Esse módulo não adota a estrutura do DOM (Document Object Model). Se você nunca ouviu falar do DOM, por enquanto basta você saber que o DOM é uma interface de programação de aplicações (API) que permite aos scripts JavaScript interagir com documentos HTML e XML.

A API de estilo do Phaser é mais limitada que o DOM web, pois foca na criação de jogos 2D e não na manipulação completa de estilos CSS. Nem todas as propriedades CSS são suportadas em Phaser.

## 4. Inserção e modificação de elementos:

Em um jogo, você pode criar, inserir e modificar elementos. Elementos são personagens, objetos e cenários. A aula de UX vai lhe trazer o máximo de conceitos sobre esse tema. Aqui veremos códigos-fonte a respeito disso.

### 4.1 Criação de Elementos:

A criação de elementos é o processo de gerar novos elementos HTML na página web usando JavaScript. Isso permite construir interfaces dinâmicas e interativas. As principais ferramentas para isso são:

a) **this.add.sprite**
  
Use o método this.add.sprite(x, y, key, frame) para criar um sprite a partir de uma imagem existente carregada no jogo. A key corresponde ao identificador da imagem carregada e o frame (opcional) define o quadro específico da imagem a ser usado. Exemplo:

```
// Cria um sprite a partir de uma imagem
const player = this.add.sprite(100, 100, 'player');

// Cria um sprite com propriedades personalizadas
const enemy = this.add.sprite(200, 200, 'enemy', {
  frame: 1,
  scale: 0.5
});
```

b) **this.add.text**

Use o método this.add.text(x, y, text, style) para criar um elemento de texto. Você pode definir o texto, a posição, e um estilo que inclui propriedades como fonte, cor e alinhamento. Exemplo:

```
const scoreText = this.add.text(10, 10, 'Score: 0', {
  fontSize: 16,
  color: '#ffffff'
});
```

c) **this.add.rectangle**

Use métodos específicos para criar formas como retângulos, círculos, polígonos etc. Por exemplo, this.add.rectangle(x, y, width, height, color) para retângulos. Exemplo:

```
const rectangle = this.add.rectangle(100, 100, 100, 50, 0x00ff00);
```

d) **container.add(childElement)**

Para inserir um novo elemento antes de outro elemento de referência, use o método **container.add(childElement, index)**. Este método insere o elemento filho na posição especificada pelo índice index relativo aos filhos existentes do container. Exemplo:

```
const player = this.add.sprite(100, 100, 'player');
const weapon = this.add.image(player.x, player.y, 'weapon');

player.add(weapon); // Adiciona weapon como filho de player
```

Outro exemplo:

```
const enemies = this.add.group();
const enemy1 = this.add.sprite(100, 100, 'enemy');
const enemy2 = this.add.sprite(200, 100, 'enemy');

enemies.add(enemy1);
enemies.addAt(enemy2, 0); // Insere enemy2 antes de enemy1
```

Para alterar a imagem ou animação de um sprite, use a propriedade texture ou anims.play.

```
const player = this.add.sprite(100, 100, 'player');

player.texture = 'player_jump'; // Altera a imagem para "player_jump"
player.anims.play('attack'); // Reproduz a animação "attack"
```


### 4.3 Manipulação de Atributos:

Além de criar e inserir elementos, você pode usar JavaScript para modificar seus atributos, como posição, tamanho, cor, etc. Isso inclui:

Para definir um atributo em um elemento Phaser, você pode acessar a propriedade correspondente diretamente. Por exemplo, para definir o atributo x de um sprite, use sprite.x = newValue. Exemplo:

```
const player = this.add.sprite(100, 100, 'player');

player.x = 200; // Define o atributo 'x' como 200
player.alpha = 0.5; // Define o atributo 'alpha' como 0.5 (transparência)

```

Para atributos específicos que não possuem propriedades diretas, use o método setData(key, value) para armazenar dados arbitrários associados ao elemento.

```
player.setData('health', 100); // Armazena um valor personalizado "health"

```

Para obter o valor de um atributo, você pode acessar a propriedade correspondente diretamente. Por exemplo, para obter o valor do atributo x de um sprite, use sprite.x.

Exemplo:

```
const playerX = player.x; // Obtém o valor do atributo 'x' do player
const playerHealth = player.getData('health'); // Obtém o valor personalizado "health"
```

Para atributos específicos que não possuem propriedades diretas, use o método getData(key) para recuperar dados arbitrários associados ao elemento.

```
this.load.image('player', 'assets/player.png'); //Carrega recurso
const player = this.add.sprite(100, 100, 'player'); //carrega sprite e define atributos

// Define a vida inicial
player.setData('health', 100);

// Define a velocidade de perda de vida
player.setData('healthDrain', 1);

update() { //atualiza vida e remove o sprite
  // Diminui a vida a cada frame
  const currentHealth = player.getData('health') - player.getData('healthDrain') * this.time.deltaTime;
  player.setData('health', currentHealth);

  // Remove o sprite quando a vida chega a zero
  if (currentHealth <= 0) {
    player.destroy();
  }
}

//exibe a vida
const healthText = this.add.text(10, 10, 'Vida: 100', {
  fontSize: 16,
  color: '#ffffff'
});

update() {
  // Atualiza o texto da vida
  healthText.text = `Vida: ${player.getData('health')}`;

  // ...
}

executa o jogo

const healthText = this.add.text(10, 10, 'Vida: 100', {
  fontSize: 16,
  color: '#ffffff'
});

update() {
  // Atualiza o texto da vida
  healthText.text = `Vida: ${player.getData('health')}`;

  // ...
}
```

Para remover um atributo, você pode definir sua propriedade correspondente como undefined.

```
player.alpha = undefined; // Remove o atributo 'alpha'
```

Para remover dados personalizados armazenados com setData, use o método removeData(key).

```
player.removeData('health'); // Remove o valor personalizado "health"
```


### 4.4 Estilização Dinâmica:

Você pode usar JavaScript para modificar dinamicamente as propriedades de um elemento. Isso permite criar animações e efeitos visuais interativos. Exemplo:


a) Acessando Propriedades Diretamente: Para a maioria das propriedades de estilo, você pode acessá-las diretamente no elemento.

```
sprite.alpha = 0.5; // Altera a transparência
text.fontSize = 20; // Altera o tamanho da fonte
```

b) Usando o Método setStyle(): Para propriedades mais específicas, use o método setStyle.

```
sprite.setStyle({
  backgroundColor: 'red',
  border: '1px solid black'
});
```

c) Acessando Propriedades Diretamente: Similar à alteração, você pode acessar muitas propriedades de estilo diretamente.

```
const alphaValue = sprite.alpha;
const fontSize = text.fontSize;
```

d) Usando o Método getStyle(): Para obter um objeto com todas as propriedades de estilo, use o método getStyle.

```
const styles = sprite.getStyle();
const backgroundColor = styles.backgroundColor;
```

### Considerações Importantes:

* **Desempenho:** Criar e inserir muitos elementos pode afetar o desempenho da página. Use técnicas de otimização como reutilização de elementos e fragmentação de documentos.

* **Acessibilidade:** Certifique-se de que os elementos inseridos dinamicamente sejam acessíveis a todos os usuários, incluindo aqueles que usam tecnologias assistivas.

* **Segurança:** Valide os dados inseridos dinamicamente para evitar ataques de script entre sites (XSS).


## 5. Identificação de Colisões em Jogos JavaScript

A detecção de colisões é um componente fundamental em jogos JavaScript, permitindo que objetos interajam uns com os outros de forma realista. Detectar colisões entre elementos do jogo pode ser implementada de diferentes tipos, como detectar se um retangular bateu em outro, se um círculo bateu em outro, etc.

Exploremos as diferentes técnicas e seus pontos fortes e fracos:

### 5.1 Métodos de Detecção de Colisões:

**a) Colisão Simples entre Sprites:**

```
// Cria dois sprites
const player = this.add.sprite(100, 100, 'player');
const enemy = this.add.sprite(200, 100, 'enemy');

// Habilita a física para os sprites
this.physics.world.enable(player);
this.physics.world.enable(enemy);

// Cria um collider entre os sprites
this.physics.add.collider(player, enemy, () => {
  // Função a ser executada quando há colisão
  console.log('Colisão detectada!');
});
```

**b) Colisão com Grupos de Sprites:**

```
// Cria um grupo de inimigos
const enemies = this.add.group();
enemies.createMultiple({
  key: 'enemy',
  quantity: 10,
});

// Habilita a física para o grupo e o jogador
this.physics.world.enable(enemies);
this.physics.world.enable(player);

// Cria um collider entre o jogador e o grupo de inimigos
this.physics.add.collider(player, enemies, (player, enemy) => {
  // Função a ser executada quando o jogador colide com um inimigo
  console.log('Colisão com inimigo!');
  enemy.destroy(); // Remove o inimigo da tela
});

```
**c) Detecção de Tiles:**

Tiles (ladrilhos em português) são pequenos elementos gráficos quadrados, retangulares ou hexagonais que servem como unidades básicas para a construção de cenários em jogos 2D. São como peças de um quebra-cabeça que, juntas, formam o ambiente do jogo.

```
// Cria um mapa de tiles
const map = this.add.tilemap('map');
const layer = map.createLayer('CollisionLayer', 'tiles');

// Define as propriedades de colisão para as tiles
layer.setCollisionByExclusion([-1]); // Colisão em todas as tiles exceto -1

// Habilita a física para o jogador
this.physics.world.enable(player);

// Cria um collider entre o jogador e as tiles
this.physics.add.collider(player, layer, () => {
  // Função a ser executada quando o jogador colide com uma tile
  console.log('Colisão com tile!');
});
```

**d) Detecção de Sobreposição:**

```
// Cria dois sprites
const player = this.add.sprite(100, 100, 'player');
const enemy = this.add.sprite(200, 100, 'enemy');

// Verifica se os sprites estão se sobrepondo
const isOverlapping = this.physics.overlap(player, enemy);

if (isOverlapping) {
  // Função a ser executada quando os sprites se sobrepõem
  console.log('Sprites se sobrepondo!');
}

```

**e) Colisão com o cenário:**

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

**f) Tipos de Detecção de Colisões:**

* Colisão de Ponto: Verifica se um ponto está dentro de um elemento. Útil para detectar cliques em botões ou áreas específicas.

* Colisão de Retângulo: Verifica se dois retângulos se interceptam. Esse é o método mais comum para detectar colisões em jogos simples.

* Colisão de Polígono: Verifica se dois polígonos se interceptam. Permite detectar colisões mais complexas, como personagens com formas irregulares.

* Colisão de Círculo: Verifica se dois círculos se interceptam. Útil para detectar colisões entre objetos circulares, como planetas ou bolas.


## 6. Controles de movimento e eventos:

Cria controles para mover personagens e objetos, implementando eventos para interagir com o jogo, do tipo: clique, toque, teclado. 

### 6.1 Eventos de Teclado:

* keydown: Detecta quando uma tecla é pressionada.

* keyup: Detecta quando uma tecla é solta.

* keypress: Detecta quando um caractere é digitado.

### 6.2 Eventos de Mouse:

* click: Detecta quando o mouse é clicado em um elemento.

* mousedown: Detecta quando o botão do mouse é pressionado em um elemento.

* mouseup: Detecta quando o botão do mouse é solto em um elemento.

* mousemove: Detecta o movimento do mouse sobre um elemento.

### 6.3 Movimento de Elementos:

* setInterval: Atualiza a posição de um elemento a cada intervalo de tempo.

* requestAnimationFrame: Atualiza a posição de um elemento de forma suave.

Exemplo:

**a) Configurando o Phaser:**

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

**b) Carregando Recursos:**

```
function preload() {
  this.load.image('player', 'assets/player.png');
}
```

**c) Criando o Cenário e o Jogador:**

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

**d) Atualizando o Jogo:**

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

**e) Criando animações do jogador**

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

**f) Exemplo de Saltos:**

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

## 7. Parallax:

O Parallax é uma técnica gráfica que cria a ilusão de profundidade em um jogo 2D movendo diferentes camadas de fundo em velocidades diferentes. Isso pode ser usado para criar cenários mais realistas e envolventes.

Como Funciona o Parallax no Phaser?

No Phaser, você pode criar efeitos parallax usando a classe ParallaxLayer. Essa classe permite definir uma imagem de fundo, sua velocidade de movimento e outras propriedades.

Exemplo de Parallax Simples:

```
const background = this.add.image(0, 0, 'background');
background.setOrigin(0, 0);

// Cria uma camada parallax com a imagem 'clouds'
const clouds = this.add.parallaxLayer(0, 0, 'clouds', 800, 600);

function update() {
  // Move a camada parallax das nuvens
  clouds.setTilePosition(clouds.x - 0.5);
}
```

## 8. Física no jogo:

Aplicar conceitos básicos de física (gravidade, força, movimento). Server para simular comportamentos físicos no jogo (queda de objetos, saltos, etc.). Portanto, a física de jogo é um conjunto de regras e simulações que definem como os objetos se movem e interagem em um ambiente virtual. Ela é essencial para criar jogos realistas e interativos.

Como Funciona a Física no Phaser?

O Phaser usa o motor de física **Arcade.js** para simular a física do jogo. O **Arcade.js** oferece uma variedade de recursos para criar movimentos realistas, colisões e interações entre objetos.

Exemplo de Física Simples:

```
// Cria um sprite para o jogador
const player = this.physics.add.sprite(100, 100, 'player');

// Define a gravidade
this.physics.world.gravity.y = 300;

function update() {
  // Controla o movimento do jogador
  // ...

  // Aplica a física ao jogador
  this.physics.world.update();
}
```

### 8.1 Conceitos de Física de Jogo:

* Força: Uma influência que causa a mudança no movimento de um objeto.

* Massa: A propriedade de um objeto que resiste à mudança de movimento.

* Velocidade: A taxa de mudança de posição de um objeto.

* Aceleração: A taxa de mudança de velocidade de um objeto.

* Colisão: A interação entre dois ou mais objetos.

* Movimento com Impulso: O jogador aplica força a um objeto para movê-lo.

* Salto com Trajetória: O jogador pula e a física calcula a trajetória do salto.

* Colisões com Resposta Realista: Os objetos se deformam e ricocheteiam de acordo com a física.


## Exercício:

Acesse o [Phazer](https://github.com/pacifiquem/phaser-star-game) e comente as linhas. Use suas anotações dos autoestudos para fazer essa tarefa.
Você pode até usar o chatGPT ou Gemini para lhe ajudar. Mas atenção, não exagere. Tente relembrar dos seus autoestudos.

Um sorteio contemplará 10 de alunos para explicar para a sala 20 linhas do **script.js**

1. Estudante 01 --> comentará e explicará da linha 1 à 20
  
3. Estudante 02 --> comentará e explicará da linha 21 à 40
   
...

10. Estudante 10 --> comentará da 180 à 203 (última linha)

E quem vier aqui na frente, terá um prêmio!


<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/m01-semana03/blob/main/imgs/turma13.png">
   <img alt="RTurma 13" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/m01-semana03/blob/main/imgs/turma13.png)">
</picture>


## Ponderada da Semana

[Ponderada Semana 03](https://github.com/InteliContent/M1/blob/main/Semana_03/tutorial/Semana_03.md)

No fechamento do dia, trarei dicas importantes.

Prazo final de entrega: domingo às 23h.
