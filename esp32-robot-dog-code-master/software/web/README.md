# Interface de Controle

## Alterar a Interface
(Este procedimento foi testado apenas em sistemas Linux)

Para alterar a interface de controle, siga as etapas abaixo:

1. Localize o arquivo **index.html** no seguinte caminho: `/esp32-robot-dog-code-master/software/web/src`.

2. Após efetuar as alterações necessárias, você precisará converter este arquivo HTML para os formatos **.gz** e **.gz.h**.

3. Para realizar essa conversão, navegue até a pasta: `/esp32-robot-dog-code-master/software/robot_dog_esp32/web`.

4. Apague todos os arquivos dentro da pasta **web**.

5. Agora, abra o terminal e navegue até o seguinte caminho: `/esp32-robot-dog-code-master/software/web`.

6. Execute os seguintes comandos:
   (user a versão 12 ou inferior do Node.js)
   - `npm install`: Isso instalará os pacotes do Node.js necessários.
   - `gulp`: Este comando irá compilar a interface web.

8. O arquivo resultante estará disponível na pasta **web** do projeto.

Agora você concluiu o processo de geração da nova interface com sucesso.
