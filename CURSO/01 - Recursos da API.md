# 01 **Apresentação**

Olá, tudo bem? Vamos começar mais um curso aqui na Alura. Meu nome é **Rodrigo Ferreira** e serei o instrutor que irá te acompanhar nesta jornada

> **Audiodescrição:** Rodrigo se autodeclara como um homem de pele branca. Tem cabelos curtos e castanho-escuros, e não tem barba. Está usando *headphone* branco e camiseta roxa. Ao fundo, uma parede iluminada de azul com alguns quadros decorativos.

Estamos aqui para convidar você a fazer mais um curso voltado para **inteligência artificial com programação** .

No caso, utilizaremos a linguagem de programação **Java** e aprenderemos como desenvolver um código que se integra com a API da OpenAI — a famosa empresa do ChatGPT. Essa empresa possui uma API que permite desenvolver aplicações, seja com Java ou com outras linguagens, e fazer uma integração com essa API para ter acesso aos recursos de IA que ela disponibiliza.

## O que vamos aprender?

A ideia central do curso é desenvolver uma aplicação utilizando a linguagem **Java** e entender como **integrar essa aplicação com a API da OpenAI** para utilizar esses recursos de inteligência artificial.

Para isso, vamos desenvolver do zero uma aplicação utilizando Java e algumas bibliotecas que vão facilitar nosso objetivo de integrar a aplicação com essa API e usar os recursos dessa ferramenta.

Durante o curso, vamos aprender algumas **boas práticas** dessa integração e como utilizar o **recurso de chat** para enviar perguntas e a inteligência artificial da OpenAI gerar respostas.

Então, vamos aprender sobre ***prompt engineering*** (engenharia de prompts) e ***prompt template*** (template de prompts) para otimizar essas mensagens enviadas na hora de integrar a nossa aplicação com a API.

Nesse processo, vamos entender quais são os **modelos do GPT** disponíveis nessa API. Utilizaremos a versão 4 e a 4 Turbo, as últimas versões disponíveis no momento da gravação desse curso, para aproveitar ao máximo as mais recentes melhorias desenvolvidas pela OpenAI.

Nós também vamos entender quais são as **diferenças** entre esses modelos, principalmente em relação aos **custos** , para que possamos fazer otimizações no código na hora de escolher entre um modelo e outro.

Vamos aprender como funcionam esses custos, e que grande parte deles está relacionada com os **tokens** . Entenderemos no curso como a OpenAI identifica esses tokens e faz essa cobrança, e como podemos fazer em nosso código uma **contagem de tokens** para ter uma estimativa de custos e uma escolha dinâmica do modelo a ser utilizado na integração.

Por fim, vamos aprender também sobre **tratamento de erros** . Como vamos nos conectar com uma API externa que não foi desenvolvida por nós e sobre a qual não temos controle, eventualmente pode acontecer um problema, como a API pode ficar fora do ar, então nosso código deve ser preparado para lidar com essas situações inesperadas. Vamos aprender algumas boas práticas para lidar com erros ao se conectar com a API da OpenAI.

## Pré-requisitos

Para conseguir acompanhar o curso com mais tranquilidade, o conhecimento básico necessário é de linguagem **Java** e **orientação a objetos** .

> Aqui na Alura, temos uma formação focada em Java e orientação a objetos. Com ela, você terá todos os conhecimentos necessários para desenvolver nosso projeto.

Não é preciso ter conhecimentos avançados, nem conhecimentos sobre *frameworks* como o Spring e JPA, porque o foco não será desenvolver uma aplicação complexa usando essas tecnologias. O foco será na **integração** de uma aplicação Java com a API. Portanto, apenas conhecimentos básicos de Java e orientação a objetos já serão suficientes.

Também é importante que você conheça o **Maven** . O conhecimento também não precisa ser aprofundado, pois utilizaremos o Maven como ferramenta para gerenciar as dependências do nosso projeto.

Vamos precisar adicionar dependências no projeto, que serão bibliotecas para nos ajudar com essa integração com a API da OpenAI. Portanto, você precisa ter uma noção do que é o Maven, como funciona a estrutura de diretórios de uma aplicação Java que utiliza o Maven e como funciona a questão de bibliotecas e dependências que podemos adicionar no projeto.

Além disso, como vamos fazer uma integração com uma API, é importante que você também tenha uma noção básica sobre o que é uma **API Rest** : como ela funciona, noções do protocolo HTTP, o que é a ideia de disparar uma requisição, receber uma resposta, código HTTP. Afinal, nossa integração ocorrerá via API Rest.

Também é necessário ter noções básicas sobre **inteligência artificial generativa** . Se você está aqui, provavelmente já conhece e deve ter utilizado o ChatGPT. Não vamos ensinar nesse curso o que é o ChatGPT ou o que é a ideia de inteligência artificial; nós vamos apenas usar essa ferramenta.

Esperamos que você goste bastante dessa jornada. Não se esqueça de, ao final, deixar sua **avaliação** ! Ao longo do curso, se você tiver alguma **dúvida** , pode recorrer ao nosso **fórum** e também participar da nossa comunidade do **Discord** .

Tudo pronto?! Nos encontramos na primeira aula!

# 02 **Precificação da OpenAI**

## Aviso importante sobre mudanças de precificação da OpenAI

No momento em que este curso foi desenvolvido, a OpenAI disponibilizava o que chamamos de “free tier”, ou seja, um “nível gratuito” de uso, voltado para facilitar o acesso à tecnologia e incentivar a experimentação. Com isso, era possível fazer um número limitado de requisições aos modelos e obter respostas sem custo para quem está aprendendo.

Porém, a partir de junho/2024, a OpenAI modificou seus termos de uso e extinguiu o “free tier” da forma como era utilizado anteriormente. A partir de então, a plataforma exige um débito inicial de pelo menos US$ 5 (cinco dólares) para o nível mais básico de uso dos modelos.

O pagamento é feito via cartão de crédito, que fica cadastrado no sistema da OpenAI. Para isso é necessário que você configure as informações pessoais de sua conta, incluindo o cartão de crédito a ser utilizado e adquira um valor de no mínimo 5 dólares de crédito, dentro do [painel de uso](https://platform.openai.com/organization/usage).

Após o esgotamento do crédito, é possível optar por continuar usando a API dentro dos limites de taxa que melhor se adaptem às suas necessidades. Para entender melhor sobre esses limites, é recomendado que você acesse a documentação da OpenAI sobre [limites de taxa](https://platform.openai.com/docs/guides/rate-limits/usage-tiers?context=tier-free).

É importante entender que os limites de taxa são definidos no nível da organização e no nível do projeto, não no nível do usuário, variando conforme o modelo sendo utilizado. Você pode conferir os limites de taxa e uso da sua organização acessando a seção de [limites](https://platform.openai.com/settings/organization/limits) nas configurações da sua conta.

Conforme o uso da API da OpenAI e os gastos associados aumentam, sua conta é automaticamente elevada para o próximo nível de uso. Isso normalmente resulta em um incremento nos limites de taxa para a maioria dos modelos.

Você pode conferir mais sobre os preços de uso da API na seção de [pricing](https://openai.com/api/pricing/) da página inicial da OpenAI.

> **IMPORTANTE** : Você pode estabelecer um **orçamento mensal** nas [configurações de cobrança](https://platform.openai.com/settings/organization/limits) e configurar este orçamento para interromper o atendimento às suas solicitações após determinado limite. **Mantenha o recurso auto recharge (recarga automática) desativado** para que a API deixe de funcionar ao atingir o limite de créditos.

> Reiteramos que esta cobrança é uma política interna da OpenAI e **recomendamos fortemente que você estabeleça limites de valor para evitar cobranças desnecessárias** .




# 03 **Criação e configuração da conta**

Vamos iniciar nosso curso, cuja proposta é criar uma aplicação utilizando a linguagem Java, que se integrará com a API da OpenAI. Primeiramente, precisamos **conhecer essa API** , entender seus recursos e funcionalidades, bem como a maneira de nos integrar a ela. Para isso, nada melhor do que acessar a [documentação da OpenAI](https://openai.com/) para aprender sobre essas questões.

## Cadastro na OpenAI

Na página inicial do site da OpenAI, encontramos uma propaganda sobre a ferramenta e um menu no topo da página. Nosso foco está na segunda opção, "**API** ", então vamos clicar nela. É a API que vamos utilizar e com a qual vamos criar nosso projeto e realizar as integrações. Esse link conta com um submenu de várias opções — vamos clicar em "**Overview** " (visão geral).

Ao acessar o *Overview* da API, somos direcionados para a página que apresenta **informações básicas** sobre a API da OpenAI. Nesse espaço, encontramos uma explicação detalhada sobre o que é essa API e como ela funciona. Temos também informações sobre os modelos do GPT, o que vamos aprender durante o curso, além de outras ferramentas para geração de imagem e transcrição de áudio.

No final da página, há um link chamado "***Get Started*** " (começar), que é nosso ponto de partida. Vamos clicar nele e nos redirecionar para uma nova aba de cadastro na OpenAI.

Vale lembrar que essa ferramenta é paga e, para utilizá-la, é preciso ter uma **conta** . Quando criamos uma conta pela primeira vez, inclusive, ganhamos alguns créditos para fazer testes. O importante é ter uma conta cadastrada.

Portanto, caso você ainda não tenha uma conta, é necessário fazer o **registro** , preenchendo o formulário com endereço de e-mail ou optando por fazer login com o Google, com a conta da Microsoft ou da Apple.

Para ilustrar, vamos fazer um cadastro novo. Se você já tem uma conta no site da OpenAI, pode pular essa parte e apenas realizar o login com seus dados.

No formulário de cadastro, vamos clicar em "**Continuar com Google** " e escolhemos uma conta do Gmail para vincular ao nosso cadastro. Depois disso, é necessário preencher alguns dados num formulário: nome, sobrenome, organização (opcional) e data de aniversário. Então, clicamos no botão "**Agree** " (concordar) e o processo de criação de conta é iniciado, assim como em qualquer outro site.

Após a criação da conta, surge um *Captcha* para garantir que não é um robô que está criando contas e, após resolvê-lo, somos direcionados para a página de boas-vindas. Nela, temos uma dashboard com informações gerais sobre a OpenAI e sobre a plataforma e um menu à esquerda, que permite explorar mais sobre a ferramenta.

## Configurando limites de custos

A primeira coisa que você deve fazer após criar a sua conta, ou após logar caso já tenha uma conta, é se informar sobre os **custos** da API.

Ela não é gratuita, mas, ao criar a conta pela primeira vez, a OpenAI oferece um **crédito** cujo valor e período de utilização podem variar. No momento da gravação desse vídeo, são 5 dólares por 3 meses, mas isso pode mudar no futuro.

No menu à esquerda, clicaremos na última opção, chamada "***Settings* "(configurações) > "*Billing* (faturamento)** . Nessa área, encontramos informações sobre faturamento, uso de crédito e dados bancários para débito.

Quando os créditos acabarem, será necessário cadastrar um cartão de crédito para continuar utilizando a API. Para isso, clicamos em "***Payment Methods*** " (métodos de pagamento). Caso esteja disponível a opção, surgirá um botão para cadastramento do cartão de crédito, permitindo a continuação da utilização dos recursos. Não faremos isso agora, pois usaremos o crédito do período gratuito.

Outro ponto importante a ser verificado no menu à esquerda é a opção "***Limits*** " (limites), onde é possível configurar limites de utilização de crédito. Esse passo é essencial para evitar surpresas com relação à cobrança.

Caso você já tenha excedido o crédito ou período gratuito e cadastre o cartão de crédito, aparecerão dois campos para habilitar um **limite de uso** para liberar uma notificação via e-mail caso você atinja esse limite, e um segundo limite para barrar as requisições que você fizer para a API após atingi-lo. Por exemplo, você pode cadastrar um limite máximo de 10 dólares; após gastar esse valor, suas requisições são bloqueadas.

Com a conta criada, limites configurados e cartão de crédito cadastrado (quando necessário), temos tudo pronto para utilizar a ferramenta.

Na sequência, aprenderemos **como funciona essa API** . Agora que já temos a conta criada, como fazemos para usá-la? Escrevemos nosso código usando Java ou outras linguagens de programação? Há outra forma de conhecer melhor, sem ter que ler a documentação? Vamos explorar essas questões com calma na sequência.


# 04 **Chat completion**


Agora que já aprendemos a criar uma conta, podemos começar a utilizar os **recursos** que essa ferramenta nos disponibiliza.

> **Observação:** O instrutor deslogou da conta criada no vídeo passado e logou com sua conta pessoal. Essa conta já possui um cartão de crédito cadastrado e já passou pelo período gratuito. Com isso, temos acesso a mais recursos disponíveis para conhecer ao longo do curso.

## Detalhes de cobrança

Já que estamos na tela de *Billing* (cobrança), vamos explorar os detalhes mencionados no vídeo anterior. Nessa conta, mostra-se no visor de cobrança que, nesse mês, até o momento, gastamos 5 dólares e 52 centavos.

Abaixo do visor de cobrança, há a opção de ***Payment Methods*** (Métodos de Pagamento). Clicando nela, vamos para uma nova aba que mostra o cartão cadastrado. Se clicarmos no botão "*Add payment method* ", podemos adicionar outros cartões de crédito e métodos de pagamento.

No menu à esquerda, vamos clicar em "***Limits*** " para voltar àquela tela de limites. Vamos entender melhor sobre os campos mencionados no vídeo anterior.

Nessa conta, já aparecem esses dois campos na metade inferior da página: "***Set a monthly budget*** " (configure um orçamento mensal) e "***Set an email notification threshold*** " (defina um limite de notificação por e-mail).

Na conta do instrutor, o limite para notificação por e-mail está configurado como 10 dólares. Portanto, ao atingir esses 10 dólares no mês, a ferramenta enviará um e-mail para nos alertar.

Já o orçamento mensal é o limite que, de fato, não poderá ser ultrapassado. Nessa conta, esse orçamento está configurado como 20 dólares. Portanto, se por acaso, dentro de um mês, ultrapassarmos esses 20 dólares, a ferramenta bloqueia as requisições, para que não ultrapasse esse valor estipulado.

Isso serve para termos controle de gastos, para não exceder o limite do nosso cartão de crédito e ter uma surpresa quando a fatura fechar com um valor gigantesco. Portanto, lembre-se de configurar esses limites na sua conta!

## Modelo de Chat

Após criar a conta e entender como funciona a cobrança, podemos começar a, de fato, utilizar a ferramenta.

Mas, antes de escrever o código em Java da nossa aplicação, primeiro precisamos conhecer os **recursos disponíveis** nessa API da OpenAI. Precisamos entender como funciona e como podemos testar.

Não precisamos ler toda a documentação para entender. A própria ferramenta tem um recurso chamado "***Playground*** " que permite fazer testes no próprio navegador. Com isso, conseguimos entender melhor o funcionamento dessa ferramenta antes de partir para o código. Com isso, conseguiremos escrever o código com mais assertividade, sabendo exatamente o que precisamos fazer.

Para acessar esse recurso, clicamos em "*Playground* " no menu à esquerda. Nessa nova página, no canto superior esquerdo da tela, há um menu suspenso com o texto "***Assistants*** ". Ele serve para trocar o modelo que vamos utilizar; ou seja, por padrão, o modelo configurado é o de assistente.

Vamos trocar para o modelo de "**Chat** ". Queremos utilizar a ferramenta nesse modo de chat, onde a pessoa usuária faz uma pergunta e a ferramenta vai gerar uma resposta baseada no GPT.

Após fazer isso, a página vira um chat com algumas opções e recursos diferentes. Há um campo à esquerda chamado ***System*** , a parte central tem o formato de chat, e à direita temos um menu com vários campos de configurações ajustáveis. Vamos, com calma, entender como funciona essa ferramenta.

No campo "***User*** ", no centro superior da tela, é onde vamos simular uma pessoa usuária enviando uma pergunta para a API.

## Prompts no modelo de Chat

A partir de agora, vamos começar a trabalhar no contexto da nossa aplicação, o projeto do nosso curso, que será um **e-commerce** . Ou seja, vamos imaginar que trabalhamos em um e-commerce e queremos usar a integração com a OpenAI para melhorar nossos serviços.

Vamos fazer alguns testes nesse chat primeiro para entender como essa ferramenta funciona e como ela pode ajudar no nosso trabalho nesse e-commerce fictício.

Imagine que vamos usar a ferramenta para **gerar nomes de produtos** . Ao lado de "User" temos um campo de texto editável em que escreveremos esse pedido:

> **User:** *Gere cinco produtos fictícios para um e-commerce.*

Para enviar essa pergunta e ver a resposta que a API vai gerar usando o modelo do GPT, clicamos no botão verde "***Submit*** " na parte inferior do centro da tela. Temos que esperar um pouco para ele começar a gerar a resposta.

A resposta começa a aparecer na tela sob o nome de usuário "**Assistant** ". Para essa pergunta, a ferramenta gerou uma lista de cinco produtos diferentes com uma pequena descrição para cada um:

> **Assistant:**
>
> **1. Smart Fridge Pro:** Uma geladeira inteligente que se conecta ao seu smartphone e permite controlar a temperatura, fazer compras online diretamente do seu painel digital e enviar lembretes para repor itens essenciais.
>
> **2. Robô de Limpeza MaxClean:** Um robô de limpeza autônomo com funções avançadas, como mapeamento inteligente da área, limpeza programada, detecção de obstáculos e capacidade de limpar diferentes tipos de superficie.
>
> **3. Pulseira Fitness FitLife:** Uma pulseira de atividade física com monitoramento contínuo de frequência cardíaca, contador de passos, calorias queimadas, distância percorrida, além de oferecer recursos de monitoramento do sono e uma interface intuitiva no aplicativo do celular.
>
> **4. Óculos de Realidade Virtual 360Vision:** Óculos de realidade virtual de última geração, oferecendo uma experiência imersiva em 360 graus com jogos, filmes e aplicativos. Possui ótima qualidade de imagem eé compatível com a maioria dos smartphones.
>
> **5. Drone**

No quinto produto, ele começou a digitar, mas parou antes de dar uma descrição. Depois vamos entender o motivo disso.

Mas perceba: aqui no *Playground* já podemos "brincar", de fato, com essa ferramenta, para explorar e entender seu funcionamento. Se já usou o chat GPT da OpenAI, deve ter reconhecido esse esquema de perguntas e respostas geradas pelo sistema com base no modelo treinado.

Mas temos um problema. Ele gerou os cinco produtos, mas não queríamos que ele gerasse essas descrições, queríamos só o **nome** do produto. Mas não queremos ter que ficar digitando exatamente o nosso pedido, ajustando as regras toda vez que mandamos uma pergunta.

## Regras de Sistema

Para sanar esse problema, há uma maneira de pré-determinar essas regras. O campo à esquerda, chamado ***System*** , é onde podemos fazer uma configuração de regras para determinar o comportamento das respostas do sistema.

Podemos escrever, por exemplo, que ele vai gerar apenas o nome dos produtos. Então, no *prompt* do usuário, não precisamos repetir as regras toda vez. Para cada pergunta que a pessoa usuária enviar, ele vai seguir as regras descritas no campo de *System* .

Então, vamos descrever o seguinte nesse campo:

> **System:** *Você é um gerador de produtos fictícios para um e-commerce e deve gerar apenas o nome dos produtos solicitados pelo usuário.*

Com isso, descrevemos a regra do sistema. A partir de agora, toda vez que mandarmos uma nova pergunta, ele vai gerar novas respostas seguindo essas regras do sistema.

Vamos voltar para o Chat, na parte central da tela. Temos a resposta anterior do sistema, com os nomes e descrições dos produtos. Se passarmos o cursor por cima da resposta, encontraremos no canto direito um ícone de um símbolo de "menos", onde podemos clicar para **apagar** a resposta.

Agora, vamos alterar o prompt do usuário:

> **User:** *Gere cinco produtos.*

Não vamos especificar para gerar só o nome para verificar se ele vai respeitar as regras que configuramos no sistema. Vamos clicar em *Submit* .

Agora, ele gerou apenas o nome dos produtos e agora não tivemos aquele problema:

> **Assistant:**
>
> 1. Relógio Lunar
> 2. Kit de Maquiagem Estelar
> 3. Cadeira ergonômica Celestial
> 4. Impacto Solar (perfume feminino)
> 5. Tênis Astral

Vamos fazer um novo teste. Podemos apagar a resposta ou, embaixo dela, clicar no botão "***Add Message*** ". para adicionar uma nova mensagem:

> **User:** *Gere mais dez produtos.*

E vamos submeter. Perceba: ele gerou uma nova resposta ainda respeitando as regras do sistema:

> **Assistant:**
>
> 1. Colar Galáctico
> 2. Mochila Cósmica
> 3. Conjunto de Canecas Estelares
> 4. Fones de Ouvido Nebulosos
> 5. Papel de Parede Planetário
> 6. Bracelete Lunar
> 7. Óculos de Sol Astrais
> 8. Camiseta Interplanetária
> 9. Kit de Pincéis Celestiais
> 10. Capa de Celular Espacial

Este é o modo de Chat. Temos o modo de Assistente também, como conferimos anteriormente, que não vai ser explorado neste curso, mas apenas num curso posterior.

Agora, nosso foco vai ser esse modo de chat, o modo mais comum, em que simulamos um chat onde fazemos uma pergunta e o sistema nos devolve uma resposta, gerando-a no modelo do GPT.

Esses dois campos, de *System* e *User* , são os mais importantes para nós. O do *User* **recebe a pergunta** a ser feita; no do *System* , podemos **pré-configurar comportamentos específicos** : o que ele deve fazer, o que ele deve ignorar, como deve ser a saída. Com isso, deixamos a resposta gerada mais próxima do que queremos mais rapidamente.

Lembrando que, além do *System* e do *User* , temos vários outros **parâmetros** na lateral direita da tela, que são configurações alteráveis. Vamos conhecê-los melhor no próximo vídeo!



# 05 **Testando outros parâmetros**


Conhecemos o Playground, utilizamos o recurso de enviar uma mensagem simulando o usuário e também de configurar um prompt do sistema. No entanto, conforme mencionado no vídeo anterior, existem **outros parâmetros** na ferramenta que vamos explorar agora para entender o seu funcionamento.

## Modelo

No Playground, no lado direito da tela, há um menu com vários campos de parâmetros que podemos modificar. O primeiro é chamado de "**Model** ", onde podemos controlar qual será o modelo GPT utilizado.

Ele vem por padrão com a opção GPT 3.5, mas há outros modelos disponíveis — dependendo da sua conta, se estiver no período gratuito, podem aparecer algumas opções e outras não. Podemos usar o GPT-4 ou o GPT-4 modelo *preview* , por exemplo. **No curso, vamos utilizar o GPT-4** . Portanto, a partir de agora, sempre vamos deixar esse modelo selecionado.

## Temperatura

Além do modelo, temos o campo de "**Temperature** ". Este campo está relacionado com o outro abaixo, chamado "**Top P** ". Esses dois campos estão relacionados e, no geral, é recomendado que se altere um ou outro, mas não ambos ao mesmo tempo. Eles servem para controlar os níveis de probabilidade das próximas palavras que são escolhidas para gerar a saída.

> O modelo GPT é baseado na probabilidade das palavras, que na verdade são ***tokens*** . Vamos entender isso melhor posteriormente no curso.

O modelo faz essa geração de respostas baseado em probabilidade. Qual é a palavra mais provável para vir em seguida? E agora, qual é a próxima palavra mais provável? E assim por diante.

Porém, às vezes, queremos que ele não escolha as palavras de maior probabilidade, mas que ele pegue outras opções que têm um pouco menos de probabilidade. Esses parâmetros acabam sendo úteis quando queremos gerar algo mais **criativo** ; por exemplo, um texto para uma chamada de marketing ou um conto de ficção.

No campo de "Temperature", os valores variam de 0 a 2. Por padrão, vem com o valor 1 selecionado. Se selecionarmos o valor máximo, 2, e submetermos uma nova mensagem, como "*gere mais 5 produtos* ", podemos observar que a saída começa a ficar estranha:

> **Assistant:**
>
> 1. Lâmpada Veneza Eduardo premiumUberwolth/_sales inantMMM.ver2hhh219azz tecn-spot [...]

Ele até começou a gerar uma resposta coerente, mas depois perdeu o sentido. Isso acontece porque o valor alto de Temperatura faz com que ele comece a concatenar as próximas palavras com baixo filtro de probabilidade de coerência. Portanto, tome cuidado com esse campo. Você pode aumentar ou diminuir baseado nos seus objetivos e qual o tipo de resposta que você espera.

Uma coisa importante a notar é que **não existe um número mágico** , ou uma única configuração boa desse parâmetro. Isso você terá que testar. Por isso existe essa ferramenta do Playground! A ideia é justamente essa: brincar e fazer testes até a resposta sair mais ou menos próxima do que desejamos. **É uma questão de tentativa e erro.**

## Maximum length

Outro campo importante é o "**Maximum Length** ", ou seja, o tamanho máximo da saída. Por padrão, esse tamanho é configurado como 256. Isso também é relacionado ao número de *tokens* que serão contabilizados. Esta quantidade é o máximo de *tokens* que desejamos gerar como resposta.

Você deve se lembrar que, antes de configurarmos as regras do sistema, pedimos para que ele gerasse 5 produtos e ele gerou uma lista de produtos com suas respectivas descrições. Mas, no quinto produto, ele deixou apenas o nome e não inseriu sua descrição como nos outros. Isso aconteceu porque o valor máximo de *tokens* , de 256, foi atingido.

Você pode estar se perguntando: *será que não é melhor configurar esse valor como o mais alto possível para não ter mensagens e respostas cortadas?* Na teoria, sim. Mas, como mencionado, essa API é paga, e o custo dela é baseado justamente em *tokens* .

Posteriormente, vamos ter uma aula para falar especificamente sobre *tokens* e custos. Por enquanto, sabemos simplesmente que não é uma boa ideia deixar um valor muito alto aqui porque podemos perder o controle dos gastos.

## Stop sequences

Há também o campo "**Stop Sequences** ", que serve para interromper a geração da resposta quando aparece uma determinada sentença.

Agora, nosso Assistant está gerando a lista de nomes dos produtos, sempre colocando o número do item, um ponto e o nome. Podemos colocar no campo em questão o "**6.** ". Ao pedir para ele gerar mais 10 produtos, ele vai parar quando encontrar essa sequência, deixando a lista com apenas mais cinco produtos, sem gerar o sexo, sétimo, oitavo nono e décimo que foram pedidos.

Esse parâmetro é útil para quando queremos controlar uma condição de parada na resposta.

## Frequency penalty e Presence penalty

Os dois últimos campos são para **penalizar** . Eventualmente, quando utilizamos a API, ela pode começar a repetir muitas vezes um determinado *token* na resposta, seja uma palavra ou frase, e não queremos que isso aconteça. Portanto, podemos controlar uma penalização para isso nesses campos.

Em **Frequency penalty** , uma resposta é penalizada pela frequência de ocorrência de um mesmo token. Em **Presence penalty** , uma resposta é penalizada pela presença de um token.

De modo semelhante ao parâmetro de temperatura, apenas mexemos nesses parâmetros quando queremos algo mais criativo e menos prolixo.

Novamente: não existe um valor mágico para inserir nesses campos — precisamos testá-los. No geral, ele já vem com os valores padrão, que estão bem próximos do que geralmente desejamos em uma aplicação tradicional.

Porém, dependendo do seu contexto e projeto, você terá que fazer ajustes até chegar em um padrão que gere respostas próximas do que deseja. Seja algo mais criativo, aumentando esses campos, ou algo mais específico, sem muita variação, diminuindo esses campos.

Agora já conhecemos como funciona esses recursos de Chat Completion da API da OpenAI. Fizemos testes, conhecemos o recurso do usuário, do sistema e os parâmetros, e entendemos bem como tudo isso funciona.

Porém, o nosso objetivo não é ficar brincando no Playground. Nosso objetivo é criar uma aplicação utilizando a linguagem Java, que se integra com essa API. E todas essas configurações, queremos fazer via código Java.

Então, na próxima aula, vamos começar a escrever código Java para aprender a integrar nossa aplicação com essa API via código.



# 06 **Para saber mais: parâmetros do GPT**

Como vimos durante a aula, os parâmetros controlam o comportamento e a saída do modelo de linguagem gerado no playground da plataforma da OpenAI. Entender para que servem os parâmetros é essencial para atender às necessidades de seu projeto com qualidade e comportamento desejado.

Os principais parâmetros têm a seguinte funcionalidade:

* **Mode (modo):** define como você deseja que o modelo se comporte, e cada um dos modos tem seu próprio contexto e aplicação específicos. Atualmente, temos os modos:
  * `assistants`: usado para criar assistentes integrados com aplicações;
  * `chat`: usado para criar interações de conversa com o modelo;
  * `complete (legado)`: uma forma de solicitar ao modelo que complete um texto ou código fornecido;
  * `edit (legado)`: projetado para auxiliar na edição e revisão de textos.
* **Model (modelo):** refere-se à arquitetura específica do modelo de linguagem que você deseja usar. No playground da OpenAI, você pode escolher entre vários modelos, cada um com diferentes capacidades de processamento de instruções e tamanhos de tokens. Todos os modelos disponíveis e suas especificações estão descritos na [documentação da OpenAI](https://platform.openai.com/docs/models/models).
* **Temperature (temperatura):** controla a aleatoriedade da saída gerada pelo modelo. Valores mais altos de temperatura (por exemplo, 0,8) produzem saídas mais criativas e imprevisíveis, enquanto valores mais baixos (por exemplo, 0,2) geram saídas mais determinísticas e seguras.
* **Maximum length (comprimento máximo):** limita o tamanho da resposta gerada pelo modelo. Você pode definir um número máximo de tokens (unidades de texto) que a resposta deve conter. Isso é útil para evitar que a saída seja muito longa e se ajustar às restrições do contexto em que o modelo está sendo usado.
* **Stop sequences (sequências de parada):** são tokens que indicam ao modelo que ele deve parar de gerar texto. Isso é útil para controlar quando e onde a saída deve terminar.
* **Top P:** controla a proporção cumulativa das probabilidades dos tokens a serem considerados durante a geração de texto. Isso permite que você controle a diversidade da saída, garantindo que o modelo escolha entre uma seleção mais restrita de tokens com probabilidades mais altas.
* **Frequency penalty (penalidade de frequência):** controla a frequência com que o modelo repete palavras ou frases semelhantes. Valores mais altos desencorajam o modelo a repetir as mesmas palavras ou estruturas, tornando a saída mais diversificada.
* **Presence penalty (penalidade de presença):** influencia a diversidade da saída, mas de maneira diferente do frequency penalty. Valores mais altos incentivam o modelo a explorar mais possibilidades e produzir respostas menos óbvias e mais criativas.

Lembre-se de que a combinação desses parâmetros pode afetar significativamente o resultado gerado pelo modelo. Tente sempre experimentar diferentes configurações para atingir o tipo de saída desejada em suas interações com o modelo de linguagem.



# 07**Para saber mais: Tiers de conta**

A OpenAI oferece diferentes níveis de contas para seus usuários, conhecidos como "tiers" ou categorias de conta. Cada tier possui recursos e benefícios específicos, permitindo aos usuários escolher o plano mais adequado às suas necessidades.

O primeiro tier é o **Free Trial** (avaliação gratuita), que é uma conta gratuita disponível para os usuários experimentarem a plataforma da OpenAI. Nesse nível, os usuários têm acesso limitado aos recursos da API e podem fazer um número restrito de chamadas à API por mês.

O segundo tier é o **Pay-as-you-go** (Pague conforme o uso), que é um nível de conta em que o usuário paga pelos recursos utilizados. Essa opção é mais flexível e não possui restrições de uso mensal. Os usuários pagam de acordo com o consumo da API, podendo aumentar ou diminuir suas necessidades de uso conforme desejado.

A OpenAI também oferece tiers específicos para empresas e desenvolvedores por meio do **Team** e **Business** tiers. Esses tiers oferecem suporte aprimorado, recursos adicionais e personalização de contratos para atender às necessidades.

Para mais detalhes, acesse a [página da documentação](https://platform.openai.com/docs/guides/rate-limits/usage-tiers).


# 08**Melhorando as respostas**

Vimos que no playground da OpenAI existem diversos parâmetros que podemos ajustar para alterar a maneira que a API gera as respostas.

Escolha todas as alternativas com afirmações verdadeiras em relação a esses parâmetros.

* Alternativa correta
  [ ]Os parâmetros já apresentam valores default preenchidos que não deveriam ser modificados.
* Alternativa correta
  [ ]Alterar o parâmetro `Frequency penalty` pode ajudar a evitar repetições na resposta.

Esse parâmetro ajusta a penalidade para a repetição de tokens já utilizados na resposta. Valores mais altos desencorajam a repetição, ajudando a gerar respostas mais diversificadas e menos redundantes.

* Alternativa correta
  [ ]Para a API gerar respostas mais satisfatórias devemos alterar os valores dos parâmetros para o valor máximo possível.
* Alternativa correta
  [ ]Ajustar o parâmetro `Temperature` afeta a criatividade das respostas geradas pela API.

A temperatura é um parâmetro que pode tornar as respostas mais conservadoras ou mais inovadoras, dependendo se o valor é diminuído ou aumentado, respectivamente. Um valor mais alto promove maior variabilidade, enquanto um valor mais baixo tende a produzir respostas mais previsíveis e seguras.


# 09 **Faça como eu fiz: criando sua conta e explorando Playground**

[ Próxima Atividade](https://cursos.alura.com.br/course/gpt-java-integre-aplicacao-openai/task/147444/next)

Nesta aula, vimos como criar e configurar uma conta no site da OpenAI, além de aprender a utilizar o Playground como ferramenta de testes da API.

E aí? Já colocou a mão na massa? Chegou a hora de você executar o que foi feito nos vídeos.


# **O que aprendemos?**

Nesta aula, você aprendeu como:

* Criar uma conta no site da OpenAI;
* Realizar configurações de meios de pagamento;
* Ajustar limites financeiros de utilização da API;
* Utilizar o modo chat, via playground, para simular interações com a API da OpenAI.
