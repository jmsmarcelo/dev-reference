# 📂 Entrada e Saída Padrão

A biblioteca `<stdio.h>` oferece funções para realizar operações básicas de entrada e saída, como leitura e escrita em arquivos, entrada do teclado e saída no terminal, além de controle de fluxo dos dados.

| Função | Descrição |
| --- | --- |
| `printf` | Imprime saída formatada no terminal (stdout). |
| `fprintf` | Imprime saída formatada em um arquivo ou fluxo especificado. |
| `sprintf` | Formata uma string em buffer (não imprime). |
| `snprintf` | Igual ao `sprintf` mas com limite de tamanho para o buffer. |
| `scanf` | Lê entrada formatada do terminal (stdin). |
| `fscanf` | Lê entrada formatada de um arquivo ou fluxo. |
| `sscanf` | Lê dados formatados de uma string. |
| `getchar` | Lê um caractere do stdin. |
| `putchar` | Escreve um caractere no stdout. |
| `gets` | Lê uma linha da entrada padrão (não seguro, obsoleto). |
| `fgets` | Lê uma linha de um arquivo/fluxo com tamanho limitado. |
| `puts` | Escreve uma string no stdout seguida de uma nova linha. |
| `fputs` | Escreve uma string em um arquivo/fluxo (sem adicionar nova linha). |
| `fopen` | Abre um arquivo e retorna um ponteiro para ele. |
| `fclose` | Fecha um arquivo aberto. |
| `feof` | Testa se o fim do arquivo foi alcançado. |
| `ferror` | Verifica se ocorreu erro em uma operação com arquivo. |
| `fflush` | Limpa (flush) o buffer de saída de um arquivo/fluxo. |
| `fread` | Lê dados binários de um arquivo para um buffer. |
| `fwrite` | Escreve dados binários de um buffer para um arquivo. |
| `fseek` | Move o ponteiro de leitura/escrita para uma posição no arquivo. |
| `ftell` | Retorna a posição atual do ponteiro de arquivo. |
| `rewind` | Move o ponteiro do arquivo para o início. |
| `perror` | Imprime uma mensagem de erro associada ao último erro. |
| `setbuf` | Define um buffer para um arquivo/fluxo (controle de buffering). |
| `setvbuf` | Define modo e tamanho do buffer para um arquivo/fluxo. |

## 🛠️ Especificadores de Formato (`printf`, `scanf`, stc)

| Especificar | Descrição | Exemplo |
| --- | --- | --- |
| `%d` / `%i` | Inteiro decimal com sinal | `123`, `-456` |
| `%u` | Inteiro decimal sem sinal (`unsigned`) | `123`, `456` |
| `%o` | Inteiro em octal | `0123` |
| `%x` | Inteiro em hexadecimal (minúsculo) | `0x1a3f` |
| `%X` | Inteiro em hexadecimal (maiúsculo) | `0x1A3F` |
| `%f` | Número de ponto flutuante (`float`/`double`) | `3.14159` |
| `%e` / `%E` | Notação científica (exponencial) | `1.23e+02`, `1.23E+02` |
| `%g` / `%G` | Notação automática (escolhe entre `%f` e `%e`) | `3.14`, `1.2e+3` |
| `%c` | Caractere único | `'A'` |
| `%s` | String (sequência de caracteres) | `"Hello"` |
| `%p` | Ponteiro (endereço de memória) | `0x7ffee3c2a9f0` |
| `%n` | Número de caracteres escritos até aqui (usa um ponteiro como argumento) | - |
| `%%` | Caracter % literal | `%` |

### ⚙️ Modificadores de Tamanho (antes do especificador)

Os modificadores indicam ao compilador qual o tipo exato do argumento passado para funções como `printf` e `scanf`. Eles são usados antes do especificador principal (`d`, `u`, `x`, etc).

| Modificador | Descrição | Exemplo | Tipo esperado |
| --- | --- | --- | --- |
| (nenhum) | Tipo padrão | `%d`, `%u` | `int`, `unsigned int` |
| `hh` | Tipo muito curto | `%hhd`, `%hhu` | `signed char`, `unsigned char` |
| `h` | Tipo curto | `%hd`, `%hu` | `short int`, `unsigned short int` |
| `l` | Tipo longo | `%ld`, `%lu` | `long int`, `unsigned long int` |
| `ll` | Tipo longo longo | `%lld`, `%llu` | `long long int`, `unsigned long long int` |
| `j` | Tipo inteiro máximo | `%jd`, `%ju` | `intmax_t`, `uintmax_t` |
| `z` | Tipo para tamanhos | `%zu`, `%zd` | `size_t` (unsigned), `ssize_t` (signed) |
| `t` | Tipo para diferença entre ponteiros | `%td`, `%tu` | `ptrdiff_t` (signed), `unsigned ptrdiff_t` |
| `L` | Tipo ponto flutuante de precisão estendida | `%Lf` | `long double` |