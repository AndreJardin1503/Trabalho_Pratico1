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

- Classes "RC" - Classes mais abstratam que lidam com __ mais necessários para o bom funcionamento e fluido do programa/ jogo. Assim, cria texturas, pinta, muda tamanho de imagens, cria particulas, lida com eventos: mouseClick, MouseOver, colisões, metodos de ajuda para gerir e programar, cria retangulos que servem como hitBoxes e damageBoxes, basicamente para detetar eventos, cria um inputBox para pegar texto do utilizador,exibe texto

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

Sobre:
   As classes RCs vêm da RC_Framework, que foi criada por Robert Cox @ University de Canberra e que foi implementado na criação deste jogo. Como uma Framework, o programador só utiliza certas classes, já que algumas não são todas pertinentes. 

         RC_GUI:
      classe GUI_Globals:
//Global para todos os objetos gui, tudo public e static

initGUIGlobals(device, buttonFont, toolTipFont, defaultTextColor)
{
   //inicia uma gui, uma textura 2d de fundo, com texto de uma certa cor e fonte num certo lugar do ecrâ
}

desenhaToolTip(SpriteBatch sb)
{
   //se tiver algum texto para desenhar, desenha a gui, com o fundo do tamanho do texto para caber direito e depois desenha o texto
}

updateToolTips()
{
   //passado um tempo o texto desaparece
}

---------------------------------------------------------------------------------------

      classe GUI_Control: RC_RenderableBounded:
//Esta é a classe pai de todos os objetos gui

bool MouseDownEventLeft(mouse_x, mouse_y)
{
   //devolve um booleano que diz se o player clicou no lado esquerdo do rato ou não
}

bool MouseOver(mouse_x, mouse_y) //(eg tool tips)
{
   //devolve um booleano que diz se o player passou por cima com o rato ou não
}

desenhaSubControls(SpriteBatch sb) 
{
   //desenha todas as gui que forem para desenhar
}

public GUI_Control() 
{
   //Construtor basico
}

setToolTip(String texto)
{
   //renicia o tempo e coloca o texto para o tooltip
}

Clear()
{
   //remove todos os sub controles
}

AddControl(GUI_Control c)
{
   //adiciona um sub controlador, colocando este como filho de outro
}

GUI_Control getControl(int cnum)
{
   //retorna um controlador a partir do index
}

Boolean dentro(float x, float y)
{
   //devolve um booleano que diz se o ponto está dentro dos limites e se o controlador estiver visible = true
}

clearFocus(bool clearParent)
{
   //limpa a variavel focus no objeto e nos seus sub contolls
}

Vector2 getScreenPos()
{
   //pega a posição na tela, ajustada á posição dos pais
}

override bool KeyHitEvent(Keys keyHit)
{
   //devolve um booleano que diz se o o player clicou em uma tecla
}

bool passOnKeyhit(Keys keyHit)
{
   //devolve a tecla para os sub controlls
}

override Atualiza(GameTime gameTime)
{
   //atualiza todos os controles
}

setColor(Color c, bool passOn)
{
   //define a sua cor e a cor dos seus sub controlls, serve para controlar transparencia
}
---------------------------------------------------------------------------------------

      classe Frame: GUI_Control:
//classe gui simples com 1 imagem, normalmente usado como um recipiente para outras classes

Frame(Texture2D t, retangulo pos)
{
   //construtor basico
}

public override void Desenha(SpriteBatch sb)
{
   //Desenha o container e depois os SubControls
}
---------------------------------------------------------------------------------------

      Button2 : GUI_Control:
//classe gui simples com 2 imagens - button up e button down:

Button2(Texture2D upZ, Texture2D downZ, Vector2 pos)
{
   //construtor, define o tamanho das texturas
}

Button2(Texture2D upZ, Texture2D downZ, retangulo pos)
{
   //construtor basico
}

override void Desenha(SpriteBatch sb)
{
   //desenha basico, onde desenha up ou down, dependendo da variavel state ser 0 ou 1
}

override bool MouseDownEventLeft(float mouse_x, float mouse_y)
{
   //se o player clicou no lado esquerdo do rato no butão, muda a variavel state e retorna true
}
---------------------------------------------------------------------------------------

      ButtonSI : GUI_Control:
//Butão simples com 1 imagem 2 cores que muda quando clicado:

ButtonSI(Texture2D upZ, Color cClicked, Vector2 pos)
{
   //Construtor - redimensiona a textura
}

ButtonSI(Texture2D upZ, Color cClicked, retangulo pos)
{
   //Constructor basico
}

setText(String t, SpriteFont f)
{
   //define o texto e a font, é optional
}

override void Desenha(SpriteBatch sb)
{
   //desenha a cor dependendo se o botão está ou não a ser clicado, desenha tambem o texto e os SubControls 
}

override bool MouseDownEventLeft(float mouse_x, float mouse_y)
{
   //muda a variavel state e retorna true se o jogador clicar com o lado esquerdo do rato no botão
}

override void Atualiza(GameTime gameTime)
{
   //passado algum tempo desaparece mudando o estado e clicared=false
}
---------------------------------------------------------------------------------------

      TextBox : GUI_Control:
//simples controlar gui para exibição de texto

caixa de texto(Texture2D texZ, Vector2 pos, SpriteFont fonty, string s)
{
   //Construtor - redimensiona a textura
}

caixa de texto(Texture2D texZ, retangulo pos, SpriteFont fonty, string s)
{
   //Constructor basico
}

override void Desenha(SpriteBatch sb)
{
   //desenha a "caixa" que vai ter o texto, e desenha o texto
}

override bool MouseDownEventLeft(float mouse_x, float mouse_y)
{
   //lida com o clique esquerdo do mouse, mandando para os controles dos filhos
}

override void Atualiza(GameTime gameTime)
{
   //atualiza todos os controles:
}

override bool KeyHitEvent(Keys keyHit)
{
   //lida com a tecla clicada, mandando para os controles dos filhos
}
---------------------------------------------------------------------------------------

      InputBox : GUI_Control:
//pega o texto do utilizador:

InputBox(Texture2D texZ, Vector2 pos, SpriteFont fonty, string s, int maxLen)
{
   //redimensiona a caixa para a largura da imagem 
}

InputBox(Texture2D texZ, retangulo pos, SpriteFont fonty, string s, int maxLen)
{
   //Constructor basico
}

int asInteger()
{
   //tenta converter o texto do utilizador para inteiro 
}

override void Desenha(SpriteBatch sb)
{
   //desenha InputBox
   //desenha a "animação" para quando o utilizador clicar no lugar para escrever:
   //desenha SubControls
}

override void Atualiza(GameTime gameTime) 
{
   //atualiza a animação
}

override bool KeyHitEvent(Keys key)
{
   //ajuda o player a escrever "."/" "/numeros/apagar(Backspace)/submeter(Enter)
}

override bool MouseDownEventLeft(float mouse_x, float mouse_y)
{
   //se clicar dentro, manda para o controle dos filhos, limpa o focus dos pais, e torna este focus true
}
---------------------------------------------------------------------------------------

      StringListBox : GUI_Control:
//controlador gui para exibição de texto com multiplas linhas:

StringListBox(Texture2D texZ, retangulo pos, SpriteFont fonty, StringList slst)
{
   //Constructor basico
}

override void Desenha(SpriteBatch sb)
{
   //desenha caixa de texto, e desenha cada linha de texto e desenha SubControls
}

override bool MouseDownEventLeft(float mouse_x, float mouse_y)
{
   //se clicar dentro, manda para o controle dos filhos
}

override void Atualiza(GameTime gameTime)
{
   //Atualiza o controll, manda para o controle dos filhos
}

override bool KeyHitEvent(Keys keyHit)
{
   //lida com a tecla clicada, mandando para os controles dos filhos
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_Sound:
   //Limita um som a reproduzir um certo número de instâncias dele mesmo (para o som de ficar turvo):
LimitSound(SoundEffect soundEffect, int numOfSoundz)
{
   //Cria usando um soundeffect
}

LimitSound(string name, int numOfSoundz, ContentManager c)
{
   //cria usando o nome de um som
}

private void init()
{
   //cria um array para ter todos os sons
}

playSound()
{
   //toca o som do começo, depois de tocar para, e toca a proxima, e volta para a primeira no fim
}

playSoundIfOk()
{
   //se não tem nenhum som a tocar, encontra um que não está a tocar e começa a tocar  
}

Atualiza(GameTime gameTime)
{
   //atualiza o som
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_GameState:
      RC_GameStateParent:
//todos os niveis são filhos desta classe:

virtual void InitializeLevel(GraphicsDevice g, SpriteBatch s, ContentManager c, RC_GameStateManager lm)
{
   //começar nivel com sprites
}

//metodos criados para filhos da classe
public virtual void LoadContent() { }
public virtual void UnloadContent() { }
public virtual void EnterLevel(int paraLevelNum) { }
public virtual void ExitLevel() { }

public static void getKeyboardAndMouse()
{
   //pega inputs do teclado e do rato
}
---------------------------------------------------------------------------------------
      RC_GameStateManager:
//para gerir os niveis, os gameStates são telas, normalmente usado para os niveis mas 
///são para telas em geral como a tela de ajuda quando o player clica no botão de ajuda, 
////a tela de pausa do jogo, a tela que diz que tem o cheat ativado, etc:

/* variáveis: has states[], current_state, prev_state, curr_lvl_numb, ...*/

RC_GameStateManager()
{
   //inicia o processo de criar espaço para os RC_GameStateParent[], mandando a quantidade
}

private void init(int numLevelz)
{
   //tem os RC_GameStateParent[] numa var e coloca todos a null
   //inicia um nivel vazio
}

void AddLevel(int levNum, RC_GameStateParent lev)
{
   //adiciona um nivel
}

RC_GameStateParent getLevel(int levNum)
{
   //dá return em um nivel
}

void setLevel(int levNum)
{
   //coloca o prevState = cur, define o novo cur, limpa a tela e sai do nivel passado, 
   //limpa o nivel que estou agora e passa para outro, provavelmente o anterior
   ///desenha o novo, pega o estado do rato e do teclado para por exemplo:
   ////se estava a disparar continua a disparar no proximo nivel, e onde o player estava
}

void pushLevel(int levNum)
{
   //limpa o nivel que estou agora e passa, sem começar a jogar outro
}

int popLevel()
{
   //faz eu passar para o nivel anterior exemplo: se estivesse no nivel 3 passava para o 2
   ///e limpava o nivel 3, pega o estado do rato e do teclado para por exemplo: se estava 
   ////a disparar continua a disparar no proximo nivel, e onde o player estava
}

void setEmptyLevel()
{
   //coloca um nivel vazio
}

RC_GameStateParent getCurrentLevel()
{
   //retorna o nivel que está de momento
}

int getCurrentLevelNum()
{
   //retorna o numero do nivel que está de momento
}
---------------------------------------------------------------------------------------
      EmptyState : RC_GameStateParent:
//um nivel vazio para resolver uns problemas devido a estar a fazer Draw e update de nada

override void Desenha(GameTime gameTime)
{
   //não faz nada
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_RenderablesUtilText:
      RC_resizeText : RC_RenderableBounded:

public RC_resizeText(GraphicsDevice gd, string textZ, retangulo boundz, Color backGroundColor, Color foregroundColor)
{
   //contructor, define as variaveis
   //se o utilizador cria um foregroundColor branco, e a font do texto é branca vai re-colorir no Draw(), se o utilizador defenir cor
}

override void Desenha(SpriteBatch sb)
{
   //desenha o texto
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_RenderableMulti:
      MultiScrollBackGround : RC_RenderableBounded:

MultiScrollBackGround(retangulo boundsZ)
{
   //Contrutor, cria um retangulo
}

setScrollBackGrounds(ScrollBackGround sbb1, ScrollBackGround sbb2, ScrollBackGround sbb3)
{
   //cria os 'quadros', que dá para fazer scroll, no maximo 3
}

override void Atualiza(GameTime gameTime)
{
   //atualiza os 'quadros'
}

override void Desenha(SpriteBatch sb)
{
   //desenha os 'quadros'
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_PositionFactory:
      abstract classe RC_PositionFactory:
   //classe pai para todas as position factories: 
/* Variáveis:
   public abstract Vector2 getNextPos();
   public virtual void init() {}
   public virtual void reset() {}
   public virtual void desenha(SpriteBatch sb, Color col) { }
*/
---------------------------------------------------------------------------------------
      RC_posInrectangle : RC_PositionFactory:
//Cria posições dentro de um retangulo:

RC_posInrectangle(retangulo r, Random rndZ)
{
   //Contrutor, cria um retangulo
}

override Vector2 getNextPos()
{
   //retorna uma posição random no quadrado
}

override void desenha(SpriteBatch sb, Color col)
{
   //desenha o retangulo
}
---------------------------------------------------------------------------------------
      RC_posInCircle : RC_PositionFactory:
//Cria posições dentro de um circulo:

RC_posInCircle(Vector2 posZ, float radiusMinZ, float radiusMaxZ, Random rndZ)
{
   //construtor, cria um raio minimo, um raio maximo e uma posição
}

override Vector2 getNextPos()
{
   //retorna uma posição random no circulo, usando matematica(pi e cos e seno)
}

override void desenha(SpriteBatch sb, Color col)
{
   //desenha o circulo(o circulo com o minimo de raio e outro com o maximo)
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_Renderables:
      TextRenderable : RC_Renderable:
//esta classe é apenas uma unica linha de texto:

TextRenderable(string textZ, Vector2 posZ, SpriteFont fontZ, Color colourZ)
{
   //construtor, cria um texto em uma posição
}

public override void Desenha(SpriteBatch sb)
{
   //desenha o texto draw a text
}
---------------------------------------------------------------------------------------
      TextureFade : RC_Renderable:
//Desaparece gradualmente e redimensiona uma texture, no final pode entrar em loop, ficar inativa or voltar em reverso, é uma ferramenta usada para diferentes efeitos

TextureFade(Texture2D texZ, retangulo initFrameZ, retangulo finalFrameZ, Color initColourZ, 
Color finalColourZ, int fadeTicksZ) : base()
{
   //Construtor, cria uma textura
}

setLoop(int loopQ)
{
   //define se quando a textura chegar ao fim, vai acabar entrar em loop ou voltar invertida
}

override void Desenha(SpriteBatch sb)
{
   //desenha a textura
}

override void Atualiza(GameTime gameTime)
{
   //atualiza a textura, e lida com acabar, entrar em loop ou voltar invertida
}

override void Reset()
{
   //reinicia a textura
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_PanZoom:
      PanZoomStage : RC_Renderable:

PanZoomStage()
{
   //construtor, cria uma transição vazia
}

reset()
{
   //reinicia transição
}

override void Atualiza(GameTime gameTime)
{
   //faz transição até acabar, e acaba quando chegar a um certo numero
}

override void Desenha(SpriteBatch sb)
{
   //vai desenhando á medida que faz a transição
}
---------------------------------------------------------------------------------------
      PanZoomSequence : RC_Renderable:
/*var List<PanZoomStage> lst(list de transitions)*/

PanZoomSequence(retangulo destZ, Texture2D defaultTexZ, Color defaultColorZ)
{
   //construtor, cria uma transição, coloca ela do zero, inicia a lista vazia
}

reset()
{
   //reinicia transição, voltando ao zero 
}

addStage(PanZoomStage s)
{
   //adiciona uma transição á lista, e coloca ela do zero
}

addStage(Texture2D texZ, int ticksToTransitZ, Color initColourZ, Color finalColourZ,
         retangulo initDestZ, retangulo finalDestZ, retangulo initSourceZ, 
         retangulo finalSourceZ)
{
   //cria uma transição e adiciona á lista, e coloca ela do zero
}

addStage(int ticksToTransitZ, retangulo initSourceZ)
{
   //cria uma transição default com posição inicial e adiciona á lista, e coloca ela do zero
}

addStage(int ticksToTransitZ, retangulo initSourceZ, retangulo finalSourceZ)
{
   //cria uma transição default com posição inicial e final, e adiciona á lista, e 
   ///coloca ela do zero
}

bool Done()
{
   //retorna se já acabou a transição
}

override void Atualiza(GameTime gameTime)
{
   //passa por todas as frames das transiçôes da lista de transiçôes
}

override void Desenha(SpriteBatch sb)
{
   //desenha todas as transiçôes da lista de transiçôes
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_RenderableAttached:
      HealthBar : RC_RenderableAttached:
//healthbar classe para prender a um sprite, escolhe se a barra fica o tempo todo ou só quando recebe dano:

HealthBar(Color bar, Color backGround, Color barOffColorZ, int heightZ, bool alwaysDrawZ)
{
   //construtor, inicia as variaveis da barra
}

override void Desenha(SpriteBatch sb)
{
   //desenha a barra de vida
}
---------------------------------------------------------------------------------------
      AttachedText : RC_RenderableAttached:
//esta classe prende um pedaço de texto a um sprite pode ter o seu propio texto ou 
usar a propriedade de um texto do sprite:

AttachedText(Color colorZ, SpriteFont fontZ, Vector2 offsetZ, string textZ)
{
   //construtor, inicia as variaveis do texto
}

AttachedText(Color colorZ, SpriteFont fontZ, Vector2 offsetZ)
{
   //construtor, inicia as variaveis do texto, mas sem texto nenhum para usar o da 
   ///classe pai
}

AttachedText(Color colorZ, SpriteFont fontZ)
{
   //construtor, inicia as variaveis do texto, mas sem texto nenhum para usar o da 
   ///classe pai e coloca colado ao sprite
}

override void Desenha(SpriteBatch sb)
{
   //desenha o texto
}
---------------------------------------------------------------------------------------
      AttachedTextureFade : RC_RenderableAttached:
//Desaparece gradualmente e redimensiona uma texture, no final pode entrar em loop, ficar inativa or voltar em reverso

AttachedTextureFade(Texture2D texZ, retangulo initFrameZ, retangulo finalFrameZ, Color initColourZ, 
Color finalColourZ, int fadeTicksZ) : base()
{
   //Construtor, cria uma textura
}

setLoop(int loopQ)
{
   //define se quando a textura chegar ao fim, vai acabar entrar em loop ou voltar invertida
}

override void Desenha(SpriteBatch sb)
{
   //desenha a textura apegada/conectada ao sprite 
}

override void Atualiza(GameTime gameTime)
{
   //atualiza a textura, e lida com acabar, entrar em loop ou voltar invertida
}

override void Reset()
{
   //reinicia a textura
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_LineBatch:
      LineBatch:
//desenha linhas num spritebatch:
void init(GraphicsDevice device)
{
   //inicializa uma textura branca default 
}

void desenhaLine(SpriteBatch batch, Color color, Vector2 point1, Vector2 point2)
{
   //Desenha uma Unica linha
}

void desenhaLine(SpriteBatch batch, float x1, float y1, float x2, float y2, Color color)
{
   //Desenha uma Unica linha, com posições mais detalhadas que o metodo anterior
}

void desenhaLineRectangle(SpriteBatch batch, retangulo r, Color c)
{
   //desenha um retangulo com linhas
}

void desenhaLineRectangleOuter(SpriteBatch batch, retangulo r, Color c)
{
   //desenha um retangulo com linhas em volta de outro retangulo, e este retangulo é maior 1 pixel
}

void desenhaFillRectangle(SpriteBatch batch, retangulo r, Color c)
{
   //Desenha um retangulo preenchido com uma cor
}

void desenhaFillRectangleBorder(SpriteBatch batch, retangulo r, Color c, int bWidth)
{
   //Desenha um retangulo preenchido com uma cor, e uma borda, dando um aspeto mais 3d
}

void desenhaCrossX(SpriteBatch batch, float x1, float y1, float size, Color c1, Color c2)
{
   //Desenha com 2 linhas um X
}

void desenhaCross(SpriteBatch batch, float x1, float y1, float size, Color c1, Color c2)
{
   //Desenha 2 linhas um +
}

void desenhaRect4(SpriteBatch sb, Rect4 r, Color c)
{
   //desenha uma figura com 4 pontos
}

void desenhaPolygon12(SpriteBatch sb, Polygon12 r, Color c)
{
   //desenha um poligono de 12 lados 
}

void desenhaCircle(SpriteBatch sb, Color c, Vector2 center, float radius, int sides, float xScale)
{
   //Desenha um circulo, um circulo feito com linhas
}

void desenhaLine(SpriteBatch batch, Color color, Vector2 point1, Vector2 point2, float Layer)
{
   //Desenha uma linha num SpriteBatch, numa camada expecifica
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_Particle:
   struct Particle:
      position
      velocity
      bounds
      angle
      size
      Color

      ParticleSystem : RC_Renderable:
/* Variáveis:
   co-ordinates, time_que_lasts, velocity(randome can choose how much variates), angle
*/

ParticleSystem(Vector2 posZ, int MaxnumZ, int ticksSystemDurationZ, int randomSeed)
{
   //cria o template de uma particula
   //cria uma string de particulas e enche de particulas, depois reinicia-las
}

override void Reset()
{
   //reionicia todas as particulas
}

setMandatory1(Texture2D texZ, Vector2 startSizeZ, Vector2 endSizeZ, Color startColorZ, Color endColorZ)
{
   //define a aparencia da particula especifica
}

setMandatory2(int totalNumberTocriaZ, int initialNumberTocriaZ, int subsequentNumberTocriaZ,
               int ticksBetweencriaEventsZ, int random10000TocriaZ)
{
   //define a quantidade de particulas geradas
}

setMandatory3(int ticksParticleDurationZ,  retangulo boundsZ )
{
   //define os limites de onde a particula pode ir
}

setMandatory4(Vector2 deltaZ, Vector2 initialVelosityZ, Vector2 initialVelosityRandomZ)
{
   //define a velocidade da particula
}

activate()
{
   //ativa a particula
}

deActivate()
{
   //desativa a particula
}

ifSafeToRemoveDeActivate()
{
   //remove as particulas quando todas estiverem desativadas
}

criaParticles(int num)
{
   //tem uma lista das particulas que é preciso realizar, e passa para uma lista de 
   ///particulas realizadas que tem um maximo, ao passar pelo maximo para de gerar particulas
   //para todas as particulas não ativas, defina-las(velocidade, angulo, etc) e ativa-las
}

int Contains(Vector2 point)
{
   //procura uma particula ativa que contem um certo ponto
}

public override void Atualiza(GameTime gameTime)
{
   //atualiza as particulas, criando mais se poder
}

public void updateParticles()
{     
   //para todas as particulas ativas, atualizar a projeção e velocidade, e se chegarem 
   ///ao fim desativar e remover
}

public override void Desenha(SpriteBatch sp)
{
   //desenha todas as particulas ativas
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_RenderableParents:
      RC_Renderable:
//classe Pai para todos renderables sprites e lista de renderables para desenhar que estão activos, têm 
///cor, e são visiveis, carrega conteudo e atualiza funções, controla mouse 
////e keyhit functions, ajuda a fazer renderables com proposito geral:
RC_Renderable()
{
   //constructor simples
}

RC_Renderable(bool activeZ, bool visibleZ, Color colorZ)
{
   //constructor mais detalhado
}

RC_Renderable(RC_Renderable r)
{            
   //copia o constructor
}

virtual void setColor(Color c)
{
   //define uma cor para um sprite
}

Color getColor()
{
   //pega cor
}

///Standard:
   public virtual void Desenha(SpriteBatch sb)
   {
   }

   public virtual void Atualiza(GameTime gameTime)
   {
   }

   public virtual void LoadContent()
   {
   }

   public virtual void Reset()
   {
   }

setVisible(bool v)
{
   //define se a renderable é visivel
}

bool getVisible()
{
   //pega se é ou não visivel
}

virtual bool scrollMove(float x, float y)
{
//usado para dar scroll pela tela toda
   //se conseguiu retorna true 
}

//comportamentos por default devem tar em false:
   virtual bool MouseMoveEvent(MouseState ms, MouseState previousMs) { return false; }
   virtual bool MouseDownEventLeft(float mouse_x, float mouse_y) { return false; }
   virtual bool MouseUpEventLeft(float mouse_x, float mouse_y) { return false; }
   virtual bool MouseDownEventRight(float mouse_x, float mouse_y) { return false; }
   virtual bool MouseUpEventRight(float mouse_x, float mouse_y) { return false; }
   virtual bool KeyHitEvent(Keys keyHit) { return false; }
   virtual bool MouseOver(float mouse_x, float mouse_y){ return false; } //para tool tips e mouse overs
---------------------------------------------------------------------------------------
      RC_RenderableBounded : RC_Renderable:
//Esta classe é a pai para as classes renderable com um retangulo para bounds  
///permite defenir limites que redimensionam para zoom, não é para collision box (apesar de ser parecido):

override bool scrollMove(float x, float y)
{
   //usado para dar scroll pela tela toda - e preserva posição antiga
}

setWidthHeight(int w, int h)
{
   //define uma altura e largura
}

bool Contains(int x, int y)
{
   //Retorna true se a renderable contem um certo ponto x,y
}

retangulo Intersect(retangulo r)
{
   //Retorna um retangulo que é a intersecta deste renderable com outro retangulo
}

bool Intersects(retangulo r)
{
   //Retorna true se um retangulo intersecta com este renderable
}

Vector2 getSubLocation(int subLocNum)
{
   //Retorna um ponto em um retangulo 
}

bool inside(retangulo r)
{
   //Retorna true se estiver dentro do retangulo
}
---------------------------------------------------------------------------------------
      RC_RenderableAttached : RC_Renderable:
//classe pai para renderables que prendem a sprites que podem ser desenhados depois de outro sprite, bom para health bars e etc:

setParent(Sprite3 parentZ)
{
   //define um sprite para ser prendido a outro
}
---------------------------------------------------------------------------------------
      RC_RenderableList : RC_Renderable:
//uma list de renderables, onde inativos podem ter o seu lugar na lista reutilizado, por outros activos 

RC_RenderableList()
{
   //cria list de RC_Renderables
}

override void Desenha(SpriteBatch sb)
{
   //desenha cada renderable que estão active da list de renderables 
}

override void Atualiza(GameTime gameTime)
{
   //atualiza os renderables que estão active da list de renderables 
}

override bool scrollMove(float x, float y)
{
   //dá scroll a todos renderables, usedo para dar scroll á tela
}

override void LoadContent()
{
   //inicializa uma list com conteudo
}

addToEnd(RC_Renderable r)
{
   //Adiciona á lista
}

addReuse(RC_Renderable r)
{
   //Adiciona á lista reutilizando espaço da lista não mais preciso, para a lista não ficar muito grande
}

public int Count()
{
   //Counta a quantidade de renderables
}

Contains(float x, float y)
{
   //retorna o index do primeiro renderable que contem um certo ponto nele
}

collision(retangulo r)
{
   //retorna o index do primeiro renderable que está a colidir com um certo retangulo
}

override void setColor(Color c)
{
   //define a cor para todos os renderables ativos
}

override bool MouseOver(float mouse_x, float mouse_y)
{
   //se o rato estiver por cima retorna true
}

override bool MouseDownEventLeft(float mouse_x, float mouse_y)
{
   //se clicar com o lado esquerdo do mouse retorna true
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_RenderableBounded:
      ColorField : RC_RenderableBounded:
//este renderable é um retangulo com 1 cor:

ColorField(Color c, retangulo r)
{
   //cria aum retangulo com 1 cor
}

override void Desenha(SpriteBatch sb)
{
   //cria um retangulo com 1 cor
}
---------------------------------------------------------------------------------------
      TextRenderableBordered : RC_RenderableBounded :
//Uma linha de texto num frame com borda que tem ilusão 3D:

TextRenderableBordered(string textZ, retangulo posZ, SpriteFont fontZ, Color txtCcolor, Color backColor, int borderWidth)
{
   //define o TextRenderableBordered
}

override void Desenha(SpriteBatch sb)
{
   //desenha o TextRenderableBordered
}
---------------------------------------------------------------------------------------
      Button : RC_RenderableBounded:
//Uma linha de texto num frame com borda que tem ilusão 3D:

Button(Texture2D backGroundTex, string textZ, SpriteFont fontZ, Vector2 pos, Color fontColorZ, Color backColor)
{
   //define o button
}

override void Desenha(SpriteBatch sb)
{
   //desenha o button
}

override bool MouseOver(float mouse_x, float mouse_y)
{
   //vê se o mouse está por cima do button e se estiver muda de cor e return true
}
---------------------------------------------------------------------------------------
      GridBackGround : RC_RenderableBounded:
//cria uma grid de fundo



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_Surface:
      RC_Surface:
//O porposito desta classe é fornecer uma canvas, fornece maneiras de trabalhar com pixels sem ser preciso 
///carregar uma imagem, pode converter para uma textura que é necessário para ter uma surface



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_Utils3:
      Polygon12:
//cria um poligono de 12 lados e dá para rodá-lo:



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_Waypoint:
      WayPoint:
//cria um unico wayPoint numa certa posição, com a velocidade com que sprites vão até ele:

      WayPointList:
//cria uma wayPointList com diversos waypoints, maximo sendo 3:

//0=loop
//1=direção reversa
//2=fica invisivel/inativo
int wayFinished { get; set; }

criaPathCircle(Vector2 center, float radius, float startAngle, float angleIncrement, int steps, float speed, float Xscale)
{
   //controi um caminho circular com os waypoints
}

Desenha(SpriteBatch sb, Color cPoints, Color cLines)
{
   //desenha os waypoints
}



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_Utils2:
      Rect4:
//Uma classe que são 4 pontos, normalmente usadp para rodar retangulos, 
///ou poligonos, mas não necessariamente:

Cria()
Roda()
Create_rectangle_arround()
---------------------------------------------------------------------------------------
      Util:
//Apenas uma classe com metodos que podem vir a ser uteis

rotatePoint() - rotate in a given angle a point based on a given center
convertBetweenRadiansAndDegrees()
MovePoint()
GetAngleBetweenTwoPoints()
Copy a block de pixels from one image to another()
findFile()
createNewColor_LighterOrDarkerThanTheGivenOne()
CreateRectanglesInsideOfAnoarOrOutsideOrBeside()



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_UtilText:
      UtilTextSI:
//standard textures:

Texturas com colors que tem fade de top-left para bottom-right
---------------------------------------------------------------------------------------
      FontParent:
//classe pai para todos as bitmapped fontes guardadas em codigo:

Desenha um char num ponto no tamanho default ()
desenha um char num retangulo()
desenha uma string num ponto()
desenha uma string de um certo tamanho()
Desenha uma string com shadow effect()
desenha uma string num retangulo()
---------------------------------------------------------------------------------------
      SillyFont : FontParent:
//8x8 fonte que é defenida em codigo

SillyFontContructor - carrega a Fonte
---------------------------------------------------------------------------------------
      SillyFont16 : FontParent:
//fonte com o dobro do tamanho - tem menos blur



---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------



         RC_Sprite3:
      Sprite3Parent : RC_RenderableBounded:
/*hotspot, offset, position*/

defineVariables()
getVariables()
saveposition() - save x & y
restorePosition() - position = savedPosition
---------------------------------------------------------------------------------------
      Sprite3 : Sprite3Parent:
//hotspot e offset estão no mesmo sitio

bounds()
attacheRenderables() - prende renderables como lifeBars or valores se atingido, pode prender até 2
setVariables() - texture/position/name/state/speed/angle/hotspot&offset/width/height/color
saveposition() - salva x & y
restorePosition() - position = savedPosition
getVariables()
setVariables()
Create_rectangle_arround - como uma collision box por exemplo
collision() - vê se colide com alguma coisa
moveSprite()
scroll() - Usado para dar scroll da tela - preserva posição antiga
moveWayPointList() - movimenta um sprite pela lista de waypoints
boundingBoxEqualsWidth&Height - as a collision box por exemplo
desenhaInfo() - desenha bounding box hotspot
Set&GetFrames()
Set&GetNumberOfFrames()
setAnimationSequence() - define uma sequência de animações 
animationStart()
setAnimFinished() - quando animação acaba: 0=loop/1=invisible/2=inactive & invisible
DistanceBetweenSprites()
