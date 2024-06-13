//varíaveis da Bolinha
let xBolinha = 300;
let yBolinha = 200;
let diametro = 30;
let radio = diametro /2;
let raqueteComprimento = 10;
let raqueteAltura = 90;


//velocidade da Bolinha
let velocidadeXBolinha = 6;
let velocidadeYBolinha = 6;

//variaveis da raquete
let xRaquete = 5;
let yRaquete = 150;

let xRaqueteOponente = 585;
let yRaqueteOponente = 150;
let velocidadeYOponente;

let colidiu = false

function setup() {
  createCanvas(600, 400);
  
}

function draw() {
  background(0);
  mostraBolinha();
  movimentaBolinha();
  verificaColisaoBordas();
  mostraRaquete(xRaquete, yRaquete);
  movimentaMinhaRaquete ();
  verificaçãoColisãoRaquete(xRaquete, yRaquete);
  mostraRaqueteOponenete(xRaqueteOponente, yRaqueteOponente);
  movimetaRaqueteOponente();  verificçãoColisãoRaquete(xRaqueteOponente,yRaqueteOponente);
}
  
  
  function mostraBolinha(){
   circle(xBolinha, yBolinha, diametro);
   }
  
  function movimentaBolinha(){
    xBolinha += velocidadeXBolinha;
    yBolinha += velocidadeYBolinha;
  }
  
  function verificaColisaoBordas(){ 
    if (xBolinha + radio> width ||
     xBolinha - radio <0){
    velocidadeXBolinha *= -1;
  }
  
   if (yBolinha + radio> height ||
     yBolinha - radio <0){
    velocidadeYBolinha *= -1;
  }
  }
  
  function mostraRaquete (){
    rect (xRaquete, yRaquete, raqueteComprimento, raqueteAltura)
}
 
  function mostraRaqueteOponenete (x,y){
    rect (x, y, raqueteComprimento, raqueteAltura)
}

  function movimentaMinhaRaquete(){
  if (keyIsDown(UP_ARROW)){yRaquete -= 10;}
  
  if(keyIsDown(DOWN_ARROW)){yRaquete += 10;}
  }

  function verificaçãoColisãoRaquete(){
    if(xBolinha - radio < xRaquete + raqueteComprimento
    && yBolinha - radio < yBolinha + raqueteAltura && 
      yBolinha + radio > yRaquete){
      velocidadeXBolinha *= -1; 
    }
  }

  function verificçãoColisãoRaquete(x, y){
     colidiu= collideRectCircle(x, y, raqueteComprimento, raqueteAltura, xBolinha, yBolinha, radio);
 
  if(colidiu){
    velocidadeXBolinha  *= -1;
  }
   }

  function movimetaRaqueteOponente(){
   velocidadeYOponente = xBolinha -  yRaqueteOponente - raqueteComprimento / 2 - 30;   
    yRaqueteOponente += velocidadeYOponente
  }
