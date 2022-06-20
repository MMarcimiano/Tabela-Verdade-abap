# Tabela-Verdade-abap
algoritmo resolução tabela verdade em abap 

"Trabalho Extra inplementação da contrução de um algorítmo que retorne TABELA VERDADE
"Mateus Henrique Marcimiano B.


"campo da tela
Parameter: var_expressao type string.

"declaração de variáveis
DATA: 
w_n TYPE i,
w_count type i,
w_str type c,
w_letras type i,
w_formula type i,
w_e type string value '^',
w_ou type string value 'v',
w_not type string value '~',
w_implicacao type string value '->'.

"tamanho da expressão
n = strlen( var_expressao ).

do n times.    "loop ou while
w_count = w_count + 1.
w_str = var_expressao+count(1). "andando em posição
if w_str = sy-abcde. "verifica letras
	w_letras = w_letras + 1.
else.
	if ( w_str != w_e AND w_str != w_ou AND w_str != w_not AND w_implicacao ) "!= diferente
		mensagem de erro ("expressão não aceita") 
		leave. "sai
	endif.
endif.

endo.          "fecha loop

w_formula = 2 ** w_letras. "potencia

if ( w_letras = 0 or w_letras = 1 ).
	write 'V'.
	write 'F'.
	leave. "sai
endif.

do n times.
w_count = w_count + 1.
case w_letras.
WHEN 2.
	if ( var_expressao+1(1) = sy-abcde AND 
             var_expressao+2(1) = w_e AND 
             var_expressao+3(1) = sy-abcde ).
		write 'V' | 'V' | 'V',
		      'V' | 'F' | 'F',
                      'F' | 'V' | 'F',
	              'F' | 'F' | 'F'.
		leave. "sai do programa.
	endif.
	if ( var_expressao+1(1) = sy-abcde AND 
             var_expressao+2(1) = w_ou AND 
             var_expressao+3(1) = sy-abcde ).
		write 'V' | 'V' | 'V',
		      'V' | 'F' | 'V',
                      'F' | 'V' | 'V',
	              'F' | 'F' | 'F'.
		leave. "sai do programa.
	endif.
	if ( var_expressao+1(1) = w_not AND 
             var_expressao+2(1) = sy-abcde AND 
             var_expressao+3(1) = w_e AND 
             var_expressao+4(1) = sy-abcde ).
		write 'F' | 'V' | 'F',
		      'F' | 'F' | 'F',
                      'V' | 'V' | 'V',
	              'V' | 'F' | 'F'.
		leave . "sai do programa.
	endif.
	if ( var_expressao+1(1) = abcde AND 
             var_expressao+2(1) = w_e AND 
             var_expressao+3(1) = w_not AND 
             var_expressao+4(1) = sy-abcde ).
		write 'V' | 'F' | 'F',
		      'V' | 'V' | 'V',
                      'F' | 'F' | 'F',
	              'F' | 'V' | 'F'.
		leave. "sai do programa.
	endif.
	if ( var_expressao+1(1) = w_not AND 
             var_expressao+2(1) = sy-abcde AND 
             var_expressao+3(1) = w_e AND 
             var_expressao+4(1) = w_not AND 
             var_expressao+5(1) = sy-abcde ).
		write 'F' | 'F' | 'F',
		      'F' | 'V' | 'F',
                      'V' | 'F' | 'F',
	              'V' | 'V' | 'V'.
		leave. "sai do programa.
	endif.
"ou
	if ( var_expressao+1(1) = w_not AND 
             var_expressao+2(1) = sy-abcde AND 
             var_expressao+3(1) = w_ou AND 
             var_expressao+4(1) = sy-abcde ).
		write 'F' | 'V' | 'V',
		      'F' | 'F' | 'F',
                      'V' | 'V' | 'V',
	              'V' | 'F' | 'V'.
		leave. "sai do programa.
	endif.
	if ( var_expressao+1(1) = abcde AND 
             var_expressao+2(1) = w_ou AND 
             var_expressao+3(1) = w_not AND 
             var_expressao+4(1) = sy-abcde ).
		write 'V' | 'F' | 'V',
		      'V' | 'V' | 'V',
                      'F' | 'F' | 'F',
	              'F' | 'V' | 'V'.
		leave. "sai do programa.
	endif.
	if ( var_expressao+1(1) = w_not AND 
             var_expressao+2(1) = sy-abcde AND 
             var_expressao+3(1) = w_ou AND 
             var_expressao+4(1) = w_not AND 
             var_expressao+5(1) = sy-abcde ).
		write 'F' | 'F' | 'F',
		      'F' | 'V' | 'V',
                      'V' | 'F' | 'V',
	              'V' | 'V' | 'V'.
		leave. "sai do programa.
	endif.

	if ( var_expressao+1(1) = sy-abcde AND 
             var_expressao+2(1) = w_implicacao AND 
             var_expressao+3(1) = sy-abcde ).
		write 'V' | 'V' | 'V',
		      'V' | 'F' | 'F',
                      'F' | 'V' | 'F',
	              'F' | 'F' | 'V'.
		leave. "sai do programa.
	endif.

	if ( var_expressao+1(1) = w_not AND 
             var_expressao+2(1) = sy-abcde AND 
             var_expressao+3(1) = w_implicacao AND 
             var_expressao+4(1) = sy-abcde ).
		write 'F' | 'V' | 'F',
		      'F' | 'F' | 'V',
                      'V' | 'V' | 'V',
	              'V' | 'F' | 'F'.
		leave . "sai do programa.
	endif.

	if ( var_expressao+1(1) = abcde AND 
             var_expressao+2(1) = w_implicacao AND 
             var_expressao+3(1) = w_not AND 
             var_expressao+4(1) = sy-abcde ).
		write 'V' | 'F' | 'F',
		      'V' | 'V' | 'V',
                      'F' | 'F' | 'V',
	              'F' | 'V' | 'F'.
		leave. "sai do programa.
	endif.

	if ( var_expressao+1(1) = w_not AND 
             var_expressao+2(1) = sy-abcde AND 
             var_expressao+3(1) = w_implicacao AND 
             var_expressao+4(1) = w_not AND 
             var_expressao+5(1) = sy-abcde ).
		write 'F' | 'F' | 'V',
		      'F' | 'V' | 'F',
                      'V' | 'F' | 'F',
	              'V' | 'V' | 'V'.
		leave. "sai do programa.
	endif.

WHEN 3.
WHEN 4.
endcase.
endo.
