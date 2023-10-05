# Robot Dog

## Aviso Legal
**Este projeto foi feito principalmente para diversão cerca de um ano atrás. Algumas bibliotecas foram atualizadas, então basicamente não funciona mais. Nem todos os recursos planejados foram lançados. Nenhuma PCB foi criada e isso causa muitos problemas para a maioria de vocês. Sinto muito dizer, mas não vou mais fornecer suporte para isso. É exaustivo e às vezes apenas destrói qualquer intenção de continuar. Este não é um projeto comercial e não pretendo fazer algo como doação. Talvez esteja decepcionando alguém. Desculpe. Projeto encerrado.** 

![Pequeno robô cão](https://github.com/SovGVD/assets/img/small.jpg?raw=true)

## Hardware
- ESP32
- IMU (não implementado)
- 12 servos TowerPro mg90d
- Dois 18650

## Software
- Compatível com Arduino IDE

## A Fazer
- [ ] Usar sensor de energia e IMU

## Como Fazer
### Calibrar os servos (criar `servoMainProfile`)
- Imprima a ferramenta servo_calib e instale o servo nela: um prato circular com pontos, 10 graus cada um de 0 a 180.
- Use a ferramenta tools/servoCalib.ino e conecte o servo ao pino 14.
- Abra o terminal do Arduino IDE e digite `1500` (e pressione Enter) - isso deve ser o meio do servo e ele deve apontar para o ponto médio da ferramenta impressa.
- Diminua o valor para encontrar os valores `minAngle` e `degMin` (comece com `800` e diminua até o servo parar de se mover, depois volte um passo, por exemplo, defina 790 - servo moveu, 780 - servo moveu, 760 - servo não se move, use 780).
- Faça o mesmo para encontrar `maxAngle` e `degMax`, mas comece com 2100 e aumente os valores.
- Ótimo, agora sabemos os limites do nosso servo (ou pelo menos quais são os limites para a lib+servo), hora de encontrar posições mais precisas do servo.
- Insira valores até encontrar as posições adequadas para deg30, deg50...deg130, deg150.

### Pernas
#### Montagem
- Para montar as pernas corretamente, imprima a ferramenta/template de calibração de perna exatamente como ela é e outra espelhada para o outro lado do robô para os ângulos Beta e Gamma, assim como a ferramenta de ângulo Alpha.
- Ligue o servo e conecte o ESP32 ao seu computador, abra o terminal do Arduino IDE.
- Digite `set servo_to_calib` para definir todos os servos na posição esperada para a ferramenta de impressão.
- Monte as pernas o mais próximo possível das posições esperadas das partes da perna de acordo com a ferramenta (90 graus, 45 graus, 90 graus).

#### Calibração
- Repita os passos 2 e 3 da instrução Pernas->Montagem.
- Digite `set help` para ver a lista de comandos disponíveis, estamos interessados em `XX_HAL_trim_xxxx`, por exemplo, `LF_HAL_trim_alpha`, onde `LF` - perna frontal esquerda, e `alpha` é o nome do ângulo.
- Coloque a ferramenta de ângulo Alpha em cima dos servos das pernas do robô, a superfície da ferramenta deve estar (quase) perfeitamente alinhada com o corpo dos servos, se não estiver, use o comando `XX_HAL_trim_alpha valor_em_graus` para definir o valor de ajuste do servo, por exemplo, `set LF_HAL_trim_alpha -3`, não deve ser muito grande, em outros casos você precisa repetir o passo de Montagem.
- Usando a ferramenta para os ângulos Beta e Gamma, calibre/ajuste os outros servos.
