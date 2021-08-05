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

Modificações no montador - arquivos defs.h e montador.c:

* __defs.h__

```c
// Definir o Codigo da Instrucao: 
#define SQRT_CODE      98
// Definir os Bits da Instrucao: 
#define SQRT           "100110"
// Definir a String de como a Instrucao deve aparecer no programa ASM:
#define SQRT_STR       "SQRT"
```

* __montador.c__
```c
// 1) Definir os separadores da Instrucao e quantas linhas do EXE (mif) ela necessita:
        /* Instrucoes de 2 argumentos e 1 linha : instr (), () -> [...] */
        case NOT_CODE :	
     -> case SQRT_CODE:
	case MOV_CODE :
        case OUTCHAR_CODE :
        case CMP_CODE :
            parser_SkipUntil(','); 
            parser_SkipUntilEnd(); 
            end_cnt++; 
            break;

// 2) Explicar como o Montador vai montar os BITs da Instrucao e escrever no arquivo:
        case SQRT_CODE : // Sqrt R1, R2
            str_tmp1 = parser_GetItem_s();
            val1 = BuscaRegistrador(str_tmp1);
            free(str_tmp1);
            parser_Match(',');
            str_tmp2 = parser_GetItem_s();
            val2 = BuscaRegistrador(str_tmp2);
            free(str_tmp2);
            str_tmp1 = ConverteRegistrador(val1);
            str_tmp2 = ConverteRegistrador(val2);
            sprintf(str_msg,"%s%s%20000",SQRT,str_tmp1,str_tmp2);
            free(str_tmp1);
            free(str_tmp2);
            parser_Write_Inst(str_msg,end_cnt);
            end_cnt +=1;
            break;

// 3) Buscar o nome da instrucao na base de instrucoes e retornar 'op_code interno' da instrucao:
      if (strcmp(str_tmp,SQRT_STR) == 0)
        {
            return SQRT_CODE;
        }
    
```

Adicionar instrução no Simple Simulator:

* __simple_simulador.c__

```c
(mesmas instruções que as demais operações aritméticas)
//etapa de STATE_DECODE:
case SQRT:
    // reg[rx] = reg[ry] + reg[rz]; // Soma ou outra operacao
    selM3 = ry;
    selM4 = rz;
    OP = pega_pedaco(IR,15,10);
    carry = pega_pedaco(IR,0,0);
    selM2 = sULA;
    LoadReg[rx] = 1;
    selM6 = sULA;
    LoadFR  = 1;
    // -----------------------------
    state=STATE_FETCH;
    break;

//etapa de calcular resultado na ULA:
case SQRT:
    if(x>1)
        result = (int)sqrt(x);
    else
        result = x;
    break;	
```

Adicionar teste da instrução no arquivo de testes:

* __cpuram.asm__

```c
//Teste do Sqrt
loadn r1, #9
sqrt r3, r1
loadn r4, #'N'
add r3, r4, r3
loadn r0, #32
outchar r3, r0	 //Printa Q na linha 32
```

[Link para o video com a explicação do código](https://youtu.be/)
