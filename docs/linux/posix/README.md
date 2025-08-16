# 📌 Principais headers no Linux (POSIX)

A tabela abaixo reúne algumas das bibliotecas e cabeçalhos mais utilizados no desenvolvimento em **C para Linux**, oferecendo acesso direto às funcionalidades do sistema operacional. Esses arquivos permitem trabalhar com **processos, threads, rede, dispositivos, manipulação de sinais e interações de baixo nível com o kernel.**  
Assim como no Windows, a lista é apenas uma introdução: o ecossistema Linux é vasto, e cada subsistema do kernel pode trazer novos cabeçalhos especializados.

O objetivo aqui é destacar os pontos de entrada mais comuns para quem deseja programar **aplicações nativas em Linux** e ter maior controle sobre recursos do sistema.

| Header | Função principal |
| --- | --- |
| `<unistd.h>` | Chamadas do sistema POSIX (fork, exec, pipe, read, write, close, sleep, etc.) |
| `<fcntl.h>` | Controle de arquivos (abrir, bloquear, permissões, flags) |
| `<sys/types.h>` | Define tipos usados em chamadas do sistema (pid_t, off_t, size_t etc.) |
| `<sys/stat.h>` | Informações sobre arquivos (permissões, tamanho, tipo, `stat()`) |
| `<dirent.h>` | Manipulação de diretórios (`opendir`, `readdir`, `closedir`) |
| `<pthread.h>` | Threads POSIX (criação, mutex, semáforos, sincronização) |
| `<sys/socket.h>` | Comunicação via sockets (TCP, UDP, Unix Domain) |
| `<netinet/in.h>` | Estruturas e constantes para programação de rede (endereços IP, portas) |
| `<arpa/inet.h>` | Conversão de endereços IP (`inet_pton`, `inet_ntop`) |
| `<sys/select.h>` | Multiplexação de I/O com `select()` |
| `<poll.h>` | Alternativa moderna ao `select()` |
| `<sys/epoll.h>` | Sistema de I/O escalável do Linux (`epoll`) |
| `<signal.h>` | Tratamento de sinais (SIGINT, SIGKILL, etc.) |
| `<sys/wait.h>` | Controle de processos filho (wait, waitpid) |
| `<sys/mman.h>` | Memória compartilhada e mapeamento de arquivos (`mmap`, `munmap`) |
| `<semaphore.h>` | Semáforos POSIX |
| `<sys/shm.h>` | Memória compartilhada System V |
| `<sys/ipc.h>` | IPC (Inter-Process Communication) estilo System V |
| `<sys/msg.h>` | Filas de mensagens System V |
| `<sys/sem.h>` | Semáforos System V |
| `<dlfcn.h>` | Carregamento dinâmico de bibliotecas (`dlopen`, `dlsym`, `dlclose`) |
| `<time.h / sys/time.h>` | Tempo e temporizadores |
| `<sys/resource.h>` | Limites e prioridades de processos |