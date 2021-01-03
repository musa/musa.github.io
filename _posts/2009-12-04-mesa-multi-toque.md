---
layout: post
title: Mesa Multi-toque
date: 2009-12-04 11:30:19.000000000 -02:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Projeto
tags: []
meta:
  _edit_last: '1'
  lead_image: /assets/images/2010/08/mesa01.png
  secondary_image: /assets/images/2010/08/mesa02.png
author:
permalink: "/musa/projetos/mesa-multi-toque/"
---
Nesse artigo são descritas as atividades realizadas durante duas fases do projeto Mesa Multitoque . A primeira fase foi a construção e testes dos aspectos de hardware do sistema. A segunda fase foi o desenvolvimento de software para a plataforma multitoque, com base nas ferramentas e bibliotecas Processing, CCV e TUIO.

[![pic_0116]({{ site.baseurl }}/assets/images/2009/12/pic_01161.jpg "pic\_0116")](/assets/images/2009/12/pic_01161.jpg)

Multitoque significa um conjunto de técnicas de interação que permite que um usuário controle aplicações gráficas no computador utilizando vários dedos. Um dispositivo multitoque geralmente consiste de uma tela de toque (que pode ser um display LCD, um quadro, uma parede, uma mesa, etc.) e um conjunto de softwares que trabalhe para reconhecer múltiplos pontos de toque na superfície, ao contrário de uma touchscreen tradicional, que apenas reconhece um ponto de toque na tela (NUI Group 2008).  
O NUI Group atua como uma comunidade que oferece suporte, documentação e eventos relacionados às interfaces multimodais, e em especial, interfaces multitoque. Segundo o NUI Group, existem cinco técnicas principais para desenvolver o hardware para a superfície multitoque, são elas:

1.Frustrated Total Internal Reflection (FTIR), criada por Jeff Han;  
2.Rear Diffused Illumination (Rear DI), utilizada no Microsoft Surface Table;  
3.Laser Light Plan (LLP), criada por Alex Popovich e utilizada no protótipo da Microsoft LaserTouch ;  
4.LED-Light Plane (LED-LP), desenvolvido por Nima Mota- medi;  
5.Diffused Surface Illumination (DSI), desenvolvido por Tim Roth.

Todas essas técnicas tem por base a visão computacional e conceitos de ótica (por meio de algum tipo de câmera). Apesar do sensoriamento ótico estar na base da maioria das técnicas, existem diversas outras técnicas de sensoriamento que podem ser utilizadas na criação de interfaces naturais e multitoque. Algumas delas incluem sensores de proximidade, acústicos, capacitivos, resistivos, de movimento, orientação e pressão. É normal a combinação de vários sensores para formar uma técnica multitoque particular.  
No projeto desenvolvido, **foi escolhido o modelo FTIR** pois é amplamente documentado na Internet, através de trabalhos como (Brand 2007). A Tabela 1 demonstra um quadro com as vantagens e desvantagens do modelo escolhido.

| **Vantagens** | **Desvantagens** |
| 

Não é necessária uma caixa fechada

_Blobs_<sup><em><a class="sdfootnoteanc" name="sdfootnote1anc" href="#sdfootnote1sym"><sup>1</sup></a></em></sup> possuem alto contraste

Permite _blobs_ com vários niveis de  
pressão

 | 

A construção exige uma matriz de LED's  
(é necessário soldagem)

Exige uma superfície adequada

Não reconhece formas mais complexas como  
_tags fiducials_

 |

**Tabela 1 Vantagens e desvantagens do modelo FTIR (NUI Group 2008).**

A configuração do modelo multitoque FTIR envolve três componentes principais: uma tela de acrílico transparente, uma matriz de LED's infravermelhos e uma câmera com filtro infravermelho.&nbsp; Os raios infravermelhos compõem uma porção do espectro luminoso que se localiza um pouco além do que o olho humano pode observar. Trata-se de uma faixa de comprimento de onda mais longa que a luz visível, porém mais curta que as microondas. No que diz respeito à tecnologia multitoque, a luz infravermelha é utilizada para distinguir entre uma imagem visível projetada na superfície de acrílico e os pontos de toque dos dedos que serão mapeados. Sem os LED's infravermelhos e um filtro infravermelho na câmera, haveria confusão entre as imagens visíveis na tela de acrílico e o movimento dos dedos (NUI Group 2008).  
Os LEDs são arranjados em torno da tela de acrílico, dessa forma eles brilham diretamente na superfície da tela. Uma vez que os LED's infravermelhos são posicionados dentro do acrílico, a luz infravermelha atinge o topo e a base do acrílico em um ângulo aproximadamente paralelo, sendo esse efeito conhecido por reflexão interna total (do inglês Total Internal Reflection), como demonstra a Figura 1.

![MesaMultitoque_html_m37c681f0]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_m37c681f0.png "MesaMultitoque\_html\_m37c681f0")

**Figura 1 Efeito de Reflexão Interna Total de um LED infravermelho em uma tela de acrílico (Castle 2009).**

Esse efeito acontece em determinados materiais quando a luz passa de um material para outro com um índice de refração maior e com um ângulo de incidência maior que um ângulo específico. Esse ângulo específico depende do índice de refração de ambos os materiais, sendo conhecido como ângulo crítico, cujo cálculo pode ser efetuado através da lei de Snell. Quando um dedo é pressionado contra o acrílico, uma parte da luz é refletida para baixo através da tela, sendo em seguida detectada pela câmera, como demonstra a Figura 2:

![MesaMultitoque_html_m6c6d40a0]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_m6c6d40a0.png "MesaMultitoque\_html\_m6c6d40a0")

**Figura 2 Resultado da reflexão da luz infravermelha quando um dedo é pressionado na tela de acrílico (Castle 2009)**

No modelo de Mesa Multitoque construído, foram utilizados 38 LED'S infravermelhos, distribuídos em duas arestas de 17 LED'S cada. Para a alimentação, foi reaproveitada uma fonte AT que estava em um computador antigo, sem uso. Como esse tipo de LED suporta entre 1,5 e 1,6V, para uma tensão de alimentação de 5V fez-se necessária uma configuração de 6 circuitos paralelos, com 5 circuitos de 3 LED's ligados em série e um circuito com 2 LED's ligados em série, como demonstra a Figura 3.

![MesaMultitoque_html_m3d5e259d]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_m3d5e259d.png "MesaMultitoque\_html\_m3d5e259d") **Figura 3 Circuito da matriz de LED's de uma das arestas.**

A Figura 4 demonstra uma das arestas sendo construída, com o posicionamento dos LED's infravermelhos.

![MesaMultitoque_html_m5a4d132a]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_m5a4d132a.jpg "MesaMultitoque\_html\_m5a4d132a")

**Figura 4 Construção da aresta de LED's.**

A Figura 5 demonstra a aresta sendo posicionada na mesa, com os LED's infravermelhos ligados.

![MesaMultitoque_html_m452ec9ed]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_m452ec9ed.jpg "MesaMultitoque\_html\_m452ec9ed") **Figura 5 Posicionamento da aresta de LED's na mesa.**

Para a imagem ser projetada na tela de acrílico, um projetor Datashow é utilizado, e um espelho serve de suporte tanto para refletir a imagem, como para a câmera realizar a captura, como demonstra a Figura 6, que apresenta um esquema geral da Mesa Multitoque.

![MesaMultitoque_html_36f1cb86]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_36f1cb86.jpg "MesaMultitoque\_html\_36f1cb86")

**Figura 6 Esquema da Mesa Multitoque construída.**

A câmera utilizada para a construção da Mesa Multitoque foi a Sony PS3Eye (padrão no videogame Playstation 3). A documentação do NUI Group recomenda a utilização dessa câmera, por possuir uma taxa de 120 frames por segundo em uma resolução de 320x240 pixels.

**Processing**

Processing é uma linguagem de programação open source criada por Ben Fry e Casey Reas e voltada para a produção e processamento de imagens, animações e interações, através de objetos OpenGL. É uma linguagem muito utilizada por estudantes, artistas, designers e pesquisadores para o aprendizado, prototipação e produção de tecnologias computacionais visuais. É utilizada também para ensinar o fundamental de programação para iniciantes, pois conta com uma sintaxe clara e simples, onde pode-se desenhar objetos gráficos com muita facilidade (Fry 2007).

O ambiente integrado de desenvolvimento (IDE) Processing foi desenvolvido com base em Java, o que facilita a portabilidade do ambiente para diferentes sistemas operacionais como GNU/Linux, Mac OS X e MS-Windows, devido à maquina virtual JVM.&nbsp; A Figura 7 demonstra o ambiente de desenvolvimento do Processing:

![MesaMultitoque_html_76f3148c]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_76f3148c.png "MesaMultitoque\_html\_76f3148c") **Figura 7 IDE Processing.**

Os programas escritos em Processing organizam-se basicamente em torno de duas funções principais, a função setup e a função draw. A função setup é responsável pela configuração de parâmetros como o tamanho da janela onde o programa será executado, a cor do plano de fundo e se o programa executará em loop ou apenas uma única vez. A função draw, como o nome indica, irá realizar os desenhos na tela e pode ser considerada como a função principal de um programa em Processing.  
A Figura 8 demonstra, na janela do lado direito um código simples em Processing, para desenhar um retângulo de dimensões 50x30 pixels, e no lado esquerdo o resultado do código executado.

![MesaMultitoque_html_76f3148c]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_76f3148c.png "MesaMultitoque\_html\_76f3148c")**Figura 8 Código Processing para desenhar um retângulo (Barbeiro 2009).**

No código em questão, a primeira linha da função setup indica que a janela deverá ter a dimensão de 200x200 pixels. A segunda linha indica que o plano de fundo deverá ter a cor preta (0), e a terceira linha indica que o programa não deve ser executado em loop – para um programa simples que apenas desenha um objeto, isso é interessante para evitar consumo computacional desnecessário, pois por padrão todo programa em Processing executa a função draw em loop infinito. Já a função draw, apenas executa a função rect(), responsável por desenhar um retângulo com as dimensões de altura e largura dadas, em pixels.  
Um fato interessante sobre o Processing é que ele foi readaptado para ser utilizado como ambiente de programação para microcontroladores Atmega através do projeto de hardware livre Arduino.

**CCV**

Community Core Vision, ou CCV (conhecido anteriormente como tbeta), é um aplicativo open source para visão e sensoriamento computacional, muito útil na construção de aplicações multitoque. O CCV recebe como entrada um sinal de vídeo, para realizar um mapeamento no sinal e retornar como saída as coordenadas e o tamanho de um blob e eventos que descrevem a direção do movimento de um dedo ou se um dedo foi pressionado ou solto. O CCV suporta webcams internas e externas, assim como pode conectar-se a diversas aplicações TUIO/OSC/XML. Ele suporta diversas técnicas de multitoque, como FTIR, DI, DSI e LLP.  
A Figura 9 demonstra um diagrama com o ambiente de trabalho CCV.

![MesaMultitoque_html_m62e1d266]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_m62e1d266.jpg "MesaMultitoque\_html\_m62e1d266") **Figura 9 Ambiente principal do CCV.**

De acordo com o diagrama apresentado, o ambiente de trabalho do CCV é composto pelos seguintes itens:  
1. Source Image – Exibe o vídeo&nbsp; de entrada;  
2. Use Camera Toggle – Atribui a câmera como fonte de entrada e grava frames da câmera selecionada;  
3. Use Video Toggle - Atribui um arquivo de vídeo como fonte de entrada e grava frames do mesmo;  
4. Botão Previous Camera – Seleciona o dispositivo de câmera anterior, caso haja mais de um;  
5. Botão Next Camera – Seleciona o próximo dispositivo de câmera;  
6. Tracked Image – Exibe o resultado final sobre o vídeo após o mapeamento de blobs;  
7. Show IDs Toggle – Exibe o ID de cada blob mapeado;  
8. Show Outlines Toggle – Exibe círculos de cor rosa em torno dos dedos no vídeo de entrada;  
9. Controle de Threshold – Ajusta o nível de pixels aceitáveis no mapeamento: pixels com valor menor ao threshold serão removidos e os de valor superior serão aceitos no mapeamento.  
10. Botão Remove Background –&nbsp; Recapturar uma imagem de fundo estática;  
11. Dynamic Subtract Toggle – Ajusta dinamicamente a imagem de fundo, útil para o caso de falsos blobs ocorrerem devido a mudança de luzes no ambiente.  
12. Controle de Smooth – Suaviza a imagem e filtra ruídos;  
13. Controle de Highpass Blur – Remove as partes borradas da imagem e mantém as partes mais brilhantes  
14. Highpass Noise – Filtra o ruído da imagem após passar o filtro passa-alta;  
15. Controle Amplify – Amplifica o brilho dos pixels mais fracos – útil para amplificar os blobs;  
16. On/Off&nbsp; - Ativa ou desativa os filtros;  
17. Camera Settings&nbsp; – Altera configurações da câmera;  
18. Flip Vertical&nbsp; – Inverte verticalmente o vídeo de entrada;  
19. Flip Horizontal – Inverte horizontalmente o vídeo de entrada.  
20. GPU Mode – Ativa a aceleração de hardware 3D (GPU);  
21. Send TUIO – Ativa o envio de mensagens TUIO;  
22. Enter Calibration – Inicia o processo de calibração;  
23. Save Settings – Salva a configuração atual.

Um processo que não costuma ser trivial é a configuração do CCV para reconhecer os dispositivos de câmera instalados no computador. Antes de tudo, para se realizar a captura com uma câmera comum, já detectada corretamente pelo kernel Linux, é necessário fazer o download do código fonte da&nbsp; biblioteca unicap, para então compilar a mesma. Isso pois, o CCV realiza a captura de vídeo com base nessa biblioteca, apesar da mesma não ser distribuída no pacote CCV.

No caso do sistema desenvolvido, o objetivo é a utilização da câmera PS3Eye, pois trata-se de um dos modelos de câmera recomendados pelo NUI Group. Para isso, é preciso fazer o download do driver da câmera, que funciona apenas para a versão 2.6.30 do kernel Linux. Para o caso de um sistema Debian:

$ sudo aptitude install linux-image-2.6.30-bpo.1-686 linux-headers-2.6.30-bpo.1-686

Após isso, basta reiniciar o computador a partir do novo kernel e instalar o driver com os comandos:

$ sudo aptitude install mercurial  
$ hg clone http://linuxtv.org/hg/~jfrancois/gspca/  
$ cd gspca  
$ make release  
$ make  
$ make install

Em seguida, é necessário aplicar um patch na biblioteca unicap, para o driver gspca da PS3Eye. Como o patch desenvolvido é para o unicap 0.9.5 e a versão atual do unicap é 0.9.7, é necessário então fazer uma pequena modificação no arquivo de patch, substituindo o número de versão no arquivo. Com o comando sed, não é necessário nem abrir o arquivo para realizar a modificação:

$ sed -i 's/0.9.5/0.9.7/g' "unicap-gspca.patch"

Após isso, o patch pode ser aplicado com sucesso:

$ patch -p0 \< unicap-gspca.patch

Para utilizar o CCV com uma câmera e um projetor, é necessário antes executar o processo de calibração. A calibração permite que pontos de toque alinhem-se com os elementos na tela. Dessa forma, ao tocar algo exibido na tela, o toque é registrado na localização correta. Para que isso seja possível, o CCV necessita traduzir o espaço da câmera para o espaço da tela. Isso é feito com o toque nos pontos de calibração.

**TUIO**

TUIO é um framework que define um protocolo comum em uma API para superfícies multitoque tangíveis. O protocolo TUIO permite a transmissão de um descritor abstrato para superfícies interativas, incluindo eventos de toque e estados de objetos tangíveis. O TUIO codifica dados de controle de uma aplicação de mapeamento (como o CCV) e envia o sinal para qualquer cliente capaz de decodificar os dados no formato do protocolo (como o Processing).  
Tecnicamente,&nbsp; o TUIO é baseado no Open Sound Control (OSC) – um padrão emergente para ambientes interativos que não limita-se apenas ao controle de instrumentos musicais. Por tratar-se de um protocolo baseado em UDP, o OSC permite comunicação em rede, onde aplicações interativas podem comunicar-se remotamente.  
Desde que foi publicada a primeira especificação do protocolo TUIO&nbsp; como parte do sintetizador reacTable, o protocolo passou a ser adotado por diversos outros projetos relacionados à interfaces tangíveis e multitoque, como o trabalho desenvolvido pelo NUI Group.

**Exemplo de Aplicação: Pilha Multioque**  
O aplicativo de pilhas multitoque foi desenvolvido para o sistema operacional Debian GNU/Linux 5.0 executando Kernel 2.6.30 em uma máquina Intel Centrino Core2Duo 1.8 Ghz, com 4Gb de RAM. Porém, todas as ferramentas utilizadas podem ser portadas sem maiores problemas para outros sistemas operacionais.  
O proposto é que seja possível manipular com os dedos a representação gráfica de estruturas de dados tais como pilhas, listas e árvores. Para isso, inicialmente é necessário realizar uma integração entre as ferramentas CCV e Processing.  
A comunicação entre CCV e Processing é realizada através de mensagens TUIO, com a utilização da biblioteca TuioProcessing, como demonstra o diagrama da Figura 10.

![MesaMultitoque_html_m773d2ca9]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_m773d2ca9.png "MesaMultitoque\_html\_m773d2ca9") **Figura 10 Integração do CCV com o Processing.**

Por padrão, o CCV envia mensagens TUIO pelo protocolo OSC, para o endereço de IP 127.0.0.1 (localhost), através da porta 3000. Dessa forma, ao instanciar um objeto como cliente TUIO no Processing, deve-se especificar a porta 3000:

TuioProcessing tuioClient;  
tuioClient&nbsp; = new TuioProcessing(this, 3000);

Isso é necessário, pois por padrão o TuioProcessing utiliza a porta 3333. O exemplo desenvolvido é de uma pilha manipulável, como demonstra a Figura 11.

![MesaMultitoque_html_5c086c01]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_5c086c01.png "MesaMultitoque\_html\_5c086c01") **Figura 11 Representação gráfica de uma pilha em Processing.**

Uma pilha pode ser construída em Processing a partir de conjuntos de retângulos interligados verticalmente, onde cada retângulo representa um elemento de dado&nbsp; a ser inserido na estrutura. A pilha inicia vazia, e ao inserir o primeiro elemento, tem-se apenas o topo. Ao inserir outro elemento, arrastando um dedo até a localização da pilha, é permitido apenas que o novo elemento passe a ser o novo topo. Ao arrastar dois dedos sobre a pilha, desempilha-se o elemento do topo.  
Para arrastar os objetos em Processing, os retângulos foram desenvolvidos como objetos Spring2D, que possuem uma massa e são submetidos a uma gravidade artificial. Isso faz com que pareça mais real a manipulação dos objetos. A classe Spring3D possui o seguinte código:

class Spring2D {  
float vx, vy; // Velocidade em x e y  
float x, y; // Posição x e y  
float gravity;  
float mass;  
float radius = 20;  
float stiffness = 0.2;  
float damping = 0.7;

// construtor da classe:  
Spring2D(float xpos, float ypos, float m, float g) {  
x = xpos;  
y = ypos;  
mass = m;  
gravity = g;&nbsp;&nbsp; }

// atualiza posição e velocidade:  
void update(float targetX, float targetY) {  
float forceX = (targetX - x) \* stiffness;  
float ax = forceX / mass;  
vx = damping \* (vx + ax);  
x += vx;  
float forceY = (targetY - y) \* stiffness;  
forceY += gravity;  
float ay = forceY / mass;  
vy = damping \* (vy + ay);  
y += vy;&nbsp;&nbsp; }

// exibe o retângulo  
void display(float nx, float ny) {  
noStroke();  
rect(x,y,90,90);&nbsp; }  
}

A declaração de 3 objetos, s1 , s2 e s3, resulta graficamente numa pilha com 3 elementos, como foi demonstrado na Figura 5. Os objetos são declarados da seguinte maneira:

Spring2D s1, s2, s3;  
float gravity = 6.0; // valor da “gravidade”  
float mass = 2.0; // valor da “massa”

s1 = new Spring2D(0.0, width/2, mass, gravity);  
s2 = new Spring2D(0.0, width/2, mass, gravity);  
s3 = new Spring2D(0.0, width/2, mass, gravity);

Quanto maior o valor da gravidade e da massa, mais lentamente o objeto será arrastado na tela. Para que a pilha seja controlada por coordenadas x e y provenientes dos toques na superfície da mesa, é preciso realizar um mapeamento das mesangens TUIO enviadas pelo CCV, com a seguinte sequência de códigos:

// coleta todos os cursores x/y do tuio  
Vector tuioCursorList = tuioClient.getTuioCursors();  
for (int i=0;i\<tuioCursorList.size();i++) {  
TuioCursor tcur = (TuioCursor)tuioCursorList.elementAt(i);  
Vector pointList = tcur.getPath();

if (pointList.size()\>0) {  
stroke(0,0,255);  
TuioPoint start\_point = (TuioPoint)pointList.firstElement();;  
for (int j=0;j\<pointList.size();j++) {  
TuioPoint end\_point = (TuioPoint)pointList.elementAt(j);  
start\_point = end\_point;  
}  
} }

A Figura 12 exemplifica o uso do aplicativo desenvolvido, onde há uma pilha cujo quarto elemento será inserido como novo topo, única posição onde se permite a conexão de novos elementos.

![MesaMultitoque_html_402e7a5c]({{ site.baseurl }}/assets/images/2009/12/MesaMultitoque_html_402e7a5c.jpg "MesaMultitoque\_html\_402e7a5c") **Figura 12 Manipulação de uma pilha multitoque.**

Ao tentar arrastar com dois dedos um elemento para fora da pilha, só será possível se o mesmo for o elemento do topo.&nbsp; O topo inicia na posição central da tela:

s1.update(width/2, height/2);  
s1.display(width/2, height/2);

A conexão do topo com os outros elementos da pilha foi desenvolvida fixando-se a posição dos elementos, sempre alinhados verticalmente. Os objetos foram localizados na posição do topo somando-se 70 pixels abaixo a partir das coordenadas do topo (objeto s1):

s2.update(s1.x, s1.y+70);  
s2.display(s1.x, s1.y+70);  
s3.update(s2.x, s2.y+70);  
s3.display(s2.x, s2.y+70);

A aplicação desenvolvida encontra-se em estágio de protótipo, numa fase intermediária de desenvolvimento. Tem-se como planos mapear operações com maior números de pontos de toque, assim como extender para operar com outras estruturas de dados como árvores, listas, multi-listas, etc.

[![pic_0081]({{ site.baseurl }}/assets/images/2009/12/pic_0081.jpg "pic\_0081")](/assets/images/2009/12/pic_0081.jpg)

[![pic_0084]({{ site.baseurl }}/assets/images/2009/12/pic_0084.jpg "pic\_0084")](/assets/images/2009/12/pic_0084.jpg)

[![pic_0086]({{ site.baseurl }}/assets/images/2009/12/pic_0086.jpg "pic\_0086")](/assets/images/2009/12/pic_0086.jpg)

[![pic_0087]({{ site.baseurl }}/assets/images/2009/12/pic_0087.jpg "pic\_0087")](/assets/images/2009/12/pic_0087.jpg)

[![pic_0088]({{ site.baseurl }}/assets/images/2009/12/pic_0088.jpg "pic\_0088")](/assets/images/2009/12/pic_0088.jpg)

[![pic_0092]({{ site.baseurl }}/assets/images/2009/12/pic_0092.jpg "pic\_0092")](/assets/images/2009/12/pic_0092.jpg)

[![pic_0079]({{ site.baseurl }}/assets/images/2009/12/pic_0079.jpg "pic\_0079")](/assets/images/2009/12/pic_0079.jpg)

[![pic_0139]({{ site.baseurl }}/assets/images/2009/12/pic_0139.jpg "pic\_0139")](/assets/images/2009/12/pic_0139.jpg)

[![pic_0125]({{ site.baseurl }}/assets/images/2009/12/pic_0125.jpg "pic\_0125")](/assets/images/2009/12/pic_0125.jpg)

[![pic_0120]({{ site.baseurl }}/assets/images/2009/12/pic_0120.jpg "pic\_0120")](/assets/images/2009/12/pic_0120.jpg)

