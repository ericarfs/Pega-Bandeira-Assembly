# Pega-Bandeira-Assembly
### Projeto de um jogo implementado em Assembly e construção do Hardware do Processador ICMC no "Simple Simulator".

* __Estudante__: Érica Ribeiro F. dos Santos 
* __nUsp__: 11836351
* __Turma__: BCC 020
* __Disciplina__:  SSC0119 - Prática em Organização de Computadores
* __Docente__: Eduardo do Valle Simões

## O Jogo - Pega Bandeira
#### O objetivo do jogo é pegar as quatro bandeiras que estão na base adversária e colocá-las na base aliada, tomando cuidado para não colidir com os inimigos, que se movimentam de maneira padronizada no mapa e cuja velocidade se altera com o decorrer do tempo. 
![Alt text](https://github.com/ericarfs/Pega-Bandeira-Assembly/blob/main/imagem_jogo1.PNG?raw=true  "Tela inicial do jogo")
![Alt text](https://github.com/ericarfs/Pega-Bandeira-Assembly/blob/main/imagem_jogo2.PNG?raw=true  "Mapa do jogo")
![Alt text](https://github.com/ericarfs/Pega-Bandeira-Assembly/blob/main/imagem_jogo3.PNG?raw=true  "Tela de derrota")
![Alt text](https://github.com/ericarfs/Pega-Bandeira-Assembly/blob/main/imagem_jogo5.PNG?raw=true  "Bandeiras na base")
![Alt text](https://github.com/ericarfs/Pega-Bandeira-Assembly/blob/main/imagem_jogo4.PNG?raw=true  "Tela de vitória")

[Link para o video com a explicação do código e o jogo funcionando](https://youtu.be/)


## Modificação do processador para com a função SQRT implementada


#### A função implementada calcula a raiz quadrada de um número, retornando seu valor inteiro.

Modificações no montador: arquivos defs.h e montador.c:

### defs.h

```c
// Para incluir uma nova INSTRUCAO, e' necessario mexer em 3 lugares diferentes:
// Definir o Codigo da Instrucao: 
  #define LOAD_CODE  1
// Definir os Bits da Instrucao: 
  #define LOAD       "110000"
// Definir a String de como a Instrucao deve aparecer no programa ASM:
  #define LOAD_STR   "LOAD"
```

[Link para o video com a explicação do código](https://youtu.be/)
