Antes de criarmos uma API de fato, é importante entender o que é uma API, conceitos que serão utilizados e porque ela é tão utilizada.

## O que significa a sigla API?

API significa Application Programming Interface (Interface de Programação de Aplicação).

## O que é uma API?

APIs são mecanismos que permitem que dois sistemas se comuniquem, usando um conjunto de definições, regras, rotas e protocolos.
Sistemas vão precisar compartilhar informações e também podem precisar pegar informações de outros sistemas, então as APIs servem para isso, é uma forma de viabilizar essa comunicação entre duas aplicações. 

Um bom exemplo: o sistema de software do instituto meteorológico contém dados meteorológicos diários. A aplicação para a previsão do tempo em seu telefone “fala”/se comunica com esse sistema por meio de APIs, pega as infos que eles necessitam e mostra as atualizações meteorológicas diárias no telefone.

## Como as APIs funcionam?

A arquitetura de uma API geralmente é explicada em termos de cliente e servidor.

![image](https://github.com/GOLANG-DO-ZERO/modulo9/assets/167575353/665a05fa-6278-4004-98be-68718a1d4407)

A aplicação que envia a solicitação é chamada de cliente e a aplicação que envia a resposta é chamada de servidor. Então, no exemplo do clima, o banco de dados meteorológico do instituto é o servidor e o aplicativo móvel é o cliente.

E essas APIs podem ser usadas entre duas aplicações de backend, para trocarem informações, ou também o frontend de uma aplicação que solicita dados para o backend para conseguir mostrar as informações em uma tela.
![image](https://github.com/GOLANG-DO-ZERO/modulo9/assets/167575353/9ea0c8db-d7cb-46a9-b8db-8cf883d49663)

Para que essa comunicação seja feita, é usada um formato de dados predefinido para compartilhar informações entre esses sistemas, com o objetivo de obter a integração entre eles. Os mais usados são XML, YAML e JSON para as aplicações web.

## Tipos de APIs

As APIs são classificadas por tipo de arquitetura:

- SOAP (Simple Object Access Protocol) significa “Protocolo Simples de Acesso a Objetos”. Cliente e servidor trocam mensagens usando XML. Utiliza XML para transferir dados entre sistemas e é comumente usado em aplicativos corporativos. Esta é uma API menos flexível que era mais popular no passado.
- RPC (Remote Procedure Call) ou “Chamada de Procedimento Remoto”. O cliente solicita uma ação necessária ao servidor e, como resposta, uma função é executada no aplicativo.
- WebSocket ativa a comunicação bidirecional entre cliente e servidor, tornando o programa mais interativo. As informações são enviadas no formato JSON.
- REST (Representational State Transfer) é a ferramenta mais popular na atualidade. O cliente envia solicitações ao servidor e o servidor usa essa entrada do cliente para iniciar funções internas e retornar os dados de saída ao cliente. Esse tipo de interface opera o protocolo HTTP para troca de dados e é frequentemente usada em aplicações web.

HTTP é um tópico importante de estudo. Recomendo a leitura desse resumo sobre HTTP no meu github pessoal: https://github.com/stephanie-cardoso/resumo-http

## Como são usadas na prática

Pensando em APIs REST, que é o que vamos focar aqui no curso, para que esses sistemas se comuniquem eles vão usar rotas/métodos HTTP.

Vamos pensar no exemplo de API que vamos elaborar o código em breve: um sistema de alunos do curso Golang do Zero.

Pensando em um sistema como esse, vamos precisar:
- Listar informações todos os alunos do curso;
- Listar informações de um aluno específico;
- Adicionar um novo aluno ao curso;
- Atualizar informações de um aluno;
- Remover um aluno do curso;

Para isso, vamos ter rotas na nossa aplicação que vamos acessar para que ações sejam executadas.

Vamos supor que o endereço do nosso sistema seja: `http://curso-golang.com`

Nesse endereço, pdoemos ter várias rotas e ainda usando vários métodos HTTP diferentes:

- GET http://curso-golang.com/students
- GET http://curso-golang.com/students/:id
- POST http://curso-golang.com/students/:id

E cada uma delas vai nos retornar certas informações. E isso quem define somos nós, quando estivermos criando o código dessa API.

E essas rotas podem usar métodos (ou verbos) HTTP diferentes, dependendo da ação que quer ser executada. No resumo sobre HTTP que indiquei acima, tem mais informações e detalhes sobre esses métodos HTTP.

![image](https://github.com/GOLANG-DO-ZERO/modulo9/assets/167575353/4e747dc8-d86a-4122-96c0-698fb820a333)

Quando acessarmos: `http://curso-golang.com/students` teremos como retorno uma lista de alunos matriculados no curso.
E essa lista vem no formato que nós estipularmos, nesse caso, podemos usar o formato JSON.

E junto com as informações de retorno, vai vir um `status code` HTTP, com o resultado da requisição que você fez. Quando for sucesso, recebemos um status code 200. Quando fazemos alguma requisição que deu algum problema de não encontrado, podemos ter como resposta o famoso status code 404.








