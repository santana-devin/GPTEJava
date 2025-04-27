# 01 **Preparando o ambiente**

[ Próxima Atividade](https://cursos.alura.com.br/course/gpt-java-integre-aplicacao-openai/task/147446/next)

A partir desta aula, vamos desenvolver uma aplicação Java para integração com a API da OpenAI.

Utilizaremos o [IntelliJ](https://www.jetbrains.com/pt-br/idea/download) como IDE para desenvolvimento do projeto, além do Java na [versão 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html).

Recomendamos que você utilize as mesmas ferramentas e versões para evitar problemas e dificuldades ao longo das aulas.

> Obs: atente-se aos pré-requisitos deste curso para se certificar de que já possui os conhecimentos necessários para dar andamento neste curso.

# 02 **Criando um projeto com Java**

á aprendemos como funciona a API da OpenAI, fizemos vários testes no Playground e entendemos os campos, as informações e os parâmetros que podemos configurar.

Agora, já temos essa base de conhecimento, então podemos partir para o nosso objetivo principal do curso, que é criar uma aplicação Java que se integre com essa API.

Mas, como funciona essa API? Como nos integramos a ela? Teremos que ler a documentação para entender esse funcionamento? É um bom ponto de partida.

> [Acesse aqui a documentação da OpenAI API](https://platform.openai.com/docs/api-reference)

Vamos acessar a documentação. Trata-se de uma API, então, existem alguns endpoints, URLs, recursos, e toda a documentação da API está aqui. Qual é o URL que precisamos disparar uma requisição HTTP, qual é o verbo, se é GET, se é POST, quais são os parâmetros, etc.

Então, toda a documentação da API está aqui e conseguimos ler, entender como funciona e escrever o nosso código que se integra com essa API.

Porém, será que teremos que desenvolver do zero um código para integrar com essa API? Não é nosso objetivo criar uma biblioteca que se integra com a API. Nosso objetivo é criar uma aplicação que vai ter algum objetivo relacionado com funcionalidades do nosso e-commerce e, por baixo dos panos, essa aplicação tem que se comunicar com a API.

Não queremos ter que escrever o código de integração com a API do zero, pois isso é bastante trabalhoso. E não precisaremos fazer isso.

Voltando na documentação, na aba "Documentation", o primeiro link lá em cima, à esquerda, descendo aqui no menu, uma das últimas opções dentro dessa categoria "Guides" (Guias), chama-se "Libraries" (Bibliotecas).

Na [seção de bibliotecas](https://platform.openai.com/docs/libraries/python-library), a própria documentação lista várias bibliotecas que podemos usar. Não precisamos escrever o código do zero, já existem bibliotecas prontas para isso. Inclusive, o pessoal da própria OpenAI desenvolveu duas bibliotecas, uma em Python e a outra em JavaScript, utilizando o Node.

Mas, e se quisermos usar Java? E se fosse outra linguagem, PHP, C Sharp, Ruby, etc. Também existem bibliotecas para essas linguagens, mas elas não são oficiais, desenvolvidas pela equipe da OpenAI.

Mas podemos pesquisar e dar uma olhada em algumas delas que têm suporte para Java. Inclusive, aqui mesmo na documentação, ele lista várias linguagens e para cada uma ele escolheu uma biblioteca, que não é oficial, mas é uma que acharam que que fazia sentido recomendar.

Procurando aqui pelo Java, temos essa biblioteca chamada `OpenAI-Java`, de uma pessoa chamada Theo Kanning.

> **Java**
>
> [openai-java](https://github.com/TheoKanning/openai-java) by Theo Kanning

Clicando nesse link de `openai-java`, ele vai abrir uma nova aba e vai para o repositório GitHub. Lá no GitHub tem um repositório do código dessa biblioteca. Essa é a biblioteca que vamos utilizar aqui no curso, a biblioteca `openai-java` do Theo Kanning.

Vamos ver como utilizá-la para criar um projeto.

Aqui no curso, vamos utilizar o IntelliJ como IDE. Recomendamos que você também utilize essa mesma IDE para facilitar o aprendizado.

Vamos abrir o IntelliJ, e na tela inicial, escolher a opção "New Project".

Vamos criar o nosso projeto. Vamos nomear o projeto como "openai-java". Vamos salvá-lo no desktop, escolher a opção de linguagem Java, a opção "Maven" para fazer o gerenciamento das bibliotecas.

Em "Advanced Settings", vamos trocar o Group ID, vamos colocar `br.com.alura`. E no ArtifactId, vamos colocar `ecommerce`. Simulando que seria o nosso projeto de e-commerce. Em seguida, vamos clicar no botão "Create".

Ele vai criar um projeto Java, padrão do Maven, aquela estrutura de diretórios. E ele já abriu aqui o `pom.xml` com as declarações do Maven. Inclusive, é no arquivo `pom.xml`que vamos mexer.

Temos um projeto Java, usando o Maven, e não tem nenhuma dependência aqui, nenhuma biblioteca, nenhum framework. Uma dessas bibliotecas, vamos ter que colocar aqui, que é a biblioteca sobre a qual falamos anteriormente: `openai-java`.

Então, vamos voltar lá para o repositório da biblioteca `openai-java` no GitHub. Aqui tem um repositório, tem todo o código fonte, é aberto, podemos explorar.

Rolando a página, tem o README, que tem uma documentação explicando sobre como funciona essa biblioteca.

Ele explica como funciona a biblioteca, tem alguns exemplos, fala qual é o suporte dos recursos da OpenAI, etc. E, em determinado ponto, ele fala como importar essa biblioteca no nosso projeto.

> **Maven**

```xml
 <dependency>
    <groupId>com.theokanning.openai-gpt3-java</groupId>
    <artifactId>{api|client|service}</artifactId>
    <version>version</version>  	 
   </dependency>
Copiar código
```

Então, existem aqui aquelas tags de dependência do Maven. Vamos copiar esse bloco de código e voltar no IntelliJ. Vamos editar o `pom.xml`, logo abaixo do fechamento da tag `properties`. Primeiro, temos que abrir uma tag `<dependencies>`, e dentro dela vamos colar aquela dependência que copiamos.

```xml
<dependencies>
 <dependency>
    <groupId>com.theokanning.openai-gpt3-java</groupId>
    <artifactId>{api|client|service}</artifactId>
    <version>version</version>  	 
   </dependency>
</dependencies>
Copiar código
```

Mas aqui tem uma questão importante. Na linha de artifactId, ele tem três opções: API, Client e Service. A opção que vamos usar aqui é a `service`. Então, deixaremos apenas “service” escrito no artifactId, que ele já encapsula toda a chamada para API, ele já tem umas classes. O serviço é o modo mais fácil de utilizar a integração com a API.

E na versão, precisamos informar qual é a versão dessa biblioteca. No momento em que estamos gravando o vídeo, a versão disponível é `0.18.2`. Então, essa é a versão que recomendamos que você utilize.

```xml
<dependencies>
 <dependency>
    <groupId>com.theokanning.openai-gpt3-java</groupId>
    <artifactId>service</artifactId>
    <version>0.18.2</version>  	 
   </dependency>
</dependencies>
Copiar código
```

Para garantir que o Maven baixou essa dependência, vamos clicar na aba do Maven, no canto superior direito do IntelliJ, e clicar no ícone de "Reload all Maven projects". Depois, podemos expandir aqui a estrutura do projeto "ecommerce" e dentro de "Dependencies" teremos a dependência `com.theokanning.openai-gpt3-java`. Pronto, já baixou a biblioteca.

Podemos fechar o `pom.xml`, abrir o project à esquerda, expandir aqui o projeto, e dentro de `src/main/java`, vamos criar um pacote chamado `br.com.alura.ecommerce`.

E, dentro desse pacote, vamos criar uma classe Java chamada `TestaIntegracao`. Dentro dessa classe precisamos do método `main()`, vamos digitar "main" e pressionar "Tab" para ele completar.

```typescript
package br.com.alura.ecommerce;

public class TestaIntegracao {

  public static void main(String[] args) {
  
    }
}
Copiar código
```

Aqui vamos escrever o código para fazer a integração com a API da OpenAI, usando a biblioteca que acabamos de adicionar no projeto.

Basicamente, o que queremos fazer? Queremos simular aquele mesmo exemplo do Playground. Temos uma mensagem pré-definida para o sistema, uma mensagem pré-definida para o usuário, e queremos enviar, disparar essa requisição e imprimir na tela a resposta.

Podemos começar declarando aqui duas variáveis, `var user` é igual a `"Gere 5 produtos"`. Era basicamente isso que estávamos fazendo. Na linha de baixo vamos criar outra variável, `var system`, é igual a... Aqui vamos copiar aqui aquela mesma mensagem que tínhamos digitado no Playground.

```typescript
public class TestaIntegracao {

    public static void main(String[] args) {
        var user = "Gere 5 produtos";
        var system = "Você é um gerador de produtos fictícios para um ecommerce e deve gerar apenas o nome dos produtos solicitados pelo usuário";
    }
}
Copiar código
```

Temos essas duas variáveis, só para representar qual é o prompt do usuário e o prompt do sistema.

Agora, precisamos fazer a chamada para API, mas não vamos chamar diretamente, vamos chamar usando a biblioteca `openai-java` do Theo Kanning.

Baixamos a biblioteca no projeto, mas como ela funciona? Qual classe chamamos? Como utilizamos essa biblioteca? No próximo vídeo, aprenderemos isso com calma.

# 03 **Integração com a API**

Já criamos a aplicação e adicionamos a dependência da biblioteca Java para fazer a integração com a OpenAI.

Agora, precisamos conhecer a documentação da biblioteca para saber quais classes vamos chamar e, por baixo dos panos, ela fará toda a integração com a API da OpenAI.

Vamos retornar para a documentação da `openai-java` disponível no [repositório do GitHub](https://github.com/TheoKanning/openai-java).

Na seção README do repositório tem uma documentação que explica como funciona a biblioteca, os modos `api`, `client` e `service`, quais são os recursos da API que essa biblioteca suporta, a parte de como usar no projeto utilizando Maven ou Gradle, se estiver utilizando essa outra ferramenta.

Chegamos à parte de usos. Ele explica como usar o modo `service`. Dá alguns exemplos. Tem algumas classes disponíveis no projeto de exemplo. Mas, na minha opinião, essa documentação poderia estar um pouco melhor. Não está muito simples, ela poderia ter mais exemplos, uma explicação mais passo a passo.

Vamos entender o básico de como funciona a biblioteca.

Vamos pegar esse código do `OpenAI Service`, que está descrito na documentação:

```java
OpenAiService service = new OpenAiService("your_token");
CompletionRequest completionRequest = CompletionRequest.builder()
        .prompt("Somebody once told me the world is gonna roll me")
        .model("ada")
        .echo(true)
        .build();
service.createCompletion(completionRequest).getChoices().forEach(System.out::println);
Copiar código
```

Basicamente, é esse que queremos utilizar, mas precisamos fazer algumas alterações para usá-lo no nosso projeto, já dá para aproveitar esse código inicial.

Podemos copiar esse bloco de código e colar logo abaixo da declaração das variáveis de usuário e de sistema.

Vamos começar a fazer as alterações necessárias no bloco que copiamos. Podemos usar `var` para deixar o código mais simples.

Temos uma classe chamada `OpenAiService` que precisamos instanciar. Quando instanciamos essa classe, precisamos passar um token como parâmetro que vem como `your_token` na documentação de exemplo. Em breve vamos entender o que é isso.

Na sequência, ele cria um objeto, `CompletionRequest`. Ele chama essa classe `CompletionRequest`. Mas aqui está a diferença. Não é bem esse objeto que queremos utilizar. Queremos usar aquele modo de chat, que é chamado de `ChatCompletion`. Aqui vamos trocar para outra classe, que é o `ChatCompletionRequest`. Esse é o objeto que queremos utilizar para simular aquele modo de chat, onde fazemos uma pergunta, temos o sistema pré-configurado... Podemos trocar os parâmetros também, igual fizemos no Playground.

```php
var service = new OpenAiService(""your_token);

var completionRequest = ChatCompletionRequest
                .builder()
                .prompt("Somebody once told me the world is gonna roll me")
                .model("ada")
                .echo(true)
                .build();
 service.createCompletion(completionRequest).getChoices().forEach(System.out::println);
Copiar código
```

Não instanciamos o objeto `ChatCompletionRequest`, é uma classe que tem vários métodos estáticos. Ele segue aquele padrão de projeto *Builder* . Tem métodos que vamos encadeando a chamada para ir construindo o objeto.

Além disso, podemos apagar o método `prompt()`. No `model()` é onde passamos qual é a versão do ChatGPT que queremos utilizar. Vamos utilizar a versão do `GPT-4`. Depois vamos entender melhor essas versões, e a questão de custos e tokens.

Em seguida, podemos apagar também a linha de `echo(true)`.

```go
var service = new OpenAiService(""your_token);

var completionRequest = ChatCompletionRequest
                .builder()
                .model("gpt-4")
                .build();
 service.createCompletion(completionRequest).getChoices().forEach(System.out::println);
Copiar código
```

A princípio, deixaremos assim.

Ele faz a request, chama o objeto builder, passa qual é o modelo, manda ele construir. Na linha de baixo, pega o objeto `service`, vamos alterar `createComplition` para `createChatComplition`, ele passa o request como parâmetro e na sequência chama o `GetChoices` para pegar as respostas que foram devolvidas pela API.

Depois vamos entender que a API pode devolver mais de uma resposta. Por enquanto, ela vai devolver apenas uma, mas é possível devolver mais de uma resposta.

Por isso, ele devolve uma lista de escolhas de quais respostas queremos. Só vai vir com uma. E na sequência, como isso é uma lista, podemos chamar um `forEach` e para cada elemento chamar um `System.out::println`.

Então, ele vai disparar a requisição, pegar as respostas, percorrer e dar um `System.out` para imprimir no console. A princípio, aqui está nosso código.

Porém, e as variáveis `User` e `System`? Declarou-as aqui em cima, mas não estamos chamando em nenhum lugar. Faltou passar essas variáveis como parâmetro. Aqui no objeto `ChatCompletionRequest`, naquele *Builder* e tal, passamos apenas o `Model` e já chamamos o método `Build`. Antes de chamar o `Build`, vamos passar aqui, vamos chamar o método `Messages` e aqui podemos passar as mensagens como parâmetro. Ele recebe como parâmetro, esse método `Messages`, uma lista de objetos do tipo `ChatMessage`.

Na verdade, não vamos criar uma string solta, tem que criar um objeto do tipo `ChatMessage`. Então, aqui vamos fazer o seguinte, vamos alterar essa mensagem. Na verdade, vamos criar aqui. Nesse `Messages`, temos que passar uma lista, então, não podemos passar duas variáveis soltas. Vamos chamar a classe `Arrays.asList` para criar uma lista dinâmica e aqui vamos passar os dois objetos, `New ChatMessage` e aqui passamos o `User`, `New ChatMessage` e como parâmetro passamos o `System`.

Então, tem essa classe que encapsula a mensagem em si. Mas como é que ele sabe que essa mensagem aqui é do usuário e a de baixo é do sistema? Porque só passamos a string, mas como é que ele sabe que essa string é do sistema e a outra é a string do usuário? Então, na verdade, quando instanciamos esse objeto `ChatMessage`, temos que passar dois parâmetros aqui. Qual é o tipo, se é sistema ou usuário, e a mensagem em si.

Então, para passar o tipo, tem uma classe chamada `ChatMessageHole`, é um *enum* . Vamos passar `.user.value` e aí, vírgula, nossa mensagem que está na string `user`. Vamos fazer a mesma coisa embaixo, só que no de baixo, aqui não é user, é `system`. Pronto. Então, quando instanciamos o `ChatMessage`, passamos qual que é o perfil, se é usuário ou se é sistema, e a mensagem em si.

Pronto. Aqui está o exemplo de utilização dessa biblioteca Java para fazer a integração com a API da OpenAI. Então, está aqui o código, até que é simples, basicamente três objetos, o `service`, o `request` e as mensagens que são passadas para o `request`. E o `service` é quem vai, de fato, disparar a requisição. Então, a princípio, nosso código está pronto aqui:

```go
var service = new OpenAiService(""your_token);

var completionRequest = ChatCompletionRequest
                .builder()
                .model("gpt-4")
                .build();
 service
       .createCompletion(completionRequest)
       .getChoices()
       .forEach(System.out::println);
Copiar código
```

Porém, e as variáveis `user` e `system`? Elas foram declaradas no início do arquivo, mas não estão sendo chamadas em nenhum lugar. Faltou passar essas variáveis como parâmetro.

Antes de chamar o `build()`, vamos chamar o método `messages()` e nele podemos passar as mensagens como parâmetro.

Esse método `messages()` recebe como parâmetro uma lista de objetos do tipo `ChatMessages`. Então não vamos criar uma string solta, precisamos criar um objeto do tipo `ChatMessage`.

Dentro de `messages()` vamos chamar a classe `Arrays.asList()` para criar uma lista dinâmica. E passaremos os dois objetos: `new ChatMessage(user)` e new `ChatMessage(system)`:

```csharp
var service = new OpenAiService(chave);

var completionRequest = ChatCompletionRequest
                .builder()
                .model("gpt-4")
                .messages(Arrays.asList(
                                new ChatMessage(user),
                                new ChatMessage(system)
                ))
                .build();
Copiar código
```

Mas nós só passamos a string, como ele sabe que a mensagem `user` é da pessoa usuária e a `system` é do sistema?

Na verdade, ao instanciar o objeto ChatMessage, precisamos passar dois parâmetros nele: qual é o tipo, se é usuário ou sistema, e a mensagem em si. Para passar o tipo tem uma classe chamada `ChatMessageRole` e após a vírgula colocamos a mensagem que está na string `user`. Faremos a mesma coisa para o `system`.

```csharp
var service = new OpenAiService(chave);

var completionRequest = ChatCompletionRequest
                .builder()
                .model("gpt-4")
                .messages(Arrays.asList(
                                new ChatMessage(ChatMessageRole.USER.value(), user),
                                new ChatMessage(ChatMessageRole.SYSTEM.value(), system)
                ))
                .build();
Copiar código
```

Pronto. Aqui está o exemplo de utilização dessa biblioteca Java para fazer integração com a API da OpenAI.

A princípio, nosso código está pronto.

Estamos fazendo aquele mesmo exemplo que tínhamos disparado lá no Playground. Vamos ver se vai funcionar.

Vamos rodar aqui essa classe `main()`, vamos clicar com o botão direito, escolher a opção "Run 'testaIntegracao.main()'" e vamos olhar aqui no console o que ele vai devolver como resposta.

Não funcionou, deu uma *exception* aqui. Se olharmos essa *exception* , percebemos que ele está falando: "API key está incorreta, você passou aquela `your_token`, mas essa chave é inválida". E ele dá um link da documentação.

Então, aqui tem uma coisa importante. Lá no Playground, já estávamos logados na nossa conta, tínhamos feito o login, passamos nosso usuário e senha. Então, ele sabe no Playground quem está logado, quem está disparando a requisição, ele sabe de quem cobrar aquelas requisições.

Mas aqui, acabamos de criar um projeto Java no nosso computador, não passamos o nosso login e senha em nenhum lugar.

Então, como é que vai chegar essa requisição na API da OpenAI? Como é que ela vai saber de qual usuário que está disparando essa requisição, de quem que ela tem que cobrar?Por isso que deu esse erro.

Precisamos identificar, de alguma maneira, quem é o usuário que está disparando essa requisição.

Mas no código, não passamos nosso e-mail e senha da conta da API, que fizemos o cadastro na OpenAI.

Aqui, temos que passar uma **chave de API** , e ela é passada como parâmetro na linha 17, na variável `service`. Quando instanciamos esse `OpenAiService`, temos que passar uma chave, mas essa chave precisa ser cadastrada lá na plataforma, lá dentro da nossa conta.

No próximo vídeo, vamos ver como funciona essa questão da chave e como fazemos para cadastrar uma nova chave para poder utilizar no nosso código!

# 04 **Chave da API**

Já escrevemos o nosso código, mas ao executá-lo, falhou devido à chave da API.

Porque precisamos cadastrar uma chave de API na nossa conta e passar essa chave no código, pois é essa chave que vai identificar a pessoa usuária que está disparando essa requisição via código. Para fazer isso, precisaremos acessar a nossa conta no [site da OpenAI](https://platform.openai.com/playground).

No navegador, vamos acessar o Playground e clicar na opção "API Keys" do menu lateral.

## API Keys

Esta página exibe todas as chaves que já foram cadastradas nessa conta. A ideia é que você pode ter uma chave para cada aplicação, para ter um controle melhor.

No fim da página tem um botão chamado "Create new secret key". Para cadastrar uma nova chave, clique neste botão. Se acabou de criar a sua conta, não vai ter nenhuma chave aqui, vai estar vazio, e terá que clicar neste botão para criar a sua primeira chave.

Ao clicar nesse botão, aparece uma pop-up, e pede para dar um nome para essa chave. Vamos chamar de `CURSO_JAVA_OPENAI`. Aqui poderia ser o nome do projeto. Algo que seja descritivo para você saber qual chave é essa, quem está utilizando.

Após escrever o nome da chave, podemos clicar em "Create secret key". Ao clicar nesse botão, ele cria uma chave e mostra uma janela com a chave. E uma coisa importante: **tem que copiar a chave assim que ela for gerada!** Porque quando fechar essa janela, não exibe mais essa chave. Então, se você gerar, não copiar e fechar a janela, terá que apagar e criar uma nova.

Com a chave copiada, clique no botão "Done" para fechar a janela que exibe a chave gerada.

Na seção de API Keys ele exibe quando a chave foi criada, a última vez que foi utilizada, e também tem botões para renomear ou apagar a chave.

Essa chave de API é como se fosse um login e senha. É ela que usamos no nosso código para identificar na requisição quem está disparando a requisição, a conta de quem será utilizada para fazer a cobrança.

## Inserir a chave no código

Vamos voltar ao nosso código. Na linha 17, onde estamos instanciando o OpenAI Service, substituiremos o `your_token` pela chave que copiamos.

> cole a chave gerada nesta linha: `var service = OpenAiService("your_token");`

Após colar a chave gerada, vamos rodar novamente o projeto, clicando com o botão direito e selecionando "Run". Agora, deveria funcionar.

Ele está pensando, não mostrou a mensagem de erro, provavelmente é porque vai dar certo.

```plaintext hljs
ChatCompletionChoice (index=0, message=ChatMessage(role-assistant, content=

1. "SmartWatch com Monitor Cardiaco...
2. "Máquina de Café Expresso Multifuncional"
3. "Conjunto de Panelas Antiaderentes de Última Geração"
4. "Óculos de Realidade Virtual para Jogos"
5. "EcoStore: Torneira de Economia de Água Inteligente", name=null, functionCall=null), finishReason-stop)

Process finished with exit code 0
Copiar código
```

Deu certo e ele devolveu a resposta. Aqui pedimos para ele imprimir os objetos `choices`, o objeto `choice` tem um índice, tem a mensagem, o conteúdo em si.

O que interessa para nós é só o conteúdo. Mas deu certo, ele imprimiu corretamente os nossos produtos. Vamos só alterar o código para corrigir essa questão e ele imprimir apenas o conteúdo da resposta.

Na última linha do código, no `forEach`, vamos trocar o `.forEach(System.out)` por `.forEach(c -> System.out.println(c.getMessage().getContent()))`:

```scss
.createChatCompletion(completionRequest)
.getChoices()
.forEach(c -> System.out.println(c.getMessage().getContent()));
Copiar código
```

Vamos rodar novamente, assim sai no console apenas o conteúdo da resposta, e não as informações do objeto `choice`.

Ao rodarmos novamente, ele imprimiu apenas o conteúdo. Deu certo.

```plaintext hljs
1. "Robot de Limpeza Inteligente EcoClean Pro"
2. "Conjunto de Panelas Antiaderente Super Chef DeLuxe"
3. "Drone Compacto de Alto Desempenho SkyRise FX"
4. "Jardim Vertical Autoirrigável GreenSpace"
5. "Bicicleta Elétrica Efold Urban Mobility"

Process finished with exit code 0
Copiar código
```

Conseguimos fazer a integração via código Java, utilizando aquela biblioteca com a API da OpenAI.

Agora, tem uma coisa importante, talvez tenha percebido.

## Não exponha a chave no código

Essa chave de API é uma informação sensível.Essa informação não pode ser pública, não podemos deixá-la exposta no nosso código, não pode compartilhar isso na internet.

Se alguém tiver acesso à sua chave, a pessoa pode pegar a sua chave e sair disparando requisições da sua conta e estourar o seu limite. Então, não é uma boa prática deixar essa chave exposta dessa forma.

Como esconder essa chave?

Existem várias alternativas para esconder uma informação. Uma delas, que é a mais comum, é usar o recurso de **variáveis de ambiente** . Podemos pedir para o Java: "Quero criar uma variável, quero ler uma informação, mas não vou passar ela diretamente no código, quero que você a carregue de uma variável de ambiente". Vamos fazer essa alteração.

## Criando uma variável de ambiente

Na linha acima da variável `service`, vamos criar uma nova variável chamada `chave`. Como fazer para o Java ler uma variável de ambiente? A própria classe `System`, tem um método chamado `getEnv()`, que é para ler uma variável de ambiente.

E no `getEnv()` passamos qual é o nome da variável de ambiente. Então, vamos dizer para ele: leia uma variável chamada `OEPNAI_API_KEY`, para ficar bem explícito aqui.

Na linha abaixo do `new service`, agora passamos a `chave` como parâmetro.

```csharp
var chave = System.getenv("OPENAI_API_KEY");
var service = new OpenAiService(chave);
Copiar código
```

Se rodarmos o programa desta forma, vai dar erro, porque não configuramos essa variável de ambiente no nosso computador, no nosso sistema operacional. Precisamos configurar essa variável de ambiente com esse nome e atribuir a ela o valor da chave.

Também existem várias formas de fazer isso. Vamos fazer da forma mais simples aqui, configurando na própria classe `Main`.

Clique com o botão direito na classe e selecione a opção "Modify Run Configuration...".

Ele vai abrir uma janela. Tem um campo chamado "Environment Variables", para cadastrar as variáveis de ambiente. Aqui vamos declarar a variável de ambiente. Então, o nome dela era `OPENAI_API_KEY`, tudo em maiúsculo, igual, e colamos a chave.

> Environment Variables: `OPENAI_API_KEY=[cole aqui sua chave]`

Pronto. Então, toda vez que rodar essa classe `Main`, o Java vai considerar que existe uma variável com esse nome e esse conteúdo. Podemos clicar em "Apply > OK".

Agora a chave não está exposta no nosso código, ela está configurada apenas na IDE. Então, podemos compartilhar esse código sem medo, porque não estaremos expondo uma informação sensível.

Será que vai funcionar?

Vamos rodar novamente, só para garantir. Funcionou corretamente.

Ele funcionou da mesma forma que já estava funcionando, mas agora está lendo a informação da variável de ambiente e não mais fixa no meio do código.

## Conclusão

Conseguimos escrever o nosso primeiro código em Java, que faz a integração com a API da OpenAI. Aqui foi só um exemplo, só para começar a aprender a usar essa biblioteca do Java, que faz a integração com a API, e simular aquele mesmo programa que fizemos no Playground.

Na próxima aula, vamos começar a trabalhar, de fato, nas funcionalidades do nosso projeto de e-commerce, para aprender os novos recursos e como utilizar essa integração com a API da OpenAI e ter funcionalidades de inteligência artificial no nosso projeto.



# 05 **Para saber mais: push para o GitHub**


# ATENÇÃO!

Caso você já esteja usando o Git para versionar o código do seu projeto e já tenha criado um repositório remoto no GitHub, **cuidado ao realizar o push!**

> Certifique-se de que você removeu a chave do código e está utilizando variável de ambiente antes de realizar o *push* .

Além disso, é necessário que você crie o arquivo **.gitignore** no diretório raiz da aplicação, com o seguinte conteúdo:

```bash
target/
!.mvn/wrapper/maven-wrapper.jar
!**/src/main/**/target/
!**/src/test/**/target/

### STS ###
.apt_generated
.classpath
.factorypath
.project
.settings
.springBeans
.sts4-cache

### IntelliJ IDEA ###
.idea
*.iws
*.iml
*.ipr

### NetBeans ###
/nbproject/private/
/nbbuild/
/dist/
/nbdist/
/.nb-gradle/
build/
!**/src/main/**/build/
!**/src/test/**/build/

### VS Code ###
.vscode/
Copiar código
```

Lembre-se de que **a chave da API é uma informação sensível e não deve ser compartilhada com outras pessoas, tampouco no código do projeto** .

Para saber mais sobre Git e GitHub, acesse o [curso de Git e GitHub: repositório, commit e versões](https://cursos.alura.com.br/course/git-github-compartilhando-colaborando-projetos).

# 06 **Protegendo a chave de API**

[ Próxima Atividade](https://cursos.alura.com.br/course/gpt-java-integre-aplicacao-openai/task/147448/next)

Você está se preparando para integrar à API da OpenAI em seu projeto e sabe que deve utilizar variáveis de ambiente para proteger sua chave de API. Agora, você precisa ajustar o código para ler a chave de uma variável de ambiente chamada `OPENAI_API_KEY` e configurá-la no ambiente de execução.

Como você deve modificar o código Java para utilizar a variável de ambiente `OPENAI_API_KEY` e garantir que a integração continue funcionando corretamente?

[X]Substituir a linha que contém a chave da API por `System.getenv("OPENAI_API_KEY");`.

Ao substituir a linha com a chave da API por `System.getenv("OPENAI_API_KEY");`, você está acessando o valor da variável de ambiente `OPENAI_API_KEY`, o que protege sua chave de ser exposta no código.


[ ]Declarar `private static final String API_KEY = "OPENAI_API_KEY";` no início da classe.


[ ]Adicionar `System.setProperty("API_KEY", "OPENAI_API_KEY");` antes de usar a chave da API.


[ ]Utilizar `getClass().getResourceAsStream("/OPENAI_API_KEY");` para carregar a chave da API

[ ]Inserir `new FileInputStream("OPENAI_API_KEY");` no local onde a chave da API é necessária.



# 07 **Faça como eu fiz: integrando com a API via aplicação Java**

Nesta aula, vimos como criar uma aplicação Java que se integra com a API da OpenAI, utilizando uma biblioteca para nos auxiliar.

E aí? Já colocou a mão na massa? Chegou a hora de você executar o que foi feito nos vídeos.


# 08 **O que aprendemos?**


## Nesta aula, você aprendeu como:

* Criar um projeto Java no IntelliJ;
* Adicionar ao projeto a dependência do `openai-java`;
* Escrever um código Java que se integra à API da OpenAI;
* Criar uma chave de API na OpenAI e a utilizar no código Java;
* Proteger a chave da API no código, com a utilização de variáveis de ambiente.
