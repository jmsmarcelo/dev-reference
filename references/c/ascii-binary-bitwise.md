# ASCII, Binário e Operadores Bit a Bit

Este guia reúne explicações sobre codificação de caracteres, representação binária e manipulação de bits em C.

## 📌 ASCII 

Em C, o ASCII (American Standard Code for Information Interchange) é a codificação numérica utilizada para representar caracteres.  
Uma variável do tipo `char` armazena um código ASCII (um número inteiro de 0 a 127), e não o caractere em si.

Você pode exibir o valor ASCII de um caractere usando `%d` no printf ou converter um número em seu caractere correspondente usando `%c`.

## 🔢 Binário

Em C, "binário" pode se referir tanto à base numérica (base 2: 0 e 1), quanto a arquivos binários (dados em formato bruto, sem texto).

A leitura dos bits é feita da esquerda para a direita, da posição mais significativa para a menos significativa:
```bash
7 6 5 4 3 2 1 0 # Posição  
0 1 0 0 0 0 0 1 # Valor = 'a' (ASCII 97)
```

## Operadores Bit a Bit

| Operador | Nome | Ação | Exemplo (`a=01000001` (65=`A`), `b=01000010` (66=`B`)) |
| --- | --- | --- | --- |
| `&` | AND | 1 se ambos os bits forem 1 | `a & b` -> `01000000` (64=`@`) |
| `\|` | OR | 1 se pelo menos um bit for 1 | `a \| b` -> `01000011` (67=`C`) | 
| `^` | XOR | 1 se os bits forem diferentes | `a ^ b` -> `00000011` (3=`♥`) |
| `~` | NOT | inverter todos os bits | `~a` -> `10111110` (190=`╛`) |
| `<<` | Left Shift | Move os bits para a esquerda | `a << 1` -> `10000010` (130=`é`) |
| `>>` | Right Shift | Move os bits para a direita | `a >> 1` -> `00100000` (32=`space`) |

## Funções úteis

```c
// Converter um caractere (char) para uma string binária de 8 bits
void char_to_bin(char c, char *bin) {
    for(int i = 0; i < 8; i++) {
        bin[i] = ((c >> (7 - i)) & 1) ? '1' : '0';
    }
    bin[8] = '\0';
}

// Converter uma string binário de 8 bits para um caractere
unsigned char bin_to_char(unsigned char *bin) {
    unsigned char c = 0;
    for(int i = 0; i < 8; i++) {
        if(bin[i] == '0') continue;
        c |= (unsigned char)(1 << (7 - i));
    }
    return c;
}

// Imprimir a tabela binária completa de 8 bits (0 a 255)
void print_binary_table_8bits() {
    printf("DEC\tBIN\tCHAR\n");
    char bin[9];
    for(int i = 0; i < 256; i++) {
        unsigned char c = (unsigned char)i;
        char_to_bin(c, bin);
        printf("%3d\t%s\t%c\n", i, bin, c);
    }
}
```