# Instalando GTK no Ubuntu 22.04

Este guia irá ajudá-lo a instalar e configurar a biblioteca GTK para desenvolvimento de interfaces gráficas em C no Ubuntu 22.04.

## 🐧 Instalação do Ubuntu 22.04

Se você ainda não tem o Ubuntu instalado, recomendamos seguir este tutorial em vídeo:

[Como instalar o Ubuntu 22.04 LTS](https://www.youtube.com/watch?v=zKBNc5LWLbQ) - Este vídeo mostra passo a passo como baixar a ISO do Ubuntu, criar um pendrive bootável e instalar o sistema operacional em seu computador.

## 🛠️ Instalando o GTK no Ubuntu 22.04

### Passo 1️⃣: Atualize os repositórios

Abra o terminal e execute os seguintes comandos:

```bash
    sudo apt update
    sudo apt upgrade -y
```

### Passo 2️⃣: Instale os pacotes para o GTK

```bash
    sudo apt install -y build-essential libgtk-3-dev
```

Este comando instala:

- 📦 O compilador GCC e ferramentas de compilação
- 📦 Headers e bibliotecas de desenvolvimento GTK 3.0

### Passo 3️⃣: Instale ferramentas adicionais para desenvolvimento

```bash
    sudo apt install -y pkg-config glade cmake
```

- 🔧 pkg-config: Ajuda a gerenciar flags de compilação para bibliotecas
- 🎨 glade: Editor visual para interfaces GTK
- 🏗️ cmake: Sistema de compilação multiplataforma

### Passo 4️⃣: Verifique a instalação

Para verificar se a instalação foi bem-sucedida, crie um arquivo chamado hello.c com o seguinte conteúdo:

```c
    #include <gtk/gtk.h>

    static void activate(GtkApplication *app, gpointer user_data) {
        GtkWidget *window;
        
        window = gtk_application_window_new(app);
        gtk_window_set_title(GTK_WINDOW(window), "Olá GTK");
        gtk_window_set_default_size(GTK_WINDOW(window), 300, 200);
        gtk_widget_show_all(window);
    }

    int main(int argc, char **argv) {
        GtkApplication *app;
        int status;
        
        app = gtk_application_new("org.example.hello", G_APPLICATION_DEFAULT_FLAGS);
        g_signal_connect(app, "activate", G_CALLBACK(activate), NULL);
        status = g_application_run(G_APPLICATION(app), argc, argv);
        g_object_unref(app);
        
        return status;
    }
```

*💡 Recomendo fortemente que voce crie o arquivo dentro do vscode ou qualquer IDE/Editor de texto com acesso ao terminal integrado, ja que sera necessario compilar o arquivo via terminal*

### Passo 5️⃣: Compile e execute o programa:

```c
    gcc -o hello hello.c `pkg-config --cflags --libs gtk+-3.0`
```

Execute o binario com:

```c
    ./hello
```

✨ Se uma janela com o título "Olá GTK" aparecer, parabéns! Você instalou o GTK com sucesso. ✨
