# Instalando a Biblioteca QTRSensors Custom no PlatformIO

## Introdução

Este guia explica como instalar e configurar a biblioteca **QTRSensors Custom** em um projeto utilizando o **PlatformIO**. O PlatformIO é um ambiente de desenvolvimento popular para projetos embarcados, oferecendo suporte a diversas plataformas e microcontroladores.

## Passos para Instalação

### 1. Criando um Novo Projeto

1. Abra o **VS Code** com o **PlatformIO** instalado.
2. Clique no ícone do **PlatformIO Home** (canto inferior esquerdo).
3. Selecione **New Project**.
4. Escolha sua placa de desenvolvimento (exemplo: **ESP32, Arduino Uno** etc.).
5. Escolha o framework (**Arduino**).
6. Clique em **Finish**.

### 2. Adicionando a Biblioteca ao Projeto

#### Opção 1: Clonando o Repositório Manualmente

1. Acesse o repositório da biblioteca customizada:
   ```sh
   git clone https://github.com/Goytaborgs/QTR-Sensors-Goytaborgs.git
   ```
2. Copie a pasta da biblioteca para dentro do diretório `lib` do seu projeto PlatformIO.

Exemplo da estrutura do projeto após adicionar a biblioteca manualmente:

```
meu_projeto/
│-- lib/
│   ├── QTR-Sensors-Goytaborgs/   # Biblioteca clonada
│   │   ├── src/
│   │   ├── include/
│   │   ├── library.json
│   │   ├── README.md
│-- src/
│   ├── main.cpp                  # Código principal do projeto
│-- platformio.ini                 # Configurações do PlatformIO
```

#### Opção 2: Editando o `platformio.ini`

Altere o arquivo `platformio.ini` do seu projeto para incluir a biblioteca diretamente do GitHub:

```ini
[env:meu_projeto]
platform = espressif32 ; ou outra plataforma compatível
board = esp32dev ; ou outra placa desejada
framework = arduino
lib_deps =
    https://github.com/Goytaborgs/QTR-Sensors-Goytaborgs.git
```

### 3. Verificando a Instalação

Para garantir que a biblioteca foi instalada corretamente, compile o projeto:

```sh
pio run
```

Se a compilação ocorrer sem erros, a instalação foi bem-sucedida.

## Conclusão

Agora, sua biblioteca **QTRSensors Custom** está pronta para ser utilizada no seu projeto com o PlatformIO! Basta incluir o cabeçalho da biblioteca no seu código e começar a usar os sensores normalmente:

```cpp
#include <QTRSensors.h>

QTRSensors qtr;

void setup() {
    Serial.begin(115200);
}

void loop() {
    // Seu código aqui
}
```

Agora você está pronto para desenvolver seu projeto com sensores de reflectância utilizando o PlatformIO!
