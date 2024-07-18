# Construção de Blocos - criando templates de blocos

Estamos nos aproximando de uma versão final funcional da rede bitcoin. Temos transações. Vamos lidar com a última peça do quebra-cabeça: blocos.

Tempo Estimado: 10 minutos

## Índice

  * [Materiais Usados](#materiais-usados)
  * [Construindo Seu Primeiro Template de Bloco](#construindo-seu-primeiro-template-de-bloco)
  * [Escolhendo Transações para um Bloco](#escolhendo-transações-para-um-bloco)
  * [Escrevendo uma Transação Coinbase](#escrevendo-uma-transação-coinbase)
  * [Preenchendo o Cabeçalho do Bloco](#preenchendo-o-cabeçalho-do-bloco)
  * [Calculando o 'compromisso de tx'](#calculando-o-compromisso-de-tx)
  * [Pronto para Minerar o Nonce](#pronto-para-minerar-o-nonce)
  * [Em Resumo](#em-resumo)

## Materiais Usados

Nesta fase do LARP, usaremos os seguintes itens:

  - envelopes de template de bloco
  - cartões de cabeçalho de bloco em branco
  - um cartão de transação em branco
  - canetas esferográficas

## Construindo Seu Primeiro Template de Bloco

Roteiro do Instrutor:

  ```
  Agora que temos transações, vamos construir nosso
  primeiro template de bloco.

  AÇÃO: Levante um envelope de template de bloco vazio,
  para que os participantes saibam do que você está falando.

  Primeiro, precisaremos preencher o bloco com transações.
  Há espaço limitado em cada bloco, então teremos que
  tomar algumas decisões sobre o que incluir.

  Em seguida, queremos fazer uma transação coinbase
  que pagará qualquer taxa de minerador das transações
  que escolhemos mais a recompensa do bloco para nossa própria chave pública.

  Finalmente, queremos preencher o cabeçalho do bloco.
  ```

## Escolhendo Transações para um Bloco

Roteiro do Instrutor:

  ```
  Para nosso LARP, cada bloco pode conter um total de *quatro*
  transações. Isso significa que podemos escolher *três* transações de rede
  da nossa mempool para incluir em um bloco.

  Quem construir o bloco decidirá quais
  transações devem ser incluídas.

  Vamos escolher três transações para colocar no nosso template de bloco agora.

  Uma coisa a prestar atenção é quanto cada transação
  está pagando em taxas. Você pode ficar com essas taxas para você
  se seu bloco for minerado.

  Outra coisa a prestar atenção são as entradas de uma transação.
  Se você incluir uma transação em um bloco, mas não incluir a
  transação que suas entradas nomeiam, então seu bloco não será válido.

  AÇÃO: Permita que os nós tenham alguns minutos para encontrar três transações
  e colocá-las no seu template de bloco. Ande por aí e ajude
  os nós a verificarem quanto estão ganhando em taxas e
  que não estão esquecendo de incluir uma transação.
  ```

## Escrevendo uma Transação Coinbase

Roteiro do Instrutor:

  ```
  Agora que identificamos as transações que vão para
  nosso bloco, estamos prontos para fazer nossa transação coinbase.

  Você deve se lembrar da Transação Gênese como isso
  funciona.

  Encontre um cartão de transação em branco e desenhe um grande X sobre
  a seção de entradas. Transações coinbase não têm entradas.

  Além disso, adicione um novo ID de transação a esta nova transação.

  AÇÃO: Pegue um cartão de transação em branco do nó mais próximo
  e desenhe um grande X sobre a seção de entradas. Escreva
  um novo ID de transação nele. Levante sua transação coinbase
  para que os nós possam ver o que você fez. Se você tiver assistentes,
  peça-lhes que ajudem os outros nós a fazer isso.

  Agora só precisamos descobrir quanto podemos enviar para nós mesmos
  na coinbase. Encontre o cadeado que corresponde à sua
  chave secreta do nó e coloque-o na primeira saída.

  AÇÃO: Coloque seu próprio cadeado preto na saída e levante-o
  para que os nós possam ver + copiar o que você fez.

  Cada bloco vale 50 novos bitcoins. Então, no mínimo, teremos
  50 novos bitcoins nesta saída.

  Se as transações que você está incluindo pagaram alguma taxa ao
  minerador, você deve adicionar esse número a 50 para obter o valor total.

  Por exemplo, se você tiver 3 transações no bloco e cada uma
  pagar 1 bitcoin em taxas, o valor total que posso reivindicar na
  saída da coinbase é 53 bitcoins.

  AÇÃO: Escreva 53 bitcoins na transação coinbase de exemplo
  que você está segurando e levante-a para que os nós vejam.

  Ok, todos tirem alguns minutos para terminar de preencher sua coinbase.

  AÇÃO: Ande por aí e ajude cada nó a preencher a transação coinbase.
  ```

## Preenchendo o Cabeçalho do Bloco

Um cabeçalho de bloco completo é o que torna um bloco válido! Nesta fase, teremos tudo, exceto uma peça faltando: o nonce que bloqueará os outros dados no cabeçalho do bloco e transformará nosso 'template de bloco' em um 'bloco' válido e vencedor.

Roteiro do Instrutor:

  ```
  Agora que temos um bloco completo, estamos prontos para preencher
  o cabeçalho do bloco. Este é o último passo para construir um bloco.

  AÇÃO: Levante um cartão de Cabeçalho de Bloco para que os nós saibam no que estamos
  trabalhando. Dê-lhes um momento para encontrar um para si.

  O primeiro campo no cabeçalho do bloco é o hash da transação anterior.
  Isso cria uma cadeia de um bloco para o próximo e permite que
  qualquer pessoa que receba este bloco saiba em qual cadeia estamos construindo.

  Estaremos construindo o primeiro bloco na nossa blockchain a partir do
  Bloco Gênese. Vamos ver qual foi o hash do bloco para aquele bloco.

  AÇÃO: Tire um Bloco Gênese, no qual você deve ter escrito
  o hash do bloco que você calculou na primeira fase. Leia-o
  para que todos possam escrevê-lo no cabeçalho do bloco.

  O compromisso de tx teremos que calcular. Vamos voltar a isso.

  A hora atual é <leia a hora no telefone/relógio>. Vamos colocar isso
  como a hora.

  O alvo de dificuldade atual é o mesmo do Bloco Gênese,
  ou 8500*. Vamos escrever 8500 no campo de alvo.

  O último campo é um campo de nonce. Encontrar um valor válido para este campo
  é difícil. Usaremos nossos BASICS em breve para tentar calculá-lo
  para nós.
  ```

## Calculando o compromisso de tx

Roteiro do Instrutor:

  ```
  Para descobrir o campo de compromisso de tx, precisaremos de uma
  calculadora e das transações que você está incluindo no bloco.
  Você pode querer usar a calculadora no seu telefone.

  O compromisso de tx faz com que um nó malicioso não possa pegar um
  bloco válido e trocar por novas transações. Ele compromete-se com as transações
  que escolhemos para este bloco. É por isso que chamamos de compromisso de tx.

  Nosso compromisso de tx é a soma de todos os números nos txids das
  transações dentro dos nossos blocos.

  AÇÃO: Leia os IDs de transação dentro do template de bloco de um nó.
  Faça-os usar sua calculadora para somar esses números. Diga à turma qual
  é o compromisso de tx e faça com que a equipe do nó coloque esse número no seu
  compromisso de tx.

  AÇÃO: Faça com que todos os nós calculem e preencham o compromisso de tx no
  cabeçalho do bloco. Alguns nós podem ter o mesmo compromisso de tx, mas
  todos devem ser diferentes, dependendo do que os nós escolheram para seu
  txid da coinbase.
  ```

_Nota de Protocolo_: Participantes e facilitadores atentos podem perceber que é muito fácil criar uma nova transação que reutiliza o mesmo número do ID de transação da transação que você deseja substituir em um bloco. No protocolo bitcoin, eles usam algo chamado Raiz de Merkle, que é praticamente impossível trocar uma transação e obter a mesma raiz.

Não podemos calcular uma Raiz de Merkle para o LARP, pois é um pouco complexo demais. Em vez disso, usamos uma matemática muito mais simples.

## Pronto para Minerar o Nonce

Neste ponto, cada nó deve ter um cabeçalho de bloco quase completo. Eles só estarão faltando o campo nonce.

Este é o campo que precisaremos de nossos BASICS. Estamos prontos para a fase de mineração do LARP!

## Em Resumo

Nesta parte do LARP, nós:

- Escolhemos transações da mempool
- Calculamos o valor da saída da coinbase
- Escrevemos nossa própria transação coinbase
- Preenchemos quase todos os campos do cabeçalho do bloco
- Aprendemos como fazer um compromisso de transação

Agora estamos prontos para começar a minerar blocos.
