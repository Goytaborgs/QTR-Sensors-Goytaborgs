# Guia de Uso das Funções writeCalibration e readCalibration

## Introdução

As funções `writeCalibration` e `readCalibration` permitem salvar e carregar os valores de calibração dos sensores de reflexão QTR. Isso é útil para manter ajustes precisos sem a necessidade de recalibração a cada reinicialização do sistema.

## Como Usar

### Escrevendo a Calibração

A função `writeCalibration` grava os valores máximos e mínimos medidos dos sensores para futura referência.

```cpp
void escreverCalibracao()
{
  uint16_t maxSensorValues[sensorCount];
  uint16_t minSensorValues[sensorCount];

  for (int i = 0; i < sensorCount; i++)
  {
    maxSensorValues[i] = SerialBT.parseInt();
  }

  for (int i = 0; i < sensorCount; i++)
  {
    minSensorValues[i] = SerialBT.parseInt();
  }

  qtr.writeCalibration(maxSensorValues, minSensorValues);

  SerialBT.println("Calibração escrita");
}
```

Neste exemplo, os valores de calibração são recebidos via Bluetooth, mas também podem ser definidos manualmente no código.

#### Definindo Valores Manualmente

```cpp
void escreverCalibracao(){
  uint16_t maxSensorValues[qtd_sensor]={554,498,308,521,524,565,551,553};
  uint16_t minSensorValues[qtd_sensor]={1023,1023,667,1023,1023,1023,1023,1023};

  qtr.writeCalibration(maxSensorValues, minSensorValues);
}
```

### Lendo a Calibração

A função `readCalibration` recupera os valores gravados anteriormente.

```cpp
void lerCalibracao()
{
  uint16_t maxSensorValues[sensorCount];
  uint16_t minSensorValues[sensorCount];

  if (qtr.readCalibration(maxSensorValues, minSensorValues) == false)
  {
    SerialBT.println("Calibração não inicializada");
    return;
  }

  SerialBT.print("Max: ");
  for (int i = 0; i < sensorCount; i++)
  {
    SerialBT.print(maxSensorValues[i]);
    SerialBT.print(" ");
  }

  SerialBT.println();
  SerialBT.print("Min: ");
  for (int i = 0; i < sensorCount; i++)
  {
    SerialBT.print(minSensorValues[i]);
    SerialBT.print(" ");
  }
  SerialBT.println();
}
```

Se a calibração ainda não foi inicializada, a função retorna uma mensagem de erro.

### Realizando a Calibração e Lendo os Valores ao Mesmo Tempo

Também é possível realizar a calibração dos sensores e ler os valores máximo e mínimo simultaneamente, como mostrado no exemplo a seguir:

```cpp
void calibrar(){
  led_esp.on(); // Liga o LED do ESP32 para indicar que estamos em modo de calibração
  for (int i = 0; i < 400; i++){
    qtr.calibrate();
  }
  led_esp.off();

  // Faz a leitura dos valores máximo e mínimo dos sensores
  uint16_t maxSensorValues[qtd_sensor];
  uint16_t minSensorValues[qtd_sensor];

  qtr.readCalibration(maxSensorValues, minSensorValues);

  SerialBT.print("Max: ");
  for (int i = 0; i < qtd_sensor; i++) {
    SerialBT.print(maxSensorValues[i]);
    SerialBT.print(",");
  }
  SerialBT.println();

  SerialBT.print("Min: ");
  for (int i = 0; i < qtd_sensor; i++) {
    SerialBT.print(minSensorValues[i]);
    SerialBT.print(",");
  }
  SerialBT.println();
}
```

Essa abordagem permite que os valores sejam lidos imediatamente após a calibração, garantindo que os sensores estejam corretamente ajustados antes de iniciar o uso dos dados.

### Integração no Código Principal

No loop principal, podemos associar comandos via Bluetooth para ler, escrever ou calibrar os sensores:

```cpp
switch (comando)
{
  case 'r':
    lerCalibracao();
    break;

  case 'w':
    escreverCalibracao();
    break;

  case 'c':
    calibrar();
    break;
}
```

Dessa forma, é possível salvar, recuperar e calibrar os sensores conforme necessário.
