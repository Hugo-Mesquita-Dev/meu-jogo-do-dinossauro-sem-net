# meu-jogo-do-dinossauro-sem-net

/////// html//////
<! DOCTYPE html>
<html lang="pt-br" >
<cabeça>
  <meta charset="UTF-8">
 <o título>Dio Dino Game</título>
 <link rel="stylesheet" href="estilo.css"></link>
 <script src="script.js" charset="UTF-8" adiar></script>
</cabeça>
<corpo>
  <div class="background">
    <div class="dino"></div>
  </div>
</corpo>
</html>

//////css/////

corpo {
 fundo: #fafafa;
}

. dino {
 posição: absoluta;
 inferior: 0;
 imagem de fundo: url (dino.png);
 largura: 60px;
 altura: 60px;
}

. cacto {
 posição: absoluta;
 largura: 60px;
 altura: 60px;
 inferior: 0;
 imagem de fundo: url (cactus.png);
}

. game-over {
 alinhamento de texto: centro;
 cor: #666;
 margem: 50px 0;
 fonte-família: arial;
}

@keyframes slideright {
  de {
 posição de fundo: 70000%;
  }
  para {
 posição de fundo: 0%;
  }
}

. fundo {
 posição: absoluta;
 inferior: 0px;
 imagem de fundo: url ('background.png');
 plano de repetição de fundo: repetição-x;
 animação: slideright 600s linear infinito;
 -webkit-animação: linear infinito dos anos 600;
 largura: 100%;;
 altura: 200px;
}

////// javascript ///////

 const dino = documento. consultaSelector('.dino');
fundo const  = documento. consultaSelector('.background');

vamos éJumping = falso;
let isGameOver = falso;
deixar posição = 0;

 manipulação de funçãoKeyUp(evento) { 
 se (evento. keyCode === 32) {
 se (! isJumping) {
      saltar();
    }
  }
}

salto de função() {
 isJumping = verdadeiro;

 deixar upInterval = setInterval(() => {
 se (posição >= 150) {
      Descendo
      clearInterval(upInterval);

 desaponteInterval  = setInterval() => {
 se (posição <= 0) {
          clearInterval(downInterval);
 isJumping = falso;
        } mais {
 posição -= 20;
 dino, o que está por fazer. estilo. inferior = posição + 'px';
        }
      }, 20);
    } mais {
      Subindo
 posição += 20;
 dino, o que está por fazer. estilo. inferior = posição + 'px';
    }
  }, 20);
}

função createCactus() {
 cacto const  = documento. criarElement('div');
 deixar o cactusPosition = 1000;
 deixar randomTime = Matemática. aleatório() * 6000;

 se (isGameOver) retornar;

 cacto. classList. adicionar('cacto');
 fundo. apêndiceChild(cacto);
 cacto. estilo. esquerda = cactusPosition + 'px';

 deixe leftTimer = setInterval() => {
 se (cactusPosition < -60) {
      Saiu da tela
 clearInterval (leftTimer);
 fundo. removerChild(cactus);
 } outra se (cactusPosition > 0 && cactusPosition < 60 && posição < 60) {
      Fim de jogo
 clearInterval (leftTimer);
 isGameOver = verdadeiro;
 documento. corpo. innerHTML = '<h1 class="game-over">Fim de jogo</h1>';
    } mais {
      cactusPosition -= 10;
 cacto. estilo. esquerda = cactusPosition + 'px';
    }
  }, 20);

 setTimeout (createCactus, randomTime);
}

criarCactus();
documento. addEventListener('keyup', handleKeyUp);
