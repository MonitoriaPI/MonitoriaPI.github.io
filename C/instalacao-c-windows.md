# Instalação do compilador GCC no Windows

Compiladores são programas especiais que fornecem um arquivo executável a partir do nosso código fonte. Para compilar projetos C no Windows, serão demonstrados 2 métodos:  
- Compilar nativamente através do [MinGW](#mingw)
- Compilar em um ambiente Linux através do [WSL](#wsl)

## MinGW

MinGW é uma série de ferramentas (Toolchain) para desenvolvimento e compilação de projetos C nativamente no Windows. Algumas IDEs possuem uma versão junto de sua instalação, e seus binários podem ser baixados manualmente [aqui]().  
Entretanto, é extremamente recomendado que sua instalação seja feita por meio de um gerenciador de pacotes. Aqui, escolhemos utilizar o MSYS2, gerenciador que ainda será utilizado novamente para o projeto de interface gráfica.

[Instalação do compilador C/C++ com MinGw64/msys2 no Windows | EQE-044](https://youtu.be/ShPPSwpClPc?si=FRaOlj9jwK5PfmTm) - Esse vídeo mostra o passo a passo para a instalação do MSYS2 e do MinGW. Alguns detalhes para se atentar:
- No minuto [14:50](https://youtu.be/ShPPSwpClPc?si=FRaOlj9jwK5PfmTm&t=890) cole `pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain` no lugar
- No minuto [20:30](https://youtu.be/ShPPSwpClPc?si=UzmYE-01f-KvXKWI&t=1230) coloque `C:\msys64\ucrt64\bin`, `C:\msys64\usr\bin` e `C:\msys64\mingw64\bin` nas variáveis de ambiente

## WSL

WSL (Windows Subsystem for Linux) é uma máquina virtual Linux que roda diretamente sobre seu sistema Windows, com suporte direto da Microsoft.  
Ele pode facilitar bastante o processo de instalação das bibliotecas adicionais em futuros projetos.

Essencialmente, a instalação do WSL consiste em abrir o terminal (**Win+R**, digite **cmd**), digitar  
```
wsl --install
```  
(note que talvez seja necessário rodar o comando 2 vezes) e então seguir as instruções do programa.

Uma vez tudo instalado, atualize os pacotes com `sudo apt update` e instale o compilador GCC através de 
```
sudo apt install gcc
```
(Comandos com o predicado `sudo` requerem usuário e senha para serem executados)

Informações adicionais  

- [Instalar o WSL \| Microsoft Learn](https://learn.microsoft.com/pt-br/windows/wsl/install)
- [Como instalar o WSL2 no Windows 10/11 - Linux e Windows Lado a Lado para Iniciantes](https://youtu.be/qlLcnSvG1rA?si=--V6bfTcMoPeYivS) (vídeo)

### Integração com VS Code

Para abrir o repositório remoto Linux no VS Code, é necessário instalar a extensão WSL da Microsoft (vá em extensões e pesquise WSL).  
Depois, abra a paleta de comandos (**Ctrl+Shift+P**), pesquise WSL e confirme **"Conectar ao WSL"** (na sua primeira vez, só confirmar a distro que instalasse).

Uma vez dentro do sistema, se tiver problema em criar arquivos, abra o terminal integrado e digite
```
sudo chown -R nome_do_usuario .
```
onde `nome_do_usuario` é o nome que colocasse de login pro seu WSL.

## Checando a instalação

Para checar a instalação, abra seu editor de preferência, crie o arquivo olaMundo.c e cole o seguinte conteúdo:
```
#include <stdio.h>

int main() {
    printf("Sarve B)\n");
}
```
Abra uma janela de terminal na mesma pasta desse arquivo e digite:
```
gcc -o olaMundo olaMundo.c
```
Logo após, será criado mais um arquivo chamado `olaMundo.exe`. Ao digitar esse mesmo nome no terminal, deverá aparecer uma mensagem em seguida. Se tudo der certo, terá compilado seu primeiro programa em C
