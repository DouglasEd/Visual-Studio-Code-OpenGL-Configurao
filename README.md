# Configuração C++ & OpenGL no VSCode
Obrigado por visitar a página do meu projeto de configuração C++ & OpenGL no Visual Studio Code. Como o título sugere, esta é uma configuração básica para programação em OpenGL.

**Aviso:** este arquivo readme assume que você tem alguma experiência com Visual Studio Code, g++ e programação em OpenGL.

## Índice
1. [Introdução](#Introducao)
2. [Pré-requisitos](#pre-requisitos)
    1. [Extensões do Visual Studio Code](#extensoes-do-visual-studio-code)
    2. [g++](#g++)
3. [Estrutura do Diretório](#estrutura-do-diretorio)
    1. [.vscode](#.vscode)
    2. [builds](#builds)
    3. [dependencies](#dependencies)
    4. [src](#src)
4. [Compilando](#compilando)
5. [Executando](#executando)
    1. [Executável](#executavel)
    2. Modo [Depuração](#depuracao)
6. [Versões das Bibliotecas](#versoes-das-bibliotecas)
7. [Links Úteis](#links-uteis)

# Introdução
Como você já deve saber, este projeto é uma configuração, você precisa ter o **Visual Studio Code** instalado antes de poder executar o projeto conforme pretendido.

**NOTA:** O Visual Studio Code não é obrigatório, pois você pode usar o g++ para executar o projeto. O Visual Studio Code oferece um ambiente onde você pode escrever, executar e compilar seu código.

# Pré-requisitos

## Extensões do Visual Studio Code
As seguintes extensões são necessárias:

1. C/C++ (Microsoft)

## g++
Este projeto é compilado usando o comando g++. Em computadores Windows, isso significa que você precisa ter o **MinGW Installation Manager** instalado, de onde você pode instalar os seguintes pacotes:

1. mingw32-gcc-g++

Todos esses pacotes podem ser acessados na aba Basic Setup do instalador.

Quando esses pacotes estiverem instalados, você precisa adicionar o diretório onde o comando g++ está localizado na sua variável PATH.

Depois de tudo isso concluído, você deve ser capaz de executar o projeto.

# Estrutura do Diretório
O diretório do projeto está organizado da seguinte maneira:

* .vscode
* builds
* dependencies
* src
    * shaders

### **.vscode**
Este diretório contém a configuração e as opções do projeto no Visual Studio Code. Aqui você pode **adicionar seus próprios arquivos ao processo de compilação (tasks.json)** e **editar seu caminho de inclusão (c_cpp_properties.json)**.

### **builds**
Este diretório contém compilações específicas de plataforma. As **compilações suportadas atualmente** são **Windows e Linux**.

### **dependencies**
Esta pasta contém todas as bibliotecas que seu projeto pode usar, carregando e configurando as seguintes bibliotecas:

1. GLFW
2. GLAD
3. GLM

A estrutura principal deste diretório é uma pasta com o nome da dependência em MAIÚSCULAS com o conteúdo da biblioteca dentro dessa pasta.

**Quaisquer outras dependências que você queira adicionar precisam ser adicionadas ao processo de compilação** (.vscode/tasks.json).

### **src**
Esta pasta contém todos os seus arquivos de código-fonte (por exemplo, arquivos .cpp e .h). Também abriga seus shaders GLSL (src/shaders).

A pasta src também fornece 3 arquivos .cpp e 2 arquivos .h, que são:

1. main.cpp
2. engine.cpp + engine.h
3. shader.cpp + shader.h

**engine.cpp + engine.h**<br/>
Esses arquivos são seus principais arquivos onde você pode escrever seu código. Eles fornecem algumas funções nas quais você pode fazer a lógica de inicialização, entrada, atualização e renderização.

**shader.cpp + shader.h**<br/>
Este arquivo é uma classe básica de shader onde você pode carregar seus shaders.<br/>
**Código Exemplo:**
```cpp
Shader basicShaderProgram;

// Defina o vertex e fragment shader, depois compile em um programa
basicShaderProgram.setVertexShader("src/shaders/basicVertexShader.glsl");
basicShaderProgram.setFragmentShader("src/shaders/basicFragmentShader.glsl");
basicShaderProgram.compile();

// Vincule o shader
basicShaderProgram.use();
```
**Nota:** Este projeto não inclui arquivos de shader .glsl no executável. Isso é responsabilidade do desenvolvedor, e este projeto não fornece as ferramentas ou funcionalidades para fazer isso.

# Compilando
Para compilar seu projeto, **use o atalho de compilação padrão do Visual Studio Code** (CTRL + SHIFT + BUILD). Se o seu atalho de compilação for diferente, verifique no Visual Studio Code qual é a combinação correta.

# Executando

**Executável**<br/>
Para executar seu projeto, você precisa primeiro **compilar seu projeto** e, em seguida, executar o arquivo .exe localizado na pasta **builds/[PLATFORM]**.

**Nota:** Este projeto não inclui arquivos de shader .glsl no executável. Isso é responsabilidade do desenvolvedor, e este projeto não fornece as ferramentas ou funcionalidades para fazer isso. Para executar o executável com sucesso, você precisa criar as seguintes pastas dentro da pasta **builds/[PLATFORM]**: src/shaders/[SEU_CONTEUDO_DA_PASTA_SRC/SHADERS]. Depois, basta colar o conteúdo da sua pasta de shaders, que está localizada na pasta src, na estrutura de pastas recém-criada.

**Modo de Depuração**<br/>
Para executar o projeto em modo de depuração, **use o atalho de depuração padrão do Visual Studio Code** (CTRL + F5). Se o seu atalho de depuração for diferente, verifique no Visual Studio Code qual é a combinação correta.

# Versões das Bibliotecas
1. GLFW (Versão 3.3.bin.win32)
2. GLAD (gl: 4.6, profile: Core, extensions: none)
3. GLM (Versão 0.9.9.6)

Toda essa configuração funciona na versão mais recente do Visual Studio Code em 29-12-2019, que é a versão 1.14.1 (configuração do usuário).

# Links Úteis
* [MinGW Installation Manager](https://osdn.net/projects/mingw/releases/)
* [Compilação g++](https://www.cs.bu.edu/fac/gkollios/cs113/Usingg++.html)
* [Biblioteca GLFW](https://osdn.net/projects/mingw/releases/)
* [Biblioteca GLAD](https://glad.dav1d.de/)
* [Biblioteca GLM](https://glm.g-truc.net/0.9.9/index.html)
