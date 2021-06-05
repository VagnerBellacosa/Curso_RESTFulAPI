# Curso_RESTFulAPI

Apontamentos iniciais de RESTFul API

# RESTFul API

Você sabe o que é **API**? Essas três letras formam a sigla para **Application Programming Interface**, que pode ser traduzido como *“Interface de Programação de Aplicações”*.

De maneira simplificada, podemos dizer que as API são conjuntos de instruções e padrões de programação que servem para fornecer dados e informações relevantes de uma determinada aplicação.

Dentro do universo das APIs existe um padrão conhecido como *RESTful*. Nesta introduçao vamos falar por linhas gerais sobre as **API Restful** e entender um pouco mais sobre eles, seus conceitos, princípios e formas de criação. 

### Afinal, para que servem as APIs?

As APIs estão presente na maioria das aplicações e sistemas inteligentes que utilizamos, sejam eles focados em B2B ou em recursos do dia a dia, como o uso do app de navegação. Grande parte das APIs são criadas para integração entre um software de uma empresa e produtos associados. Um bom exemplo são os sistemas de gerenciamento de hotéis.

Eles possuem APIs para que dados de outros sistemas (como o responsável pelas reservas online ou a distribuição das diárias nos canais de venda) integrem as informações com o sistema de gestão, ampliando a precisão da base de dados e o volume de informações.

As APIs utilizam uma rede para o tráfego de informações, de uma forma padronizada. Isso pode ser através da internet ou de uma rede local.

Um bom exemplo é o Google Maps. Muitos sites e aplicações com foco em geoprocessamento possuem APIs para captar dados do Maps. Elas os adaptam para conseguir as informações necessárias e exibir pontos de interesse dentro de um serviço, como se fizesse parte da arquitetura do site ou da aplicação.

### Quais são os formatos de API?

Existem três formas de API:

- Local;
- Baseada em programa;
- Baseada em web.

A *API RESTful*, nosso foco de hoje, é uma API em *web*, baseada em protocolo *HTTP*, um formato que vem se tornando padrão de uso conforme vivenciamos o aumento de soluções digitais hospedadas em nuvem. Mas além dele, outros padrões e abordagens estão sendo utilizados com mais frequência, como *gRPC* e *GraphQL*.

Quer um exemplo de como as APIs são variadas e podem até mesmo ser divertidas? Existe uma para auxiliar na construção de sites que é capaz de preencher todos os espaços de foto e links para facilitar a visualização do projeto. A grande questão é que ele preenche TODOS os espaços com fotos e links para fotos do ator Nicolas Cage.

Parece bobo, não é? Mas a ideia é facilitar a vida do desenvolvedor de modo divertido, auxiliando a enxergar o tamanho das imagens e os links de forma rápida.

### O que são as APIs RESTful?

*API RESTful* é uma interface que fornece dados em um formato padronizado baseado em requisições HTTP.

Por exemplo: A API do Facebook, que permite que você se autentique em aplicações externas ao Facebook (como o login da PlayStation Network, que é requisitada aos jogadores do PlayStation 4). Ela fornece dados do Facebook para essas aplicações, facilitando o cadastro e o acesso.

**API RESTful** fica parada até que acontece uma requisição. É como um carro estacionado que só é ativado após a ignição com a chave. No caso do exemplo do login da PSN usando os dados do Facebook, a API do Facebook não fica processando os dados de todos os seus usuários continuamente, ela espera até que um usuário peça a permissão para se autenticar.

As APIs Restful aumentam a performance para situações de concorrência, ou seja, quando muitas pessoas estão pedindo a mesma coisa ao mesmo tempo. Elas utilizam verbos para definir qual é a finalidade da requisição que está sendo enviada. Os verbos são:

- **GET:** A requisição é um pedido de dados para a API. A API vai buscar os dados solicitados em algum banco e, provavelmente, vai retornar em formato JSON (formato de notação de objeto JavaScript);
- **POST:** Tipo de requisição utilizada para criar um recurso em uma determinada API. São chamados de recursos o objeto que está sendo tratado naquela API.
- **PUT:** Requisição utilizada para atualizar o recurso indicado com alguma informação.
- **PATCH:** Requisição feita para atualização de somente uma parte de um recurso.
- **DELETE:** Requisição para excluir um dado.

Essas operações são acessadas por meio de Endpoints, que são as URLs nas quais são feitas as requisições. Cada requisição aos endpoints é composta por:

### O método HTTP;

Um cabeçalho requisição, que pode conter informações como dados de autenticação da API, dados de origem da requisição e formato do retorno.

Embora o corpo da requisição e do retorno possam utilizar outros formatos, de modo geral é utilizado o formato JSON como padrão, tanto para o envio quanto para o retorno das requisições. Esse formato é escolhido, principalmente, por sua compatibilidade simples entre as linguagens e frameworks existentes, tanto de backend quanto de frontend.

#### Exemplos de requisições das APIs
Considerando que temos um recurso chamado Person, com os atributos id, name e age, e que temos um domínio da nossa API chamado “minhaurl”, nós podemos ter os seguintes endpoints (lembrando que por padrão, as APIs Restful tem o nome no plural do recurso que ela está tratando):

https://minhaurl/people – Utilizando o método GET – Irá retornar todas as pessoas cadastradas, por exemplo:

{
   "status":200,
   "data":[
      {
         "id":1,
         "name":"John Doe",
         "age":20
      },
      {
         "id":2,
         "name":"Mary Ann",
         "age":25
      }
   ]
}

https://minhaurl/people/{id} – Utilizando o método GET – Irá retornar as informações do usuário com o id informado. Como por exemplo https://minhaurl/people/1, irá retornar as informações do recurso Person com o id 1:
{
   "status":200,
   "data":[
      {
         "id":1,
         "name":"John Doe",
         "age":20
      }
   ]
}

https://minhaurl/people – Utilizando o método POST – Irá criar um novo recurso do tipo Person. Para isso, é necessário enviar um corpo de requisição e a API irá retornar um status HTTP indicando se foi possível ou não criar este recurso, como por exemplo:
Corpo da Requisição:

{
   "Name": "Peter Jones",
   "age":20
}

Corpo do Retorno:

{
   "status":200,
   "success":true
}

https://minhaurl/people/{id} – Utilizando o método PUT – Irá atualizar o recurso do tipo Person com o id informado. Para isso, é necessário enviar um corpo de requisição e a API irá retornar um status HTTP indicando se foi possível ou não criar este recurso, como por exemplo:
Corpo da Requisição:

{
   "id":1,
   "Name": "John Smith",
   "age":20
}

https://minhaurl/people/{id} – Utilizando o método PATCH – Irá atualizar o recurso do tipo Person com o id informado. A diferença do método PATCH para o método PUT é que no PATCH não é necessário informar todos os atributos do recurso, apenas o(s) que será(ão) atualizado(s). Para isso, é necessário enviar um corpo de requisição e a API irá retornar um status HTTP indicando se foi possível ou não criar este recurso, como por exemplo:
Corpo da Requisição:

{
   "age":25
}

https://minhaurl/people/{id} – Utilizando o método DELETE – Irá excluir o recurso com o id informado. Como por exemplo https://minhaurl/people/1, irá excluir o recurso Person com o id 1:
Corpo do Retorno:

{
   "status":200,
   "success":true
}

Ainda é possível não depender de APIs para desenvolvimento, mas quando o assunto são integrações entre serviços, elas dominam. APIs não são essenciais para deixar projetos robustos e funcionais, mas são imprescindíveis para integrar esses projetos com serviços de terceiros e outras aplicações que utilizam frameworks como React, VueJS e Angular.

A grande sacada das APIs RESTful é que elas servem para estruturar qualquer aplicação web para os dias de hoje, onde temos muitos dados e muitas pessoas trocando informações. Sua principal utilização é na troca de informações entre Apps e sistemas, tudo de forma padronizada.

### Criação de uma API

Para criar uma API é necessário ter conhecimentos intermediários em protocolo HTTP, servidores web (como Apache e NGINX) e uma linguagem de programação para web, como PHP, Javascript, Ruby e Python. Isso estamos falando do “starter pack”, pois é possível ir além e utilizar linguagens de outros paradigmas, como Golang e Clojure.

JavaScript também é uma linguagem importante a se dominar para a criação de APIs. Já existem alguns deles totalmente em JS, tanto para frontend quanto para backend. O JavaScript é essencial, uma vez que tudo que mexe com frontend na web acaba esbarrando com ele.

Não é obrigatório saber JavaScript para backend, ou seja, criar as APIs. Isso porque elas podem ser criadas usando qualquer outra linguagem que permita uma interface HTTP.

No momento da criação é importante ter em mente o que você pretende captar e transmitir de uma aplicação para outras. Codificar uma API pode não ser totalmente complexo, porém, é muito importante que você se atenha aos seguintes aspectos:

### O escopo da aplicação;

Como serão fornecidos os dados;

Outro ponto importante: Não se esqueça de analisar quais tipos de requisição podem gerar gargalos na aplicação (excesso de pedidos que demandam estratégias como cache, por exemplo).

As APIs são altamente funcionais e pretendem facilitar a execução de tarefas de uma maneira significativa. Quer saber mais dicas de desenvolvimento e descobrir outros temas, como dicas sobre frameworks e a importância do SEO para desenvolvedores?
