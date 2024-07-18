# Rede - ponto a ponto

Bitcoin é uma rede distribuída ponto a ponto.

Nesta fase do LARP, construiremos uma rede ponto a ponto real e começaremos a trocar mensagens de pares.

Tempo estimado: 30 minutos+

## Índice

  * [Materiais Usados](#materiais-usados)
  * [Conectando-se](#conectando-se)
  * [Objetivos Desta Fase](#objetivos-desta-fase)
  * [Enviando Mensagens de Rede](#enviando-mensagens-de-rede)
  * [Recebendo Mensagens de Rede](#recebendo-mensagens-de-rede)
    * [Passos para Validar uma Transação](#passos-para-validar-uma-transação)
  * [Deixando a Rede Funcionar](#deixando-a-rede-funcionar)
    * [Erros Comuns e Problemas](#erros-comuns-e-problemas)
  * [Verificando o Estado Global da Mempool](#verificando-o-estado-global-da-mempool)
    * [Quem Tem Mais Transações?](#quem-tem-mais-transações)
    * [A Transação de Quem Está em Mais Mempools?](#A-Transação-de-Quem-Está-em-Mais-Mempools)
  * [Em Resumo](#em-resumo)

## Materiais Usados

Nesta fase do LARP, usaremos os seguintes itens:

  - corda
  - tesouras
  - cartões de rede
  - argolas de fichário
  - marcador de apagar a seco
  - suprimentos para copiar transações
    - canetas esferográficas
    - cartões de transação em branco
    - adesivos de cadeado
    - adesivos de chave

## Conectando-se

Antes de começar esta fase, encontre a corda e as tesouras.

Roteiro do Instrutor:

  ```
  Até agora, estamos fazendo transações para nossos próprios nós locais.
  Mas o Bitcoin é uma rede ponto a ponto. Isso significa que quaisquer
  transações ou blocos estão no nosso nó, bem como em outros
  nós.

  Você notará que agora a mempool de todos só tem
  uma transação que eles mesmos escreveram. Isso não é muito
  útil para ninguém - precisamos que outros nós possam minerar
  e incluir sua transação.

  Para fazer isso, precisamos conectar todos os nós.
  A maneira como o bitcoin faz isso é falar com uma lista pré-definida
  de nós conhecidos, que então lhes dizem com quem mais se conectar.

  Neste exemplo, vou simplesmente conectar todos vocês.

  AÇÃO: Usando a corda e as tesouras, crie conexões
  entre todas as mesas dos nós. Idealmente, cada nó
  terá duas cordas que chegam à sua mesa,
  no máximo, qualquer nó terá três.
  ```

## Objetivos Desta Fase

Às vezes é útil para os jogadores terem objetivos de curto prazo, caso contrário, todas as ações que estão realizando começam a perder o foco.

Nesta fase, tornamos o envio + recebimento de transações e a adição delas à sua mempool orientada por objetivos.

Roteiro do Instrutor:

  ```
  Temos transações na nossa mempool. Precisamos colocar
  a transação na nossa mempool na mempool de
  todos os outros nós na rede.

  No final desta fase, cada nó deve ter
  7* transações na sua mempool.

  NOTA: o número de transações em cada mempool
  será igual ao número de nós jogando mais
  um, pela Primeira Transação de Rede.

  Existem duas maneiras de 'vencer' esta rodada do
  LARP. Você pode ser o nó que tem sua
  transação na mempool do maior número de outros nós.

  Ou você pode ter todas as transações na sua mempool.

  Todos entendem o objetivo?

  Vamos começar a enviar mensagens de rede.
  ```

## Enviando Mensagens de Rede

Vamos enviar algumas mensagens!

Roteiro do Instrutor:

  ```
  Cada nó tem quatro mensagens de rede. São elas:
  - Eu Tenho Transações
  - Enviar Transações
  - Eu Tenho Blocos
  - Enviar Blocos

  Para mover transações, usaremos apenas as mensagens de Transação.

  As mensagens de rede funcionam da seguinte forma.

  Assim que uma nova transação chegar à sua mempool,
  você deve enviar uma nova mensagem de Eu Tenho Transações
  para todos os nós aos quais está conectado, informando-os
  sobre *todas* as transações na sua mempool.

  Vamos fazer isso para este primeiro nó.

  AÇÃO: Escolha um nó aleatoriamente e ande perto da mesa dele.
  Pegue ambas as transações da mempool: a
  Primeira Transação de Rede e a transação que o nó
  fez para si mesmo.

  Este nó tem duas transações na sua mempool.

  AÇÃO: Leia os dois txids das transações.

  Eles precisam informar seus pares sobre as transações
  na sua mempool.

  AÇÃO: Pegue um cartão de Eu Tenho Transações e escreva os
  txids das duas transações no cartão, usando o
  marcador de apagar a seco. Levante-o para que todos possam ver.

  Ok, agora preciso enviar meu cartão de Eu Tenho Transações para
  todos os meus pares.

  AÇÃO: Pegue uma argola de fichário, prenda o cartão de rede
  nela. Coloque a argola em qualquer corda
  que o nó escolhido tenha a ponta, e
  envie-a pela corda para o nó que está segurando a
  outra ponta da corda.
  ```

## Recebendo Mensagens de Rede

Receber uma mensagem de rede muitas vezes exige que um nó faça algum trabalho.

Roteiro do Instrutor:

  ```
  AÇÃO: Vá até o outro nó que recebeu
  a mensagem. Um dos jogadores desta mesa deve
  agora estar segurando a mensagem.

  Depois de receber uma mensagem de rede, você deve
  verificar se já conhece as transações
  listadas.

  Há alguma transação na lista na mensagem
  de rede que você não conhece?

  R: Sim, o <txid da transação que o primeiro par fez>.

  NOTA: Eles já devem ter 'cat72' na mempool.

  Ok. Devemos pedir a este par para nos enviar esta transação.
  Fazemos isso enviando de volta uma mensagem de rede.
  Desta vez, você enviará a mensagem Enviar Transações.

  AÇÃO: Ajude o par receptor a colocar o txid da
  transação que estão faltando no cartão de Enviar Transação
  e envie-o de volta pela mesma corda para o par que
  acabou de receber a mensagem de Eu Tenho Transação.

  AÇÃO: Espere o par receber a mensagem e
  pegá-la da corda.

  Quando você recebe uma mensagem de Enviar Transação, se você
  tiver essa transação, deve fazer uma cópia dela
  e enviá-la pela corda para o nó que
  a solicitou.

  AÇÃO: Faça com que o nó faça uma cópia da transação
  da sua mempool e a envie pela corda
  de volta para o outro nó.
  ```

## Recebendo uma Transação da Rede

Na fase anterior, aprendemos a validar transações que recebemos da rede. Precisaremos repetir esses passos para cada transação que recebermos.

### Passos para Validar uma Transação

- Ela tem um txid válido? palavra + número de dois dígitos
- Para cada entrada:
  - Você consegue encontrar a saída correspondente na
    mempool ou no conjunto UTXO?
  - A assinatura corresponde ao cadeado?
- Para as saídas:
  - Cada saída está bloqueada com um cadeado colorido?
  - O valor total das saídas é menor
    que o valor total das entradas?
- Escreva o valor total das taxas no verso da transação
- Se a transação passar em todas as verificações, marque-a
  como Aprovada e coloque-a na mempool
- Se a transação NÃO passar em todas as verificações, rasgue-a
  e descarte-a

Roteiro do Instrutor:

  ```
  AÇÃO: Volte para o nó que recebeu a
  transação. Faça-os passar pelo processo de validação
  novamente. Como lembrete, veja acima o que o
  processo deve ser.

  Observe que, uma vez que você validar uma nova transação e
  colocá-la na sua mempool, deve notificar todos os seus
  pares sobre o estado atual da sua mempool.

  Isso significa enviar uma nova mensagem de Eu Tenho Transação
  para cada par, com uma lista de todas as transações
  na sua mempool.
  ```

## Deixando a Rede Funcionar

É hora de deixar os outros nós começarem a repetir o processo, fazendo a rede ganhar vida com mensagens e cada um dos nós se ocupando com o trabalho de enviar e responder mensagens.

Todos viram um ciclo inteiro de contar sobre transações, solicitar transações, copiar uma transação, e enviá-la para seu par. Agora é a vez deles.

Roteiro do Instrutor:

  ```
  AÇÃO: Instrua os nós a começar a enviar mensagens de Eu Tenho
  Transação e responder a solicitações de pares.

  AÇÃO: Dê aos nós de 5 a 8 minutos para trabalhar no envio e recebimento de transações.
  Ande por aí e ajude os nós que estão tendo problemas.

  AÇÃO: Após 5 a 8 minutos, pause o jogo para que cada nó possa
  descobrir quantas transações eles têm.
  ```

### Erros Comuns e Problemas

Esta é a primeira fase em que as coisas podem começar a se desintegrar. Redes descentralizadas são um pouco confusas. Aproveite esta oportunidade para andar por aí e garantir que os nós não estão cometendo alguns erros comuns ou problemas que acontecem, que estão listados aqui.

#### O que observar

- Uma conexão cai.
  Tudo bem, pegue-a de volta. Às vezes é
  divertido comentar "oh, parece que você perdeu a conexão".
- Nós esquecem qual conexão de entrada enviou uma mensagem.
  Incentive os nós a criar uma maneira de lembrar qual conexão
  enviou qual mensagem. Computadores têm esse mesmo problema. Uma maneira comum
  que eles resolvem isso é dar a cada conexão um número e então
  rotular as mensagens de entrada com esse número.
- Nós não fazem uma transação, mas enviam a original
  Faça-os enviar uma mensagem de Enviar Transação para o par para obter
  uma cópia da transação de volta. Depois de recebê-la,
  eles devem validá-la novamente antes de colocá-la na sua
  mempool.
- Um nó recebe uma transação já carimbada como Aprovada.
  Eles devem verificar novamente se a transação está correta.
- Um nó recebe uma transação inválida (muito dinheiro nas saídas, faltando
  cadeado ou chaves)
  Tecnicamente, eles deveriam rasgar a transação E interromper a conexão
  com o nó que enviou os dados incorretos. Cabe ao nó decidir
  quão tolerante ele quer ser em relação a punir erros. Notavelmente no
  protocolo bitcoin, não enviamos mensagens de erro de volta. Apenas paramos
  de falar com esse par.
- As transações não estão chegando a toda a rede.
  Os nós muitas vezes esquecem que precisam enviar outra rodada de mensagens de Eu Tenho
  Transação após *cada* nova transação que é adicionada
  à mempool. Pode ser útil lembrar os nós de fazer isso.

## Verificando o Estado Global da Mempool

Vamos obter uma visão do que a rede parece. É realmente difícil fazer isso na rede bitcoin, mas podemos fazer isso facilmente com um grupo de pessoas.

### Quem Tem Mais Transações?

Nota: Veja a seção em [Configuração](docs/01-setup#rewards-for-nodes) sobre o que usar como Recompensa.

Roteiro do Instrutor:

  ```
  Ok, vamos ver quem tem mais transações na sua mempool.

  AÇÃO: Aponte para cada nó um por um. Faça-os contar e
  dizer o número de transações na sua mempool.

  AÇÃO: Recompense o nó com mais transações na sua
  mempool com uma Recompensa. Idealmente, cada nó terá o mesmo
  número de transações, então todos devem ser recompensados.
  ```

### A Transação de Quem Está em Mais Mempools?

Roteiro do Instrutor:

  ```
  AÇÃO: Faça com que cada nó, por sua vez, diga qual é o txid da
  transação que escreveu. Faça com que os outros nós
  levantem a mão se tiverem essa transação na sua
  mempool.

  AÇÃO: Mantenha o controle de quantos nós levantam a mão para
  cada transação. Depois que todos os nós disseram seus IDs de transação,
  recompense o nó (ou nós) que têm sua transação
  na maioria das mempools com uma Recompensa. Idealmente, cada transação
  estará na mempool de cada nó, então todos os nós devem empatar.
  Isso raramente acontece.
  ```

## Em Resumo

Agora temos algumas mempools cheias e experimentamos como é enviar e receber mensagens de rede. Estamos prontos para seguir em frente para construir templates de bloco.

Nesta parte do LARP, nós:

- Conectamos-nos a uma rede ponto a ponto
- Enviamos e recebemos nossas primeiras mensagens de rede
- Praticamos a verificação de transações de rede
- Preenchemos nossas mempools com transações para serem mineradas
