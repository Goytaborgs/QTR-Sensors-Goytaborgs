# Instalando a Biblioteca QTR-Sensors-Goytaborgs na Arduino IDE

## Introdução

Este guia explica como instalar e configurar a biblioteca **QTR-Sensors-Goytaborgs** na **Arduino IDE** para uso com sensores de reflectância.

## Passos para Instalação

### 1. Baixando a Biblioteca

1. Acesse o repositório da biblioteca customizada:
   [QTR-Sensors-Goytaborgs no GitHub](https://github.com/Goytaborgs/QTR-Sensors-Goytaborgs)
2. Clique no botão verde **Code** e selecione **Download ZIP**.
3. Aguarde o download do arquivo compactado.

### 2. Instalando a Biblioteca na Arduino IDE

#### Opção 1: Instalação Manual

1. Abra a **Arduino IDE**.
2. No menu, clique em **Sketch** -> **Incluir Biblioteca** -> **Adicionar Biblioteca .ZIP...**.
3. Selecione o arquivo ZIP baixado e clique em **Abrir**.
4. A biblioteca será instalada automaticamente.

#### Opção 2: Instalação Manual na Pasta de Bibliotecas

1. Extraia o arquivo ZIP baixado.
2. Renomeie a pasta extraída para `QTR-Sensors-Goytaborgs`.
3. Mova a pasta para o diretório de bibliotecas da Arduino IDE:
   - No Windows: `C:\Usuários\SeuUsuario\Documentos\Arduino\libraries`
   - No macOS: `~/Documentos/Arduino/libraries`
   - No Linux: `~/Arduino/libraries`
4. Reinicie a Arduino IDE para aplicar as alterações.

### 3. Verificando a Instalação

1. Na Arduino IDE, abra **Arquivo** -> **Exemplos**.
2. Role para baixo e verifique se há uma pasta chamada **QTR-Sensors-Goytaborgs**.
3. Se a pasta estiver presente, a biblioteca foi instalada corretamente.

## Conclusão

Agora sua biblioteca **QTR-Sensors-Goytaborgs** está pronta para ser utilizada! Basta incluir o cabeçalho da biblioteca no seu código e começar a usar os sensores normalmente:

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

Agora você está pronto para desenvolver seu projeto com sensores de reflectância utilizando a Arduino IDE!
