# Biblioteca para os Sensores de Reflexão Pololu QTR

Versão: 4.1.0<br>
Data de lançamento: 2024-10-29<br>

## Resumo

Esta é uma biblioteca para a IDE do Arduino que facilita a interface com os [sensores de reflexão Pololu QTR][qtr].

## Plataformas Suportadas

Esta biblioteca foi projetada para funcionar com as versões 1.8.x ou posteriores da IDE do Arduino; não testamos com versões anteriores. Esta biblioteca deve ser compatível com qualquer placa compatível com Arduino, incluindo os [controladores Pololu A-Star][a-star].

## Primeiros Passos

### Hardware

A biblioteca QTRSensors oferece suporte às placas de sensores de reflexão de segunda geração [QTR e QTRX da Pololu][qtr], bem como aos [sensores QTR mais antigos][older-qtr]. Antes de continuar, recomenda-se a leitura cuidadosa da [Nota de Aplicação dos Sensores de Reflexão QTR][app-note].

Esta biblioteca também funciona com sensores de reflexão integrados ou projetados para robôs da Pololu, como o [Zumo 32U4 Front Sensor Array](https://www.pololu.com/product/3122). No entanto, as bibliotecas dedicadas a esses robôs (por exemplo, a [biblioteca Zumo32U4](https://github.com/pololu/zumo-32u4-arduino-library)) geralmente fornecem uma interface específica para esses sensores e mais fácil de usar.

### Software

Você pode usar o Gerenciador de Bibliotecas para instalar esta biblioteca:

1. Na IDE do Arduino, abra o menu "Sketch", selecione "Incluir Biblioteca" e depois "Gerenciar Bibliotecas...".
2. Procure por "QTRSensors".
3. Clique na entrada da QTRSensors na lista.
4. Clique em "Instalar".

Se isso não funcionar, você pode instalar a biblioteca manualmente:

1. Baixe o [arquivo da última versão no GitHub](https://github.com/pololu/qtr-sensors-arduino/releases) e descompacte-o.
2. Renomeie a pasta "qtr-sensors-arduino-xxxx" para "QTRSensors".
3. Arraste a pasta "QTRSensors" para o diretório "libraries" dentro do seu diretório de sketchbook do Arduino. Você pode visualizar a localização do seu sketchbook abrindo o menu "Arquivo" e selecionando "Preferências" na IDE do Arduino. Se ainda não houver uma pasta "libraries" nesse local, você deve criá-la.
4. Após instalar a biblioteca, reinicie a IDE do Arduino.

## Exemplos

Vários exemplos de código estão disponíveis para mostrar como usar a biblioteca. Você pode acessá-los na IDE do Arduino abrindo o menu "Arquivo", selecionando "Exemplos" e depois "QTRSensors". Se não conseguir encontrar esses exemplos, a biblioteca provavelmente foi instalada incorretamente e você deve tentar reinstalá-la seguindo as instruções acima.

## Documentação

Para documentação completa desta biblioteca, consulte a [documentação qtr-sensors-arduino][doc]. Se você já estiver nessa página, veja a referência da classe QTRSensors.

## Histórico de Versões

- 4.1.0 (2024-10-29): Funcionalidade adicionada
  - Adicionada a função `writeCalibration`
  - Adicionada a função `readCalibration`
  - Pequenas alterações de estilo em 30 de outubro de 2024
  - Adicionados cabeçalhos ao arquivo de cabeçalho em 29 de outubro de 2024
  - Documentação Doxygen adicionada em 8 de novembro de 2024
- 4.0.0 (2019-03-15): Grande reformulação da biblioteca: em vez de uma hierarquia de classes para diferentes tipos de sensores, a biblioteca agora fornece uma única classe `QTRSensors`, e instâncias dessa classe podem ser configuradas para um tipo de sensor específico. A configuração de pinos de sensores e outras configurações agora é feita usando métodos de classe mais legíveis em vez de parâmetros de construtor. Suporte para calibração usando os modos de leitura ímpar/par foi adicionado.
- 3.1.0 (2018-08-08): Adicionado suporte para sensores QTR e QTRX com controle separado dos bancos de emissores ímpares/pares.
- 3.0.0 (2016-08-16): Biblioteca atualizada para funcionar com o Gerenciador de Bibliotecas do Arduino.
- 2.1.2 (2015-12-03): Corrigido comportamento de `readLine()` para funcionar com múltiplas instâncias (graças a Tandy Carmichael).
- 2.1.1 (2014-05-02): Pequenas melhorias no comportamento de `read()` e limpeza de espaços em branco.
- 2.1.0 (2013-04-18): Melhorados exemplos existentes e adicionados dois novos exemplos para impressão de valores brutos.
- 2.0.2 (2013-04-17): Feito com que os construtores inicializem ponteiros para evitar possíveis problemas.
- 2.0.1 (2012-09-13): Adicionado um atraso de 200 µs após mudanças no estado do emissor para garantir que os sensores não sejam amostrados antes dos LEDs acenderem/apagarem.
- 2.0.0 (2012-02-14): Lançamento inicial da biblioteca no GitHub (com compatibilidade com Arduino 1.0).

[a-star]: https://www.pololu.com/a-star
[app-note]: https://www.pololu.com/docs/0J13
[doc]: https://pololu.github.io/qtr-sensors-arduino/
[older-qtr]: https://www.pololu.com/category/246/older-qtr-sensors
[qtr]: https://www.pololu.com/category/123/pololu-qtr-reflectance-sensors
