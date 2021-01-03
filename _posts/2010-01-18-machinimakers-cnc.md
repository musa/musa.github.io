---
layout: post
title: Machinimakers CNC
date: 2010-01-18 15:54:46.000000000 -02:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Blog
tags:
- arduino
- cnc
- eletrônica
- lcd
- machinimakers
- pcb
- puredata
- sprint
meta:
  _edit_last: '7'
  secondary_image: /assets/images/2010/08/cnc02.png
  lead_image: /assets/images/2010/08/cnc01.png
author:
permalink: "/musa/blog/machinimakers-cnc/"
excerpt: Depois do Encontro de Laboratórios da Audiência Zero que decorreu em Dezembro
  passado, onde Alan e Dino estiveram presentes realizando atividades, ficou a ideia
  de repetir de uma forma regular aquele tipo de trabalho colaborativo intenso e altamente
  focado.  [...]
---
Depois do [Encontro de Laboratórios da Audiência Zero](http://labcd.org/2009/12/06/encontro-labs-az/) que decorreu em Dezembro passado, onde Alan e Dino estiveram presentes realizando atividades, ficou a ideia de repetir de uma forma regular aquele tipo de trabalho colaborativo intenso e altamente focado.

Foi assim que nasceram os [Lab Sprints AZ](http://audienciazero.org/docs/), sessões de trabalho mensais em que os membros dos labs se juntam em equipes para trabalhar em projetos concretos num fim de semana.

De início, pegamos num projeto antigo dos Machinimakers, um meta projeto do [Laboratório de Criação Digital](http://labcd.org/) com o objetivo de montar máquinas para uso no lab, a CNC. O projeto voltou à tona recentemente porque surgiu a necessidade de fabricar PCBs para um projeto do LCD e apesar dos resultados interessantes das experiências de etching que fizeram no verão passado, a ideia de usar um processo com químicos tóxicos nunca foi de inteiro agrado, e usar uma CNC para gravar as PCBs pareceu uma alternativa bastante viável.

Claro que construir uma CNC fiável a partir do zero é um projeto impossível para um fim de semana, por isso colocamos o objetivo do sprint de forma mais humilde, mas mesmo assim ambiciosa: criar um protótipo funcional de uma CNC controlada manualmente por um joystick, demonstrável através do uso da máquina para mover uma caneta e desenhar sobre uma folha de papel.

A equipe intercontinental que reuniu-se para este projeto era composta por Pedro Ângelo e pelo Ricardo Lobo do [LCD](http://labcd.org/), pelo Tiago Serra do [xDA](http://www.audienciazero.org/xda/), e pelo Alan Fachini e Dino Magri do [MuSA](https://musa.github.io).

Começamos por atacar a pilha de material informático velho à procura de peças que pudessemos usar para construir a máquina.

<center>
<br>
[caption id="attachment_695" align="aligncenter" width="461" caption="Reaproveitando peças de impressoras"]<a href="http://labcd.org/wp-content/uploads/2010/01/sucata.jpg"><img class="size-full wp-image-695 " title="sucata" src="/assets/images/2010/01/sucata.jpg" alt="Reaproveitando peças de impressoras" width="461" height="308"></a>[/caption]<br>
</center>
  
Um par de impressoras forneceram os eixos e os motores, os componentes principais, e o resto da estrutura foi montada a partir de pedaços de madeira encontrados na oficina e o nosso termoplástico favorito, a cola quente.  
<center>
<br>
[caption id="attachment_696" align="aligncenter" width="461" caption="Estrutura da CNC pronta"]<a href="http://labcd.org/wp-content/uploads/2010/01/estrutura.jpg"><img class="size-full wp-image-696 " title="estrutura" src="/assets/images/2010/01/estrutura.jpg" alt="Estrutura da CNC pronta" width="461" height="306"></a>[/caption]<br>
</center>
  
A eletrónica que controla os motores foi adaptada de umas experiências realizadas durante o ano passado para um outro projeto do LCD. O circuito foi escolhido por ser simples de montar numa breadboard e por termos os componentes disponíveis. O conjunto é controlado por um Arduino com um firmware muito simples que recebe uma direção pela porta serial e move o motor correspondente.

<center>
<br>
[caption id="attachment_697" align="aligncenter" width="461" caption="Eletrônica"]<a href="http://labcd.org/wp-content/uploads/2010/01/eletronica.jpg"><img class="size-full wp-image-697 " title="eletronica" src="/assets/images/2010/01/eletronica.jpg" alt="Electrônica" width="461" height="306"></a>[/caption]<br>
</center>

Para a demonstração propriamente dita, ligamos um joystick ao PC e criamos um patch no Pure Data que converte o movimento dos eixos do joystick em valores e os envia ao Arduino pela porta serial e o resultado é este:

<center>
<br>
<object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" width="400" height="225" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,40,0"><param name="allowfullscreen" value="true">
<param name="allowscriptaccess" value="always">
<param name="src" value="http://vimeo.com/moogaloop.swf?clip_id=8815014&amp;server=vimeo.com&amp;show_title=0&amp;show_byline=0&amp;show_portrait=0&amp;color=ffffff&amp;fullscreen=1">
<embed type="application/x-shockwave-flash" width="400" height="225" src="http://vimeo.com/moogaloop.swf?clip_id=8815014&amp;server=vimeo.com&amp;show_title=0&amp;show_byline=0&amp;show_portrait=0&amp;color=ffffff&amp;fullscreen=1" allowscriptaccess="always" allowfullscreen="true"></embed></object><br>
<a href="http://vimeo.com/8815014">CNC machine (first tests)</a> from <a href="http://vimeo.com/serratiago">Tiago Serra</a> on <a href="http://vimeo.com">Vimeo</a>.<br>
</center>

Foi um fim de semana intenso e muito divertido, que nos deixou cheios de ideias para continuar a desenvolver este projeto em próximos sprints. Se estiverem interessados podem encontrar o código e mais informação sobre o projeto na [página do sprint](http://audienciazero.org/docs/public/labs/events/sprints/jan-2010/start), e claro, envolverem-se na preparação do próximo.

Vejam mais fotos do decorrer das atividades no [Flickr](http://www.flickr.com/photos/tserra/sets/72157623110047679/).

Queremos agradecer a toda a malta dos labs AZ, [LCD](http://labcd.org/), [xDA](http://xdatelier.org/) e [Altlab](http://www.altlablx.org/) por todo o companheirismo, sendo sempre muito receptivos. Com certeza essa interação intercontinental fará diferença para a construção do MuSA.

