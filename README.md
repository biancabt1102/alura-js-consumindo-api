# JavaScript consumindo dados API

## O que estou aprendendo? 

 ### Definições
  JS assíncrono: Há tarefas executadas em "segundo plano".  
  JS síncrono: Uma tarefa é concluida após a outra.

 - #### Event Loop
   É um ciclo que monitora e executa as ações, exemplo:
   ```
      function mandarMensagem() {
         console.log(“Estou aprendendo a programar.”);
      }
      console.log(“O javascript é legal.”);
      mandarMensagem();
      console.log(“Eu gosto de HTML e CSS.”);
   ```
   O processo só é finalizado quando não existem mais ações a serem executadas.

 - #### Call Stack
   É um mecanismo que organiza como irá funcionar o script quando existem muitas funções: qual função está sendo executada, quais estão sendo chamadas dentro de alguma função, etc.

 - #### Task Queue
   É a fila de tarefas assíncronas. Se algo precisa ocorrer em segundo plano ou mais tarde, é nessa fila que ele será adicionado e executado mais tarde.

 - #### Call back
   É quando você deixa algo em espera pra depois utilizar, exemplo, esquentar uma lasanha no microondas e depois comer.

 - #### Promise
    Ele retorna essa promessa que algo vai chegar ou não vai chegar.

    Finalizada com sucesso: *fulfilled*  
    Rejeitada: *rejected*

 - ### Fetch
    É um método que tem como parâmetro obrigatório que é a URL.

 - #### Then
    É um método que faz a requisição em formato de bytes e para isso temos q **converter para JSON** pois fica mais fácil para acessar e o JSON possui a mesma sintaxe que a de um objeto JS.

 - #### Catch
    É utilizado para tratar erros.

 - #### Finally
    Independente do que temos nas promises ele vai exibir.
 
 - ### Async Await
   Ele facilita a leitura de códigos assíncronos e utiliza **try** e **catch** para ver os erros. Ele funciona com **uma promise por vez**.
   ```
      async function buscaEndereco() {
         var consultaCEP = await fetch('https://viacep.com.br/ws/01001000/json/')
         var consultaCEPConvertida = await consultaCEP.json();
         console.log(consultaCEPConvertida);
      }

      buscaEndereco();
   ```
 - #### Promise All
   Ele nos ajuda a fazer várias requisições ao mesmo tempo.

### Métodos
   - #### map()
   Quando você possui um array de endpoints você utiliza o map.

### API
 - #### Fetch API
   Busca dados para convertê-los para o formato JSON.

   ```
      var consultaCEP = fetch('https://viacep.com.br/ws/01001000/json/')
      .then(resposta => resposta.json())
      .then(r => {
         if (r.erro) {
               throw Error('Esse cep não existe!');
         } else 
               console.log(r);
      })
      .catch(erro => console.log(erro))
      .finally(mensagem => console.log('Processamento concluído!'));

      console.log(consultaCEP);
   ```
 - ### Async/await
   Definindo uma função como `async`, podemos utilizar a palavra-chave `await` antes de qualquer expressão que retorne uma **promessa**. A execução async será pausada até que a promise seja resolvida.
   ```
      async function getUser(userId) {
         let response = await fetch(`https://api.com/api/user/${userId}`);
         let userData = await response.json();
         return userData.name; // nas linhas de return não é necessário usar await
      }
   ```
