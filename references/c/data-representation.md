# 🧠 Representação de Dados e Manipulação de Bits

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

## 🔢 Decimal (Base 10)

O sistema decimal é o que usamos no dia a dia. Ele possui 10 dígitos (0 a 9) e cada posição representa uma potência de 10.  
Exemplo:
- O número `375` no decimal significa:
  - `3×10² + 7×10¹ + 2×10⁰ = 300 + 70 + 2`

## 🧮 Hexadecimal (Base 16)

O sistema hexadecimal é um sistema de numeração de base 16 que utiliza os símbolos de 0 a 9 e as letras de A a F para representar valores de 0 a 15, sendo muito utilizado em computação e programação para representar dados binários de forma mais compacta, bem como na codificação de cores na web e em design gráfico.

```text
Decimal:        0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
Hexadecimal:    0 1 2 3 4 5 6 7 8 9  A  B  C  D  E  F
```

Cada 2 dígitos hexadecimais representam 1 byte (8 bits).  
- Exemplo:
  - `0x41` (hexadecimal) = `65` (decimal) = `'A'` (ASCII)
  - `0xE3` (hexadecimal) = `227` (decimal), parte do caractere `'ã'` no UTF-8.

## 📘 UTF-8 e os bits

Em C, o suporte a UTF-8 é gerenciado principalmente pelas funções de tempo de execução e pelo ambiente de compilação. Para habilitar o modo UTF-8, você deve configurar seu compilador (usando opções como `/utf-8` no MSVC) e usar a função `setlocale` com uma localidade no formato `".UTF8"` (como `setlocale(LC_ALL, ".UTF8")`) para que as funções de tempo de execução esperem e processem cadeias de caracteres UTF-8. A codificação UTF-8 usa sequências de 1 a 4 bytes para representar todos os caracteres Unicode, sendo compatível com ASCII para os 128 primeiros caracteres. 

| Tipo | Binário | Significado |
| --- | --- | --- |
| 1 byte | `0xxxxxxx` | ASCII (7 bits) |
| 2 bytes | `110xxxxx 10xxxxxx` | Letras com acento, símbolos latinos |
| 3 bytes | `1110xxxx 10xxxxxx 10xxxxxx` | Símbolos, caracteres orientais |
| 4 bytes | `11110xxx 10xxxxxx 10xxxxxx 10xxxxxx` | Emojis, símbolos raros |

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

### Converter um caractere (char) para uma string binária de 8 bits

```c
void char_to_bin(char c, char *bin) {
    for(int i = 0; i < 8; i++) {
        bin[i] = ((c >> (7 - i)) & 1) ? '1' : '0';
    }
    bin[8] = '\0';
}
```

### Converter uma string binário de 8 bits para um caractere

```c
unsigned char bin_to_char(unsigned char *bin) {
    unsigned char c = 0;
    for(int i = 0; i < 8; i++) {
        if(bin[i] == '0') continue;
        c |= (unsigned char)(1 << (7 - i));
    }
    return c;
}
```

### Imprimir a tabela binária completa de 8 bits (0 a 255)

```c
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

### Obtem o valor do bit na posição 'pos' (0-7)

```c
uint8_t get_bit(uint8_t byte, int pos) {
    return (byte >> pos) & 1;
}
```

### Defini o bit na posição 'pos' como 1

```c
uint8_t set_bit(uint8_t byte, int pos) {
    return byte | (1 << pos);
}
```

### Limpa o bit na posição 'pos' (define como 0)

```c
uint8_t clear_bit(uint8_t byte, int pos) {
    return byte & ~(1 << pos);
}
```

### Inverte o bit na posição 'pos'

```c
uint8_t toggle_bit(uint8_t byte, int pos) {
    return byte ^ (1 << pos);
}
```

### Conta o número real de símbolos na tela

*Ideal para caracteres UTF-8, ao contrario de strlen() que conta o número de bytes e não caracteres*

```c
size_t string_len(const unsigned char *str) {
    size_t count = 0;
    while(*str) {
        if((*str & 0xC0) != 0x80) count++;
        str++;
    }
    return count;
}
```

### Obtem o próximo caractere UTF-8

```c
const unsigned char *utf8_next_char(const unsigned char *p) {
    if(*p == 0) return p; // fim da string

    // Descobre quantos bytes tem o caractere
    int ext = 0;
    if((*p & 0x80) == 0x00) ext = 0;        // 0xxxxxxx -> 1 byte (ASCII)
    else if((*p & 0xE0) == 0xC0) ext = 1;   // 110xxxxx -> 2 bytes
    else if((*p & 0xF0) == 0xE0) ext = 2;   // 1110xxxx -> 3 bytes
    else if((*p & 0xF8) == 0xF0) ext = 3;   // 11110xxx -> 4 bytes

    return p + ext + 1;
}
```

### Itera e imprime cada caractere UTF-8

```c
void utf8_print_chars(const unsigned char *str) {
    const unsigned char *p = str;
    while(*p) {
        const unsigned char *nxt = utf8_next_char(p);
        printf("Caractere: ");
        while(p < nxt) {
            printf("%c", *p); // imprime todos os bytes do caractere
            p++;
        }
        printf("\n");
    }
}
```

### Converte uma string binária/textual para representação hexadecimal ASCII

```c
size_t str_to_hex(const char *str, char **hex, const char *sep) {
    const char *hexs = "0123456789ABCDEF";

    size_t str_len = strlen(str);
    size_t hex_cap = sep ? str_len * 3 : str_len * 2 + 1;
    size_t limit = hex_cap - 1;
    size_t pos = 0;

    char *ptr = *hex ? realloc(*hex, hex_cap) : malloc(hex_cap);
    if(!ptr) return pos;
    *hex = ptr;

    while(*str && pos < limit) {
        (*hex)[pos++] = hexs[(*str >> 4) & 0x0F];
        (*hex)[pos++] = hexs[*str & 0x0F];
        str++;
        if(sep && *str) (*hex)[pos++] = *sep;
    }
    (*hex)[pos] = '\0';
    return pos;
}
```

### Converte uma string de dígintos hexadecimais de volta para binário/textual

```c
size_t hex_to_str(const char *hex, char **str, const char *sep) {
    size_t hex_len = strlen(hex);
    size_t str_cap = sep ? (hex_len + 1) / 3 + 1 : hex_len / 2 + 1;
    size_t pos = 0;
    char *ptr = *str ? realloc(*str, str_cap) : malloc(str_cap);
    if(!ptr) return pos;
    *str = ptr;
    while(*hex && pos + 1 < str_cap) {
        if(sep && *hex == *sep) {
            hex++;
            continue;
        }
        unsigned char nibbles[2] = {0, 0};
        for(int i = 0; i < 2; i++) {
            if(*hex >= '0' && *hex <= '9') nibbles[i] = *hex - '0';
            else if(*hex >= 'A' && *hex <= 'F') nibbles[i] = *hex - 'A' + 10;
            else if(*hex >= 'a' && *hex <= 'f') nibbles[i] = *hex - 'a' + 10;
            else break;
            hex++;
        }
        (*str)[pos++] = (char)((nibbles[0] << 4) | nibbles[1]);
    }
    (*str)[pos] = '\0';
    return pos;
}
```