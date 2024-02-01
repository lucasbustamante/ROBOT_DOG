# Robot Dog

## Nota
**Este projeto foi concebido com o propósito de aprendizado e diversão, tendo como inspiração um projeto já existente [aqui](https://www.instructables.com/ESP32-Small-Robot-Dog/). O criador do projeto original mencionou ter descontinuado o desenvolvimento devido à obsolescência das bibliotecas utilizadas. Com a intenção de revitalizar e aprimorar o projeto, minha meta é realizar melhorias significativas, atualizar as bibliotecas e elevar ao máximo o seu potencial.** 

![ROBOT_DOG](https://github.com/lucasbustamante/ROBOT_DOG/blob/main/assets/img/small.jpg?raw=true)

## Hardware
- ESP32
- MPU9250
- 12 servos TowerPro mg90d
- Baterias 18650
- Mini360
- INA219
- TP4056

## Software
- Compatível com Arduino IDE

## A Fazer

- [x] Criação da PCB
- [x] Alteração do Layout dos Controles
- [x] Melhorias na modelagem 3D
- [x] Impressão 3D
- [x] Montagem da Estrutura
- [x] Implementar sensor de energia INA219
- [ ] Implementar sensor de giroscópio MPU9250
- [ ] Atualizaçao das bibliotecas
      

## Como Fazer
### Esquema de ligação PCB

![PCB](https://github.com/lucasbustamante/ROBOT_DOG/blob/main/assets/img/Projeto_atualizado.png?raw=true)


### Calibrar os servos (criar `servoMainProfile`)
- Imprima a ferramenta `calibrador do servo` e instale o servo nela: um prato circular com pontos, 10 graus cada um de 0 a 180.
- Use a ferramenta `tools/servoCalib.ino` e conecte o servo ao pino 14.
- Abra o terminal do Arduino IDE e digite `1500` (e pressione Enter) - isso deve ser o meio do servo e ele deve apontar para o ponto médio da ferramenta impressa.
- Diminua o valor para encontrar os valores `minAngle` e `degMin` (comece com `800` e diminua até o servo parar de se mover).
- Faça o mesmo para encontrar `maxAngle` e `degMax`, mas comece com 2100 e aumente os valores.
- Ótimo, agora sabemos os limites do nosso servo (ou pelo menos quais são os limites para a lib+servo), hora de encontrar posições mais precisas do servo.
- Insira valores até encontrar as posições adequadas para deg30, deg50...deg130, deg150.

### Conexão
#### Credenciais do ponto de acesso WiFi
- Renomeie config_wifi.example.h para config_wifi.h
- Mude APssid para qualquer nome do seu robô, por exemplo, SmallRobotDog
- Altere APpass para senha (8 ou mais caracteres), por exemplo MySup3rPassw0rd

- Após o upload do código para o ESP32, você poderá encontrar o SmallRobotDog WiFi com seu telefone ou tablet.
- Abra o navegador e insira o URL http://192.168.4.1/ e você verá dois joysticks virtuais para controlar o cão-robô.


### Pernas
#### Montagem
- Para montar as pernas corretamente, imprima a ferramenta `calibrador esq e dir` de calibração de perna para os ângulos Beta e Gamma, assim como a ferramenta `calibrador` de ângulo Alpha.
- Ligue o servo e conecte o ESP32 ao seu computador, abra o terminal do Arduino IDE e faça upload do código principal.
- Digite `set servo_to_calib` para definir todos os servos na posição esperada para a ferramenta de impressão.
- Monte as pernas o mais próximo possível das posições esperadas das partes da perna de acordo com a ferramenta (90 graus, 45 graus, 90 graus).

#### Calibração
- Repita os passos 2 e 3 da instrução Pernas->Montagem.
- Digite `set help` para ver a lista de comandos disponíveis, estamos interessados em `XX_HAL_trim_xxxx`, por exemplo, `LF_HAL_trim_alpha`, onde `LF` - perna frontal esquerda, e `alpha` é o nome do ângulo.
- Coloque a ferramenta de ângulo Alpha em cima dos servos das pernas do robô, a superfície da ferramenta deve estar (quase) perfeitamente alinhada com o corpo dos servos, se não estiver, use o comando `XX_HAL_trim_alpha valor_em_graus` para definir o valor de ajuste do servo, por exemplo, `set LF_HAL_trim_alpha -3`, não deve ser muito grande, em outros casos você precisa repetir o passo de Montagem.
- Usando a ferramenta para os ângulos Beta e Gamma, calibre/ajuste os outros servos.
