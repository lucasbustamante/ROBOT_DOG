# Interface de Controle

## Alterar a Interface
(Este procedimento foi testado apenas em sistemas Linux)

Para alterar a interface de controle, siga as etapas abaixo:

1. Localize o arquivo **index.html** no seguinte caminho: `/esp32-robot-dog-code-master/software/web/src`.

2. Após efetuar as alterações necessárias, você precisará converter este arquivo HTML para os formatos **.gz** e **.gz.h**.

3. Agora, abra o terminal e navegue até o seguinte caminho: `/esp32-robot-dog-code-master/software/web`.

4. Execute os seguintes comandos:
   (use a versão 12 ou inferior do Node.js)
   - `npm install`: Isso instalará os pacotes do Node.js necessários.
   - `gulp`: Este comando irá compilar a interface web.

5. O arquivo resultante estará disponível na pasta **web** do projeto.

Agora você concluiu o processo de geração da nova interface com sucesso.
