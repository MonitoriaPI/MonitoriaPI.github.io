# Instalação do MinGW (compilador GCC + gerenciador de pacotes MSYS2) no windows

Para transformar seu código-fonte .c em um arquivo executável .exe, faz-se uso de um compilador. No Windows, isso é possível através do MinGW, um pacote de utilidades que contém, dentre outras coisas, o compilador GCC e a biblioteca padrão da linguagem C

IDEs como Codeblocks ou CLion já acompanham uma instalação MinGW. Entretanto, caso deseje utilizar um editor de texto como VS Code, será necessária sua instalação manual

[Instalação do compilador C/C++ com MinGw64/msys2 no Windows | EQE-044](https://youtu.be/ShPPSwpClPc?si=FRaOlj9jwK5PfmTm) - Esse vídeo mostra como instalar o MinGW através do gerenciador de pacotes MSYS2, uma ferramenta que ainda será útil no futuro. Entretanto, alguns detalhes para se atentar:
- No minuto [14:50](https://youtu.be/ShPPSwpClPc?si=FRaOlj9jwK5PfmTm&t=890) cole `pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain` no lugar
- No minuto [20:30](https://youtu.be/ShPPSwpClPc?si=UzmYE-01f-KvXKWI&t=1230) coloque `C:\msys64\ucrt\bin` em vez de `C:\msys64\mingw64\bin` nas variáveis de ambiente

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

## Notas: VS Code
Caso decida escolher o VS Code como seu editor, certifique-se de instalar a extensão de suporte para C/C++. Deverá aparecer um pop-up sobre no canto inferior direito ao criar seu primeiro arquivo .c

Além de outras ferramentas, ele providenciará um botão no canto superior direito toda vez que abrir um arquivo em C, que compilará e executará o código automaticamente ao clique
