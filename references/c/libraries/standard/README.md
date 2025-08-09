# 📚 Bibliotecas Padrão

**A biblioteca padrão do C** é um conjunto de cabeçalhos (*headers*) definidos pela especificação da linguagem (ISO/IEC), que fornecem funções, macros, tipos e constantes prontas para uso.  
Essas bibliotecas abrangem recursos essenciais como **entrada/saída de dados, manipulação de strings, cálculos matemáticos, gerenciamento de memória, controle de tempo, suporte a threads**, entre outros.

O uso dessas bibliotecas evita que o programador tenha que reinventar funcionalidades comuns e garante **portabilidade** entre diferentes sistemas e compiladores.

| Biblioteca | Breve Descrição |
| --- | --- |
| [`<stdio.h>`](/references/c/libraries/standard/stdio_h.md) | Entrada e saída padrão (ex: `printf`, `scanf`, manipulação de arquivos). |
| `<stdlib.h>` | Funções utilitárias (alocação dinâmica, conversões, geração de números pseudoaleatórios). |
| `<string.h>` | Manipulação de strings e blocos de memória (`strlen`, `strcpy`, `memcpy`, etc.). |
| `<ctype.h>` | Funções para classificação e transformação de caracteres (`isalpha`, `toupper`, etc.). |
| `<math.h>` | Funções matemáticas (ex: `sin`, `cos`, `sqrt`, `pow`). |
| `<time.h>` | Manipulação de datas e horas, temporizadores e funções relacionadas. |
| `<assert.h>` | Macro para verificação de condições em tempo de execução (`assert`). |
| `<errno.h>` | Definição e manipulação de códigos de erro em funções da biblioteca. |
| `<limits.h>` | Definição dos limites dos tipos inteiros e caracteres (`INT_MAX`, `CHAR_BIT`, etc.). |
| `<stdint.h>` | Tipos inteiros com tamanhos fixos e suas definições (`int32_t`, `uint64_t`). |
| `<stddef.h>` | Definições comuns como `size_t`, `ptrdiff_t` e `NULL`. |
| `<stdbool.h>` | Define o tipo booleano `bool` e valores `true` e `false`. |
| `<signal.h>` | Manipulação de sinais do sistema (`SIGINT`, `signal`, `raise`). |
| `<setjmp.h>` | Manipulação de saltos não locais (`setjmp` e `longjmp`). |
| `<locale.h>` | Configuração de localidade para tradução e formatação regional (idiomas, moeda, etc.). |
| `<wchar.h>` | Suporte a caracteres largos (`wchar_t`) e strings largas. |
| `<wctype.h>` | Funções para classificação e manipulação de caracteres largos. |
| `<inttypes.h>` | Formatos de entrada/saída para inteiros fixos e macros auxiliares. |
| `<stdarg.h>` | Manipulação de funções com número variável de argumentos (`va_list`, `va_start`, etc.). |
| `<complex.h>` | Suporte a números complexos (C99 em diante). |
| `<fenv.h>` | Controle do ambiente de ponto flutuante (C99). |
| `<float.h>` | Constantes com limites e propriedades dos tipos de ponto flutuante. |
| `<tgmath.h>` | Macros genéricas para funções matemáticas (C99). |
| `<threads.h>` | API para criação e controle de threads (C11). |
| `<stdalign.h>` | Definições para alinhamento de tipos e variáveis (C11). |
| `<stdatomic.h>` | Suporte a operações atômicas para programação concorrente (C11). |
| `<stdnoreturn.h>` | Define o especificador `_Noreturn` para funções que não retornam (C11). |
| `<uchar.h>` | Tipos para caracteres Unicode de 16 e 32 bits (`char16_t`, `char32_t`). |
| `<iso646.h>` | Macros para operadores alternativos como `and`, `or`, `not` (útil em alguns compiladores). |