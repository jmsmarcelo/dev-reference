# 🪟 Bibliotecas do Windows (WinAPI)

O Windows fornece um conjunto de bibliotecas fundamentais (DLLs) que expôem a **WinAPI**, a interface nativa para interação com o sistema operacional.  
Essas bibliotecas oferecem acesso a recursos essenciais como gerenciamento de processos, threads, memória, janelas gráficas, rede e drivers.  
A maior parte do desenvolvimento em C, C++ e até assembly no Windows depende direta ou indiretamente dessas bibliotecas.

A tabela abaixo lista as principais DLLs da WinAPI.

| Biblioteca / Header | DLL associada | Descrição |
| --- | --- | --- |
| `<windows.h>` | (agrega várias) | Cabeçalho principal, inclui a maior parte da API do Windows |
| `<kernel32.h>` | `Kernel32.dll` | Funções essenciais do núcleo do Windows: memória, threads, processos, sincronização, sistema de arquivos |
| `<user32.h>` | `User32.dll` | Gerenciamento da interface gráfica: janelas, caixas de diálogo, eventos de teclado/mouse |
| `<gdi32.h>` | `Gdi32.dll` | Gráficos 2D: desenho de linhas, textos, imagens em janelas ou impressoras |
| `<advapi32.h>` | `Advapi32.dll` | Acesso avançado: Registro do Windows, serviços, segurança, permissões |
| `<shellapi.h>` | `Shell32.dll` | Funções do Shell do Windows: abrir arquivos, manipular atalhos, interagir com Explorer |
| `<comdlg32.h>` | `Comdlg32.dll` | Janelas de diálogo comuns (Abrir arquivo, Salvar como, Seleção de cor, Impressora) |
| `<ole32.h>` | `Ole32.dll` | Suporte a COM (Component Object Model), automação e objetos distribuídos |
| `<oleaut32.h>` | `OleAut32.dll` | Automação OLE: manipulação de tipos variantes e arrays seguros (SAFEARRAY) |
| `<ws2tcpip.h>` / `<Winsock2.h>` | `Ws2_32.dll` | Winsock 2: API de rede (TCP/IP, UDP, sockets) |
| `<wininet.h>` | `Wininet.dll` | API de Internet: HTTP, FTP (mais antiga, hoje substituída por WinHTTP/URLMon) |
| `<winhttp.h>` | `Winhttp.dll` | API moderna para comunicação HTTP |
| `<d3d9.h>` / `<d3d11.h>` | `D3D9.dll` / `D3D11.dll` | Direct3D (gráficos 3D da Microsoft) |
| `<dsound.h>` | `Dsound.dll` | DirectSound: áudio de baixa latência |
| `<dinput.h>` | `Dinput.dll` | DirectInput: dispositivos como teclado, joystick, gamepad |
| `<setupapi.h>` | `Setupapi.dll` | Instalação e configuração de drivers e dispositivos |
| `<winmm.h>` | `Winmm.dll` | Multimídia: áudio, timers, joystick (API antiga mas útil) |
| `<crypt32.h>` | `Crypt32.dll` | Funções de criptografia, certificados e segurança |