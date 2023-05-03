Hélder Rodrigues, nº25956
Sara Capela, nº25973
André Jardin, nº25978


//recomendamos em abrir em modo code para ter espaços e o texto de forma organizada


Análise do Jogo

Sobre o Jogo

Este jogo foi criado baseado no tutorial de MonoGame do Michael Hoffman (https://gamedevelopment.tutsplus.com/series/cross-platform-vector-shooter-xna--gamedev-10559), que por sua vez é um tutorial sobre como criar um jogo idêntico a um jogo já existente chamado Geometry Wars em MonoGame, este jogo é um jogo 2d de árcade space shooter em um estilo old School, mas remixado para o século 21 com gráficos de última geração e jogabilidade profunda e moderna. Jogar é simples: você é um "navio" geométrico preso em um mundo, enfrentando ondas de inimigos diferentes.

Mecânicas - PowerUps

+ : aumenta a vida em 1
∆ : o ataque duplica em vez de mandar um tiro passa a mandar 2
   : aumenta a velocidade

Existem diversos tipos de inimigos que têm como objetivo perseguir e disparar contra o jogador.


Estrutura

A nível de estrutura nós de forma "abstrata" conseguimos dividir a forma que o programador dividiu as classes em 3 tipos:

- Classes Primárias - Classes dos elementos principais do jogo (inimigos, balas, jogador) que possuem métodos que afetam diretamente o principal do jogo, os seus elementos, comportamentos e modo de funcionar.

- Classes Secundárias -  Estas classes são usadas para gerir os diferentes objetos/valores das classes principais. Nesta classes os objetos e as interações entre eles são tratadas com mais pormenor.  No caso de serem valores estes são guardados em ficheiro.

- Classes "RC" - 

Análise dos Ficheiros

Tem as classes todos em um sítio, separada dos conteúdos.
Na pasta Contents as Fontes, Sons, e Texturas estão separados por pastas.

Fontes:
Na pasta encontram-se 3 fontes, uma para o título grande, um para o titulo e o principal normalmente usado.

Sons:
Ao escolher um som para ser reproduzido o jogo pega aleatoriamente um do tipo de som que quer reproduzir, por exemplo: ao disparar existe 3 sons de disparo e aleatoriamente o jogo vai pegar um deles para ser reproduzido, acreditamos que o programador tenha tomado esta decisão á cerca do som para tornar o jogo mais cativante ao jogador, tendo sons diferentes a serem produzidos em vez de estar sempre o mesmo. Dos vários tipos de sons, existe:

	3 de Explosão
	1 música do jogo
	4 de selecionar menu
	3 de disparo
	3 de spawnar
  
Texturas:

Dentro das texturas existe 2 pastas, Menu e Options, na pasta Menu, encontra-se as texturas usadas para o menu principal e para o menu “How to Play”, como por exemplo os botões. Na pasta Options, estão as texturas dos botões. Fora das pastas, tem as texturas do Boss, da bala, da bala inimiga 





Análise do Código (por classes)

Nota: eram no total 43 classes e então dividimos as classes pelos 3, pelo que a forma que fomos fazendo nota-se a diferença do ficheiro de cada um a nível de organização, ainda que todos seguimos a estrutura de pegar na classe e analisar os métodos lá presentes

Classe Boss
•	Herda atributos da classe inimigo
•	O “boss” tem vida e localização, esta última criada num local aleatório
•	Existe um enum com as diversos estados do “boss”
•	Um método que cria o “boss”, com as respetivas caraterísticas e comportamentos;
•	Um método que determina a fase do “boss” tendo em conta a vida que ele possui;
•	Também é assegurado que o “boss” fica no ecrã;
•	Um método que faz criar uma explosão quando o “boss” fica com a vida inferior a zero;
•	Um método que adiciona pontos ao jogador caso o boss esteja morto;
•	Um método que desenha o boss;
•	Um método que faz com que a fase do “boss” influencie a maneira que ele se movimenta
•	Um método que faz com que a fase do “boss” influencie a maneira que ele dispara contra o jogador
•	Um método que faz com que o boss persiga o jogador
•	Um método que faz com que o boss dispare balas numa fase inicial e outro para a fase 2 e 3
•	Um método que cria realmente a bala que irá ser disparada

Classe Bala
•	Tem um método que cria a bala com as suas devidas caraterísticas;
•	Tem um método que destrói a bala;
•	Tem um método que atualiza a posição da bala;
•	Tem um método que desenha a bala quando o jogador pressiona uma tecla, a bala é desenhada no ecrã;

Classe Button
•	Classe designada para os botões que existem no jogo;
•	São criadas variáveis que determinam as caraterísticas dos botões;
•	É criado um enum que possui todos os tipos de botões necessários;
•	Tem um método que cria um botão com as suas caraterísticas;
•	Um método para quando um botão é pressionado é tocado um som específico e é dada a instrução de fazer o que o botão faz (utilizando um case para ver que tipo de botão foi pressionado);
•	Um método para haver animação quando saímos de um botão;
•	Um método para ver se o rato está a colidir com a sprite do botão e outro para ver se está a ser pressionado para entrar ou sair;
•	Outro método que desenha o botão criado no ecrã;

Classe Inimigo
•	É importada para esta classe atributos da classe “Sprite Actors”;
•	São declaradas as caraterísticas do inimigo (seu movimento e framerate, assim como a recarga dos tiros, e o dano atribuído a cada dano que lhe é feito);
•	Tem um método que cria o inimigo, e outro que atualiza o inimigo no ecrã, e outro que desenha o inimigo que desenha, em semelhança às balas;
•	Tem outro que destrói o inimigo e adiciona os pontos à pontuação do jogador;
•	Tem um método que lida com as colisões entre os diversos inimigos;
•	Um método que cria inimigos que caçam o jogador, outro cria dardos que perseguem o jogado, e outro que cria inimigos que só andam pelo mapa e outro que cria inimigos que vêm lutar com o jogador (todos estes inimigos têm pontuações que serão dadas ao jogador quando mortos);
•	Tem os métodos que caraterizam os comportamentos dos inimigos (caçar, lutar, e wander);
•	Tem métodos para adicionar, remover e atualizar os comportamentos anteriormente mencionados;
•	Um método para disparar as balas dos inimigos;

Classe EnemySpawner
•	São criadas variáveis que determinam a chance de aparecerem inimigos e a frequência com que eles aparecem;
•	Possui um método que cria um spawn de inimigos com as chances de aparecerem já definidas, e um que cria um spawn com chances de inimigos aparecerem customizadas;
•	 Um método que faz essas chances de aparecer os diversos inimigos de forma personalizada;
•	Um método que reinicia essas chances de inimigos aparecerem;
•	Um método que faz com que os inimigos apareçam em lugares aleatórios;

Classe Game1
•	É definido o tamanho do ecrã;
•	São definidos os managers que são usados a maior parte do tempo;
•	É criado o jogo, carregado o conteúdo preciso e é criado o método de atualizar o jogo à medida que o tempo passa, e por fim o método que salva o jogo quando sai-se dele;

Class HelperUtils
•	É criado um método que converte um vetor para um angulo de rotação;
•	Um método que devolve um float aleatório entre um intervalo;
•	Um método que devolve um vetor criado a partir de um angulo e magnitude;
•	Um método que devolve uma cor a partir de valores hsv;
•	Um método que desenha uma string com origem no centro do ecrã, outro que desenha no meio do lado esquerdo do ecrã e outro que desenha no meio do lado direito do ecrã, e outro que desenha no ecrã num local qualquer do ecrã;

Classe Player
•	É defenida a recarga dos tiros do jogador;
•	É definida a recarga da utilização dos poderes do jogador:
•	É definido o estado do poder do jogador e a sua velocidade, assim como a velocidade do poder;
•	É definido um enum com os diversos estados de poderes;
•	É criado o jogador na sua forma báscia e as suas caraterísticas são postas em default;
•	Um método que trabalha o movimento do jogador (velocidade, posição, direção dos tiros, orientação)
•	Um método que trabalha os disparos (direção, recarga, dispersão)
•	Um método que faz com que o jogador dispare dois tiros de uma vez;
•	Um método que trabalha os diversos poderes do jogador;
•	Um método que faz com que o jogador tome dano;
•	Métodos que matam o jogador, consumir os diversos poderes, e desenhe o jogador;

Classe Pickup
•	Método pickup que carrega animações;
•	Outro método que carrega os power-ups (o tileset);
•	Método de destruir entidades;
•	Método de atualizar animações;
•	Método de desenhar uma entidade;

Classe PickupSpawner
•	Definição de variáveis básicas para o spawn;
•	Definição de tipos de poderes podem aparecer;
•	Criar um pick up spawner com as chances de spawnar default;
•	Criar um pick up spawner com as chances de spawnar custumizadas;
•	Um método para reiniciar as chances de spawnar;
•	Um método de atualizar esses spawns;
•	Um método que devolve uma posição de spawn aleatória;


Classe PlayerGUI
•	Definição das coordenadas onde vão ser mostrados os diversos elementos do GUI;
•	Método para desenhar todos os elementos do GUI (pontuação, vidas, nível, boss se aplicável, a parte de estar a fazer batota…);

Classe PlayerInput
•	Definição dos estados do teclado e do rato;
•	Método estático que vê a posição atual do rato;
•	Método que atualiza o estado do rato e do teclado;
•	Métodos que verificam se a tecla k estava ou está a ser pressionada;
•	Métodos que verificam se o botão esquerdo do rato estava ou está a ser pressionado;
•	Métodos que verificam se qualquer botão do rato está a ser pressionado;
•	Métodos que verificam se qualquer tecla está a ser pressionada;
•	Método que verifica a direção  em forma de um vetor;
•	Um método que verifica a posição do rato em relação a esse vetor;

Classe Program
•	Só utilizada para iniciar o jogo, como ponto de entrada da aplicação;

Classe Resources
•	Utilizada para criar variáveis estáticas com os elementos visuais necessários para o jogo e um método que carrega as texturas cores e o título do jogo;

 Classe SpritePlayer
•	Definidas várias variáveis que são usadas ao longo dos outros métodos, estando organizadas aqui para uma maior facilidade por parte do programador;
•	Um método que cria uma nova entidade no jogo a partir de uma sprite;

Classe Level
•	Um método que obtém o nome do nível através de uma estrutura switch case;
•	Um método que verifica se o jogador clica em teclas especificas para aceder a certas definições do jogo;
•	Um método que atualiza o nível em que o jogador se encontra depois de passar essa fase;
•	Um método que trata do desenho do nível (atualiza sprites, desenha partículas e o cursor e também o GUI);
•	Uma classe para o primeiro nível, com métodos para inciá-lo, inseri-lo e atualiza-lo, e desenhá-lo;
•	Isto repete-se para os 5 níveis;
•	Uma classe de nível splash, com métodos para carregar e descarregar o conteúdo, inserir e sair do nível, atualizar e desenhar esse nível;
•	Classe com o menu dos níveis, com um método para carregar esse menu, descarregar esse conteúdo, , inserir e sair do nível, o método que vê se o cursor com o menu, o método que atualiza e desenha o menu dos níveis;
•	Uma classe com as opções dos níveis, com o mesmo género de métodos;
•	Uma classe para quando o nível esta em pausa e os métodos do género dos anteriores;
•	Uma classe para quando o tutorial dos níveis e os métodos do género dos anteriores;
•	Uma classe para quando dá game over e os métodos do género dos anteriores;
•	Uma classe para quando o jogador ganha e os métodos do género dos anteriores;
•	Uma classe para o jogador vê os seus highscores e os métodos do género dos anteriores;

SpriteActor
Esta classe é o pai de todas as sprites
Método SpriteActor – constrói a sprite: textura, posição, velocidade e tamanho;
sprite.setHSoffset -> definir hot-spot
sprite.setBBToTexture -> colocar a sprite do tamanho da estrutura;

					HighScoreManager
Vai buscar as highscores ao ficheiro, se ele não existir cria um com elas
Método AddHighScore – adiciona o HighScore dependendo do nível 
1º verifica o score do player
2º vê se é maior que as outras pontuações
3º se for substitui
Método SaveHighScore- coloca a highscore no ficheiro acima referido
Método LoadHighScore – converte para uma classe e depois serializa para guardar num ficheiro

					ParticleManager
Método CreateExplosionEnemy – cria a explosão dos inimigos – efeitos especiais
Método CreateExplosionBoss – igual ao anterior mas para o Boss
Método setMaxParticleAmount – define o máximo de partículas que podem existir dependendo da qualidade do gráfico

					SpriteManager
Método addSpriteActor – se está a dar update às outras sprites continua se não, adiciona outra sprite com o método addInternal
Método addInternal – adicona a sprite como o seu tipo.
Método handleCollision – verifica que tipo de colisão é que aconteceu e diz o que fazer com ela
1º            // Handle collision between all types of enemies
2º             // Handle collision between bullets and enemies
3º	        // Handle collision between bullets and bullets
4º             // Handle collision between player and pickup
5º             // Handle collision between player and enemies
6º             // Handle collision between player and enemy bullets

Método clearScene – limpa tudo menos o player
Método isColliding – usado acima no método handleCollision, verifica se 2 sprites estão a colidir
					
SoundManager
Load the sounds

					SaveGameManager
Inicialize – guardar os highscores(no máximo 5)
SaveGame – salva os dados do jogo
SaveGameState – salva os dados para um ficheiro
LoadGameState – converte os dados para highScore data e guarda num ficheiro

					RC_Texture
setGraphicsDevice – define os gráficos para 0 ou 1 como visto anteriormente
RC_Texture – define a textura através do nome e ficheiro ou nome, ficheiro e index
setWithHeight – define a altura e a largura
loadFile – carrega a textura através de um ficheiro
setFilename 
Texture2D tex – se for igual a NULL carrega a textura do ficheiro. Depois returna a textura
RC_TextureList  - cria nova lista de textura
setGraphicsDevice – define os gráficos para 0 ou 1 como visto anteriormente
Texture2D findName – se o nome da textura for igual ao anterior returna a textura
Loop para encontrar o index da textura e coloca na variável j
Se a textura foi encontrada o nome anterior passa para o novo nome e o antigo index passa a j.
Add – cria e adiciona a textura

					RC_StringList					
Copy – limpa o array 1st e adiciona uma nova string
Add – adiciona a string ao array
Removeat – remove do array no tal index
saveToFile – guarda no ficheiro o array
readFromFile – adiona no array as strins que tiverem no ficheiro
getKeyIndex – pegar da lista o index em que contém o igual
getValueFromPair – retorna o que está depois do igual e retira os espaços
getValueFromPairBoll – verifica se no método anterior a key é “true”
getValueFromPairInt – igual ao antes do anterior mas com inteiro
getValueFromPairFloat – igual ao anterior com float usando o método a seguir 
getValueFromPairDouble – igual ao antes do anterior mas com double
setValuePair – verifica o index da key e iguala ao valor
clear – limpa o array

					RC_SpriteList
Cria uma lista de sprite e desenha-os. 





