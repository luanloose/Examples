# Desafio Backend

## Problema

O PicPay é uma empresa de pagamentos que visa revolucionar a forma com que lidamos com dinheiro em nosso dia-a-dia. Um dos passos necessários para completarmos essa missão é implementar a criação de diferentes tipos de contas para utilização do nosso aplicativo. É importante lembrar que o seu sistema será integrado aos nossos painéis internos e ao aplicativo.

Todo o processo começa com a criação de um Usuário. Um usuário pode ter mais de um tipo de conta vinculada a ele. De um **`Usuário (User)`**, queremos saber seu <span style="color:red">Nome Completo, CPF, Número de Telefone, e-mail e Senha. CPFs e e-mails </span>.
 devem ser únicos no sistema. Sendo assim, seu sistema deve permitir apenas um cadastro com o mesmo CPF ou endereço de e-mail.

Os tipos de conta que existem no PicPay são **`Consumidor (Consumer) e Lojista (Seller).`** Todo Consumidor ou Lojista deve estar vinculado a um usuário existente. De um Lojista queremos saber a <span style="color:red">Razão Social, o Nome Fantasia, o CNPJ e seu Username</span>, além do <span style="color:red">id de Usuário</span> que será dono dessa conta. De um Consumidor, queremos saber apenas seu Username, além do id de Usuário que será dono dessa conta. Os usernames devem ser únicos dentro do sistema, mesmo entre contas de tipos diferentes. Devido a algumas limitações do sistema, **`cada Usuário pode ter apenas uma conta de cada tipo.`**

Seu sistema deve ser capaz de listar todos os usuários, além de conseguir trazer informações detalhadas de um usuário específico. Durante a listagem, deve ser possível filtar os resultados por <span style="color:red">Nome ou Username</span>. Para fins didáticos, sua busca deve considerar apenas resultados que comecem com a string especificada na busca. Como exemplo, <span style="color:red">GET /users?q=joao</span> deve retornar apenas Usuários cujos Nomes ou Usernames comecem com a string **`joao`**. Não há a necessidade de lidar com acentos.


Outra funcionalidade do sistema deve ser a possiblidade de contas poderem realizar pagamentos entre si, chamados **`Transações (Transactions)`**. Para a realização de pagamentos, seu sistema deve consumir um serviço externo (mock criado por você) para autorização das movimentações entre as contas. Todas as transações cujo valor seja **`maior ou igual a R$ 100.00`** devem ser **`recusadas`**. Transações de valor **`inferior a R$ 100.00`** devem ser autorizadas. Transações recusadas **`devem`** retornar código **`HTTP 401`**, não autorizadas. **`A lógica de autorização ou recusa de transações deve estar contida no serviço externo.`**

Sua tarefa é desenvolver uma API capaz de cumprir com todos os requisitos especificados.

## Instruções

Para ajudar no desenvolvimento e evitar perda de tempo com código boilerplate, decidimos prover uma estrutura básica para o desenvolvimento da sua solução utilizando a plataforma PHP (Lumen 5.6 + MySQL/MongoDB com Eloquent). A estrutura deve ser utilizada no desenvolvimento da sua solução. É possível fazer download do template inicial aqui.

O primeiro passo para o início do desenvolvimento é escolher qual tecnologia de banco de dados será utilizada no seu projeto. Dependendo da escolha, existem algumas alterações que devem ser feitas no seu projeto base.

Alterar, no arquivo <span style="color:red">.env</span>, o valor da variável <span style="color:red">DB_CONNECTION=mysql|mongodb</span>.
Para verificar se a sua solução está funcionando, utilize o comando <span style="color:red">docker-compose up --build</span> a partir do diretório raiz do projeto. A sua API estará mapeada para a porta <span style="color:red">8000</span> do seu host local. Uma requisição <span style="color:red">GET localhost:8000/</span> vai retornar a versão do Lumen em execução.

**IMPORTANTE:** após a execução do <span style="color:red">docker-compose up --build</span>, na pasta do projeto, execute o comando<span style="color:red"> docker exec -it users-api-php composer install</span>. Quando o volume atual é mapeado para dentro do container, ele sobrescreve a pasta com as dependências instaladas pelo composer, por isso o comando é necessário.
