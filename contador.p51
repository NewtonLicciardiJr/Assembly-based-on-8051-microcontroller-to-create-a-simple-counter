; 
; Exemplo de programa em Assembly do 8051
; 
; Este programa propoe efetuar a CONTAGEM de valores decimais e apresenta no Display 
; 3 subrotinas (fun??es) foram criadas
;    a que efetua um delay de tempo
;    a que acende o display menos significativo
;    a que acendo o dsiplay mais significativo
;    
;    o ajuste BCD do acumulador e utilizado entao ==> instru??o DA A - o que ela faz?
;       repare que para o incremento no acumulador e utilizado o comando ADD e nao INC
;             qual a raz?o? O comando ADD leva inclusive mais tempo para ser processado ....
;
;    a pilha e usada para salvar enderecos de retorno de subrotina
;    
;    repare que o programa esta pouco otimizado - ha muita repeticao de codigo!!
;       e proposital!!
;       voce seria capaz de otimizar o mesmo? Pense a respeito!!
;
;   produzido por Prof. Newton Licciardi
;
;   fev/2018
;
;   contato: newton.licciardijr@gmail.com
;


        org      000h            ;inicio do codigo assembly em 000h
        mov      a,     #0h      ;inicia o acumulador do kit com 0h
inicio:    
        add      a,     #01h     ;incrementa o acumulador
        da       a               ;faz o ajuste BCD do valor no acumulador

        acall    dmenor          ; chama subrotina para acender digito menos significativo
        acall    delay           ; propoe um delay para persistencia da visao
        acall    dispmaior       ; idem para display mais significativo 
        acall    delay           ; 

        acall    dmenor          ; chama subrotina para acender digito menos significativo
        acall    delay           ; propoe um delay para persistencia da visao
        acall    dispmaior       ; idem para display mais significativo 
        acall    delay           ; 

        acall    dmenor          ; chama subrotina para acender digito menos significativo
        acall    delay           ; propoe um delay para persistencia da visao
        acall    dispmaior       ; idem para display mais significativo 
        acall    delay           ; 

        acall    dmenor          ; chama subrotina para acender digito menos significativo
        acall    delay           ; propoe um delay para persistencia da visao
        acall    dispmaior       ; idem para display mais significativo 
        acall    delay           ; 

        acall    dmenor          ; chama subrotina para acender digito menos significativo
        acall    delay           ; propoe um delay para persistencia da visao
        acall    dispmaior       ; idem para display mais significativo 
        acall    delay           ; 

        acall    dmenor          ; chama subrotina para acender digito menos significativo
        acall    delay           ; propoe um delay para persistencia da visao
        acall    dispmaior       ; idem para display mais significativo 
        acall    delay           ; 

        acall    dmenor          ; chama subrotina para acender digito menos significativo
        acall    delay           ; propoe um delay para persistencia da visao
        acall    dispmaior       ; idem para display mais significativo 
        acall    delay           ; 


         
        jmp     inicio          ; retorna ao inicio

delay:                          ; rotina de loop temporal

; subrotina - delay - que gera uma temporiza??o 
; ajustando e decrementando o conteudo de r2, r1 e r0 
; a 12 Mhz de cristal ==> 1 Mhz cilo de maquina
;   laco interno = 3 ciclos ==> 3 us
;   ex. r1=r2=31 ==> 3us x 900 ~ 0,2 ms
;   r0 ajusta o timing deseja ==> ex. r0=1 ==> 1 x 0,2 = 0,2 ms

        mov     r0,     #01h
loop0:
        mov     r1,     #063d
loop1:
        mov     r2,     #063d
loop2:
        nop                     ; esta instru??o leva 1 ciclo de maquina - 1us
        djnz    r2,     loop2   ; esta instru??o leva 2 ciclos de maquina - 2 us
                                ; esta instru??o decrementa r2, compara se ele ? zero. 
                                ;  se nao for retorna a loop2
                                ;  djnz ? ideal para controle de loops
        nop
        djnz    r1,     loop1
        nop
        djnz    r0,     loop0
        ret        


dmenor:

;        Esta rotina testa os 4 bits menos significativos do acumulador 
;          comparando com valores de 0 a 9 
;          e acende o display menos significativo com os segmentos correspondentes 

        mov      r3,    a      ; armazena conteudo original do acumulador em r3
        anl      a,     #015d  ; faz um and logico para obter os 4 bits menos significativos do acumulador
        cjne     a,#00d,cont1  ; desvia para cont1 se a for diferente de 0;
        mov      p0,    #064d  ; prepara acendimento dos segmentos correspondentes a 0 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont1:
        cjne     a,#01d,cont2  ; desvia para cont2 se a for diferente de 1;
        mov      p0,    #121d  ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont2:
        cjne     a,#02d,cont3  ; desvia para cont3 se a for diferente de 2;
        mov      p0,    #036d  ; prepara acendimento dos segmentos correspondentes a 2 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont3:
        cjne     a,#03d,cont4  ; desvia para cont4 se a for diferente de 3;
        mov      p0,    #048d  ; prepara acendimento dos segmentos correspondentes a 3 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont4:
        cjne     a,#04d,cont5  ; desvia para cont5 se a for diferente de 4;
        mov      p0,    #025d  ; prepara acendimento dos segmentos correspondentes a 4 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont5:
        cjne     a,#05d, cont6 ; desvia para cont6 se a for diferente de 5;
        mov      p0, #018d     ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont6:
        cjne     a,#06d, cont7 ; desvia para cont7 se a for diferente de 6;
        mov      p0, #02d      ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont7:
        cjne     a,#07d,cont8  ; desvia para cont8 se a for diferente de 7;
        mov      p0,#0120d     ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont8:
        cjne     a,#08d,cont9  ; desvia para cont9 se a for diferente de 8;
        mov      p0, #00d      ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
cont9:
        cjne     a,#09d,conte  ; desvia para conte se a for diferente de 9;
        mov      p0, #016d     ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.3          ; acende display menos significativo com valor de p0
        setb     p1.2          ; apaga display mais significativo
conte:
        mov      a,     r3     ; retorna conteudo original do acumulador armazenado em r3
        ret                    ; final da subrotina do display


dispmaior:

;        Esta rotina testa os 4 bits mais significativos do acumulador 
;          comparando com valores de 0 a 9 
;          e acende o display mais significativo com os segmentos correspondentes 

        mov      r3,    a      ; armazena conteudo original do acumulador em r3
        anl      a,  #0240d    ; faz um and logico para obter os 4 bits mais significativos do acumulador
        swap     a             ; troca o nibble mais significativo com o menos do acumulador
        cjne     a,#00d,cont11 ; desvia para cont1 se a for diferente de 0;
        mov      p0,    #064d  ; prepara acendimento dos segmentos correspondentes a 0 no display
        clr      p1.2          ; acende display mais significativo com valor de p0
        setb     p1.3          ; apaga display menos significativo
cont11:
        cjne     a,#01d,cont12 ; desvia para cont2 se a for diferente de 1;
        mov      p0,#0121d     ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.2          ; acende display mais significativo com valor de p0
        setb     p1.3          ; apaga display menos significativo
cont12:
        cjne     a,#02d,cont13 ; desvia para cont3 se a for diferente de 2;
        mov      p0,    #036d  ; prepara acendimento dos segmentos correspondentes a 2 no display
        clr      p1.2          ; acende display mais significativo com valor de p0
        setb     p1.3          ; apaga display menos significativo
cont13:
        cjne     a,#03d,cont14 ; desvia para cont4 se a for diferente de 3;
        mov      p0,    #048d  ; prepara acendimento dos segmentos correspondentes a 3 no display
        clr      p1.2          ; acende display mais significativo com valor de p0
        setb     p1.3          ; apaga display menos significativo
cont14:
        cjne     a,#04d,cont15 ; desvia para cont5 se a for diferente de 4;
        mov      p0,    #025d  ; prepara acendimento dos segmentos correspondentes a 4 no display
        clr      p1.2          ; acende display mais significativo com valor de p0
        setb     p1.3          ; apaga display menos significativo
cont15:
        cjne     a,#05d,cont16 ; desvia para cont6 se a for diferente de 5;
        mov      p0,    #018d  ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.2          ; acende display mais significativo com valor de p0
        setb     p1.3          ; apaga display menos significativo
cont16:
        cjne     a,#06d,cont17 ; desvia para cont7 se a for diferente de 6;
        mov      p0,    #02d   ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.2          ; acende display mais significativo com valor de p0
        setb     p1.3          ; apaga display menos significativo
cont17:
        cjne     a,#07d,cont18  ; desvia para cont8 se a for diferente de 7;
        mov      p0,    #0120d  ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.2           ; acende display mais significativo com valor de p0
        setb     p1.3           ; apaga display menos significativo
cont18:
        cjne     a,#08d,cont19  ; desvia para cont9 se a for diferente de 8;
        mov      p0,    #00d    ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.2           ; acende display mais significativo com valor de p0
        setb     p1.3           ; apaga display menos significativo
cont19:
        cjne     a,#09d,cont1e  ; desvia para conte se a for diferente de 9;
        mov      p0,    #016d   ; prepara acendimento dos segmentos correspondentes a 1 no display
        clr      p1.2           ; acende display mais significativo com valor de p0
        setb     p1.3           ; apaga display menos significativo
cont1e:
        mov      a,     r3      ; retorna conteudo original do acumulador armazenado em r3
        ret                     ; final da subrotina do display

        end                     ; termina programa em Assembly