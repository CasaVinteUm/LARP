# Transações: Validando + Escrevendo

Agora tivemos uma introdução rápida a blocos e transações.

Vamos desacelerar um pouco e passar algum tempo validando e escrevendo nossa própria transação do zero.

Tempo estimado: 15 minutos

## Índice

  * [Materiais Usados](#materiais-usados)
  * [Transações da Rede](#transações-da-rede)
    * [Entradas](#entradas)
    * [Saídas](#saídas)
    * [TXIDs](#txids)
    * [Transações Válidas](#transações-válidas)
  * [A Mempool](#a-mempool)
  * [Verificação de Saldo da Carteira](#verificação-de-saldo-da-carteira)
  * [Escrevendo Transações](#escrevendo-transações)
    * [Saídas de Troco](#saídas-de-troco)
    * [Taxas de Transação](#taxas-de-transação)
  * [Adicionando Transações à Mempool](#adicionando-transações-à-mempool)
  * [Em Resumo](#em-resumo)

## Materiais Usados

Nesta fase do LARP, usaremos os seguintes itens:

  - a primeira transação de rede;
  - cartões de transação em branco;
  - o carimbo de aprovado;
  - adesivos de chave;
  - adesivos de cadeado;
  - canetas esferográficas;
  - o cesto de mempool;
  - lista de verificação de validação de transação;

## Transações da Rede

Roteiro do Instrutor:

  ```
  Agora que passamos por tudo no nosso download do nó do bitcoin core,
  estamos prontos para começar a receber tráfego de rede. Digamos que todos os nossos nós
  estão prontos e online e receberam sua primeira transação de um 'nó fantasma'
  (eu, o facilitador).

  AÇÃO: Ande por todos os nós e entregue-lhes a
  primeira transação da rede

  Quando você recebe dados da rede, precisa verificá-los.
  Isso porque você não sabe o que lhe foi enviado.

  Não confie, verifique.

  Há alguns passos para verificar uma tx. Vamos passar por eles juntos.
  ```

### Entradas

Uma entrada de bitcoin aponta para uma saída de bitcoin. Aqui aprenderemos como encontrar saídas que uma entrada está gastando.

Aqui encontramos nosso segundo [erro intencional](#erros-propositais): a primeira transação de rede está sem sua assinatura.

Os nós devem usar o cartão de lista de verificação de validação de transação para acompanhar, marcando itens com seu marcador de apagar a seco.

Roteiro do Instrutor:

  ```
  Para uma transação de bitcoin, precisamos saber quanto bitcoin
  temos disponível para gastar em suas saídas. Para fazer isso,
  olhamos para as 'entradas' de uma transação.

  Como sabemos quanto vale uma entrada de bitcoin?

  R: ... (deixe os nós adivinharem)

  Está escrito no campo de entrada da transação?

  R: Não, não está.

  Ok, onde podemos ir para descobrir quanto vale uma entrada?

  R: a saída para a qual ela 'aponta'.

  Podemos encontrar a saída que esta entrada está gastando usando
  o ID da transação e o número da saída listados na entrada.

  Para esta primeira transação de rede, diz que estamos gastando
  da transação 'eagle33' e saída número zero.

  Onde podemos ver quanto vale a saída zero da transação 'eagle33'?

  R: Encontre a saída no conjunto UTXO.

  Quanto vale a saída zero da eagle33?

  R: 25 bitcoin

  Ok, então temos 25 bitcoin para gastar nas saídas desta transação.

  Há mais uma coisa a verificar antes de passarmos para as saídas:
  a assinatura desta transação é válida?

  Parece que cometi um erro nesta transação: deixei a assinatura
  de fora. Normalmente, quando recebemos transações com erros ou problemas da
  rede, simplesmente as descartamos. Mas para esta, vamos fazer uma
  exceção e assinar esta entrada. Usaremos os adesivos de chave
  para representar uma assinatura, já que está desbloqueando o cadeado
  que colocamos na saída que estamos gastando.

  Qual adesivo de chave colorida devo usar para a assinatura desta entrada?

  R: a chave verde

  AÇÃO: Faça com que os nós coloquem o adesivo de chave verde no campo de assinatura para
  a primeira entrada na transação 'cat72'.
  ```

### Saídas

Roteiro do Instrutor:

  ```
  Temos 25 bitcoin para gastar nas saídas desta transação.
  Quantos bitcoin estamos travando nas saídas desta transação?

  R: 24

  Tínhamos 25 para travando, e estamos travando 24. Para onde vai aquele 1 bitcoin extra?

  R: Está disponível para o minerador como taxas.

  Vamos escrever esse valor da taxa no verso da transação. Será útil
  mais tarde quando começarmos a construir nossos próprios blocos.
  ```

### TXIDs

Roteiro do Instrutor:

  ```
  A última coisa a verificar em uma transação é se ela tem um
  ID de transação válido. Para este jogo, o ID da transação, ou txid, deve ser uma
  palavra mais um número de dois dígitos.

  O txid nesta transação está ok?
  ```

_Nota de Protocolo_: IDs de transação são calculados a partir dos dados da transação em si e identificam exclusivamente essa transação. Isso é feito usando um hash SHA256 do conteúdo da transação. Não temos uma maneira fácil de hash dos dados da transação, então simplesmente escolhemos um aleatório. Se os alunos escolherem o mesmo txid, você terá problemas. Isso pode ser bom ou não, dependendo. Geralmente deixo o caos + problemas ocorrerem por um tempo, para que os participantes possam experimentar as desvantagens de certas escolhas de protocolo (como permitir que haja txids duplicados).

Houve dois casos de IDs de transação duplicados no protocolo. Isso acontece quando as transações de coinbase são idênticas. O protocolo foi alterado para que isso não seja mais possível. Veja [BIP30](https://github.com/bitcoin/bips/blob/master/bip-0030.mediawiki) para mais detalhes.

### Transações Válidas

Roteiro do Instrutor:

  ```
  Se esta transação é válida, devemos marcá-la como tal. Vamos fazer
  isso.

  AÇÃO: Pegue o carimbo auto-tintante Aprovado e marque esta transação de rede
  como Aprovada.
  ```

## A Mempool

Roteiro do Instrutor:

  ```
  Agora que a transação está marcada como Aprovada, e somente depois que
  uma transação é marcada como aprovada, estamos prontos para colocá-la na
  Mempool.

  A mempool é um local de espera para transações que estão esperando
  para entrar em um bloco. É o conjunto de transações que são válidas
  mas não confirmadas.

  Mempools têm um tamanho estrito, se você receber muitas transações
  pode começar a descartar algumas delas.

  Quando um bloco é minerado, as transações são promovidas da
  mempool para o conjunto UTXO. Isso abre espaço para novas transações
  na mempool (se ela estava cheia).

  AÇÃO: Coloque a primeira transação de rede na mempool.
  ```

## Verificação de Saldo da Carteira

Roteiro do Instrutor:

  ```
  Agora temos uma transação confirmada no conjunto UTXO e uma
  transação esperando para ser confirmada na mempool.

  Olhando para ambas as transações confirmadas e não confirmadas,
  levante a mão se você tem bitcoin bloqueado na sua
  chave secreta.

  NOTA: Todos os nós devem levantar a mão neste ponto.

  Ótimo. Estamos prontos para escrever nossa primeira transação.
  ```

## Escrevendo Transações

Cada nó escreverá uma única transação para todo o seu grupo. Como uma nota de jogo, neste ponto os membros dos nós devem começar a assumir diferentes papéis ao realizar tarefas, etc. É útil para o funcionamento bem-sucedido do nó que isso aconteça (todos fazem trabalhos diferentes para ajudar o nó a funcionar).

Roteiro do Instrutor:

  ```
  Agora que validamos nossa primeira transação, estamos prontos
  para escrever uma nova.

  Precisaremos de um cartão de transação em branco para isso. Também
  precisaremos ter uma saída que possamos gastar com nossa chave
  privada.

  AÇÃO: Pegue um cartão de transação em branco e levante-o,
  também pegue a transação gênese do conjunto UTXO
  e levante-a para que todos possam ver.

  Vamos escrever nossa primeira transação.

  Primeiro, precisaremos de um txid. Escolha um txid aleatório para esta transação.

  AÇÃO: Nós escrevemos um txid.

  Depois de escolher um txid, você precisará preencher as informações
  para a saída que está gastando. É permitido gastar saídas não confirmadas
  (de transações na mempool).

  AÇÃO: Nós adicionam o txid e o número da saída da saída que estão gastando.
  Ande por aí e certifique-se de que estão fazendo a coisa certa.

  Finalmente, você precisará criar algumas saídas. Para esta transação,
  todos vocês estão me pagando um bitcoin, como pagamento por este LARP.

  Para me enviar bitcoin, você precisará saber meu endereço de bitcoin.

  AÇÃO: Ande por aí e entregue a cada nó um adesivo de cadeado preto.
  (Sua chave privada é o adesivo de chave preto.)

  AÇÃO: Nós devem adicionar uma saída com valor 1 e
  com o adesivo de cadeado preto como chave pública.
  ```

### Saídas de Troco

No bitcoin, se há bitcoin sobrando após você enviar dinheiro para o cadeado desejado, você precisa criar uma saída de troco.

Às vezes é divertido se os nós esquecerem de adicionar uma saída de troco, pois eles descobrem muito rapidamente que esse dinheiro acaba indo para o minerador.

Se você quiser causar um pouco de caos, pode omitir esta seção nas suas instruções.

Roteiro do Instrutor:

  ```
  Quantos bitcoins estávamos gastando originalmente?

  R: 8 bitcoin

  E agora você está me enviando 1 bitcoin. Para onde vão os
  bitcoins restantes?

  R: Para o minerador, atualmente.

  Se quisermos não enviar todos esses 7 bitcoins para o minerador,
  como devemos evitar isso?

  R: criando outra saída

  Para onde devemos enviar o bitcoin nessa outra saída?

  R: Para qualquer lugar que você quiser! Mas, provavelmente, de volta para sua própria carteira.

  Observe que para o LARP, usaremos apenas números inteiros,
  sem decimais.

  AÇÃO: Nós adicionam uma saída de troco à sua transação e a bloqueiam
  no adesivo de cadeado que corresponde ao seu cartão de chave secreta.
  ```

### Taxas de Transação

Às vezes também é divertido se os nós esquecerem de incluir uma taxa para o minerador, mas apenas se alguns dos nós se lembrarem. Isso torna mais fácil para os nós que estão construindo blocos tomar decisões sobre quais transações incluir em seu bloco (dica: geralmente as de taxa baixa).

Eu não forçaria essa situação a ocorrer, mas é interessante quando acontece naturalmente.

Roteiro do Instrutor:

  ```
  Lembre-se de que você provavelmente vai querer deixar algum bitcoin
  para o minerador, caso contrário, ele pode não incluir sua transação em um bloco.
  ```

## Adicionando Transações à Mempool

Roteiro do Instrutor:

  ```
  Agora que escrevemos nossa transação, precisamos adicioná-la
  à nossa mempool. Isso iniciará o processo de enviá-la
  pela rede.

  Antes de podermos colocar *qualquer* transação, inclusive a nossa, na mempool,
  temos que verificá-la primeiro.

  Vamos verificar esta transação.

  Ela tem um txid válido?

  AÇÃO: Nós verificam se a transação que acabaram de escrever tem um txid válido (deve
  ser uma palavra seguida por um número de dois dígitos, como 'hello11' ou 'jet89').

  Ela tem uma entrada válida. Aquela que está listada na mempool ou no
  conjunto UTXO. Também precisa estar assinada.

  AÇÃO: Nós verificam se sua entrada está ok.

  Finalmente, não podemos bloquear mais bitcoin nas saídas do que tínhamos
  disponível para gastar nas entradas.

  AÇÃO: Nós verificam novamente seus valores.

  Se todas essas verificações passarem, marque sua transação como válida e coloque-a
  na mempool.

  AÇÃO: Use o carimbo auto-tintante Aprovado para marcar a transação que acabamos
  de escrever como aprovada e coloque-a na mempool. A mempool de todos
  agora deve ter duas transações.
  ```

## Em Resumo

Nesta parte do LARP, nós:

- Recebemos nossa primeira transação 'não confiável'
- Validamos a transação
- Observamos como o valor das entradas vem da saída de outra transação
- Aprendemos para que serve a mempool
- Escrevemos nossa primeira transação
- Fizemos uma saída de troco
