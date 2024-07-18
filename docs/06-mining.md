# Mineração - construindo a cadeia

Esta é a fase final do LARP e pode durar enquanto os participantes estiverem interessados. Também é a mais caótica e difícil de gerenciar, pois o poder da descentralização realmente começa a aparecer.

Aprenderemos como minerar blocos, enviar blocos pela rede e validá-los quando os recebermos.

Tempo Estimado: 30 a 40 minutos

## Índice

  * [Materiais Usados](#materiais-usados)
  * [Objetivos Desta Fase](#objetivos-desta-fase)
  * [Mineração de Nonces](#mineração-de-nonces)
  * [Transmitindo um Bloco Válido](#transmitindo-um-bloco-válido)
  * [Solicitando um Bloco de um Par](#solicitando-um-bloco-de-um-par)
  * [Validando um Bloco](#validando-um-bloco)
    * [Validando Transações de Bloco](#validando-transações-de-bloco)
    * [Marcando Saídas como Gastas](#marcando-saídas-como-gastas)
  * [Construindo uma Cadeia](#construindo-uma-cadeia)
  * [Em Resumo](#em-resumo)

## Materiais Usados

Nesta fase do LARP, usaremos os seguintes itens:

  - os BASICs
  - templates de blocos
  - canetas esferográficas
  - cartões compactos de txid de bloco
  - todos os cartões de rede
  - marcador de apagar a seco
  - lista de verificação de validação de bloco
  - suprimentos para copiar transações
    - canetas esferográficas
    - cartões de transação em branco
    - adesivos de cadeado
    - adesivos de chave

## Objetivos Desta Fase

Nesta fase, estabelecemos dois objetivos. O primeiro é quem encontra mais blocos, o que é principalmente uma questão de sorte.

O segundo é quem tem seus blocos na maioria das blockchains, o que depende de quão bem conectado um nó está e quão ativo todos os outros estão em enviar novos blocos assim que são encontrados.

Roteiro do Instrutor:

  ```
  Estamos prontos para começar a minerar, mas antes de começar, quero
  dar a todos alguns objetivos. O primeiro é que você quer
  ser o nó a encontrar o bloco, mas esse bloco não vale
  muito se a rede não concordar sobre como a
  blockchain deve ser.

  Depois de encontrar um hash de bloco vencedor, você deve rapidamente
  começar a enviá-lo pela rede.

  O nó que tem mais blocos nas blockchains de outros pares
  será o vencedor desta fase do LARP.
  ```

## Mineração de Nonces

Um nonce é o dado que você muda em um cabeçalho de bloco que altera o resultado do hash que você obtém. Os BASICs procurarão automaticamente um nonce vencedor para você.

Roteiro do Instrutor:

  ```
  Estamos prontos para usar nossos BASICs para procurar um hash de bloco
  vencedor. Para fazer isso, precisamos encontrar um nonce que,
  juntamente com as outras informações no cabeçalho do bloco, nos dê
  um hash de bloco que esteja abaixo do alvo.

  Qual é o número que um hash de bloco vencedor deve estar abaixo
  para este bloco?

  R: 8500 (dica: está escrito no cabeçalho do bloco, como o alvo)

  Vamos digitar as informações do cabeçalho do bloco no BASIC e deixar
  ele encontrar um nonce vencedor para nós. Isso pode levar alguns minutos.

  AÇÃO: Percorra a digitação dos números para um dos
  nós mais próximos. Quando chegar à tela do nonce, diga o seguinte:

  Para o nonce, como não o conhecemos, deixe-o em branco e
  avance para a próxima tela.

  AÇÃO: Faça com que os nós digitem os dados do cabeçalho do bloco no
  seu template de bloco no BASIC. A tecla '#' avançará
  para a próxima tela. A tecla '*' excluirá caracteres.

  Quando seu BASIC encontrar um nonce vencedor, ele parará de procurar e
  mostrará na tela. Anote isso no seu template de bloco
  antes de avançar para a próxima tela no BASIC, que deve mostrar
  o hash do bloco. Anote isso também no cabeçalho do bloco, acima
  da palavra "blockheader".

  Como você saberá que um hash de bloco é válido?

  R: Será um número menor que o alvo do bloco.

  Quando seu bloco encontrar um nonce válido, por favor, levante a mão
  e todos passaremos por como transmitir um bloco.

  AÇÃO: Espere até que um nó levante a mão. Ande por aí e
  ajude os nós a fazerem seus BASICs funcionarem.
  ```

## Transmitindo um Bloco Válido

Dependendo dos deuses dos nonces, dentro de alguns minutos ou segundos, você deve ter um hash de bloco vencedor encontrado.

Para esta seção, deixaremos o primeiro bloco vencedor se propagar por toda a rede antes de retomarmos a busca pelo próximo bloco.

Roteiro do Instrutor:

  ```
  Ok, encontramos nosso primeiro bloco vencedor. Vamos pausar por um momento
  e passar por como transmitir um bloco pela rede.

  Certifique-se de ter preenchido o template de bloco com as informações
  do BASIC, particularmente seu nonce. Você precisará do hash do bloco
  para informar seus pares sobre seu bloco.

  A primeira coisa que um nó com um novo bloco deve fazer é notificar todos
  os seus pares de que tem um bloco vencedor. Para fazer isso, precisaremos
  da mensagem de rede Eu Tenho Blocos.

  Coloque o hash do bloco nesta mensagem e envie uma para cada um dos seus pares.

  AÇÃO: espere os pares receberem a mensagem de Eu Tenho Bloco. Isso deve
  ser dois ou três dos outros nós; então, dois ou três nós, dependendo da sua
  rede, devem não ter recebido nada.
  ```

## Solicitando um Bloco de um Par

Aprender a transmitir blocos pode ser um pouco tedioso e usará todas as habilidades que aprendemos até agora no LARP.

Se algum outro nó encontrar um hash de bloco vencedor enquanto estamos fazendo isso, diga a eles que ele é inválido e eles terão que esperar para construir em cima deste bloco atual.

Todos devem estar trabalhando para transmitir este primeiro bloco pela rede antes de construir o próximo bloco.

Roteiro do Instrutor:

  ```
  As mensagens de Eu Tenho Bloco funcionam quase da mesma forma que as mensagens de Eu Tenho Transação.
  Se você não tiver os blocos listados na mensagem,
  deve solicitá-los.

  Preencha uma mensagem de Enviar Blocos e envie de volta para o par que
  lhe enviou o cartão de Eu Tenho Blocos.

  AÇÃO: espere as mensagens começarem a chegar ao nó que
  encontrou o primeiro bloco.

  Para enviar uma cópia de um bloco para um par, você precisará fazer uma cópia do seu
  bloco vencedor.

  Como isso funciona, você precisará de um novo envelope de bloco e cartão de cabeçalho
  de bloco. Preencha o cartão de cabeçalho de bloco com todos os dados do seu bloco.
  Deixe de fora o hash do bloco que você calculou. Coloque isso no
  bolso do bloco que você enviará para seu par.

  AÇÃO: Ajude o nó vencedor a preencher um novo cabeçalho de bloco para a cópia
  do bloco.

  Primeiro, faça uma cópia da transação coinbase e coloque
  isso dentro da cópia do bloco.

  AÇÃO: Espere o nó vencedor fazer uma cópia da transação coinbase.

  Vamos usar o protocolo de Bloco Compacto para enviar blocos pela
  rede. Isso nos economiza muito trabalho de ter que enviar
  cópias de transações.

  Para fazer isso, usaremos os cartões de Bloco Compacto. Colocaremos os txids
  de todas as transações no bloco no cartão e
  depois colocaremos isso dentro da cópia do bloco.

  AÇÃO: Ajude o nó vencedor a preencher o cartão de Bloco Compacto e colocar
  na cópia do bloco.

  Ok, fizemos nossa primeira cópia de bloco. Estamos prontos para enviá-lo a um par
  que o solicitou.

  AÇÃO: Envie a cópia do bloco pela corda para um dos nós que a pediu.

  AÇÃO: Faça com que o nó vencedor faça cópias para TODOS os outros nós.
  Isso permitirá que todos validem o bloco ao mesmo tempo.

  AÇÃO: Distribua as cópias dos blocos para todos os nós, mesmo os
  que não ouviram falar dele originalmente.
  ```

## Validando um Bloco

Vamos garantir que nosso bloco seja válido!

Faça os nós usarem o cartão de lista de verificação de validação de bloco para acompanhar, marcando itens com seu marcador de apagar a seco.

Roteiro do Instrutor:

  ```
  Quando seu nó receber um novo bloco pela rede, precisaremos validar
  que ele tem as informações corretas dentro dele.

  Aceleramos muito as coisas para que todos possam
  passar juntos pela validação de um novo bloco. Normalmente, você teria que esperar que
  seu par lhe informasse sobre um bloco antes de obter uma cópia dele.

  Vamos passar juntos pelo processo de validação de bloco.

  Primeiro, queremos verificar se o bloco tem um hash de bloco válido.

  Usaremos nossos BASICs para fazer isso.

  AÇÃO: Digite os dados do cabeçalho do bloco no BASIC.

  Meu BASIC diz que o hash do bloco para este bloco é <leia o hash do bloco>.

  Este é um hash de bloco válido?

  R: Sim

  Como você sabe?

  R: É menor que o alvo.

  OK, vamos verificar se as transações neste bloco são válidas.

  AÇÃO: Faça os nós tirarem a transação coinbase e o Bloco Compacto
  de dentro do bloco.

  Neste bloco, recebemos uma coinbase e um Bloco Compacto. Precisaremos
  garantir que temos todas as informações da transação antes de
  terminar de verificar este bloco.

  Vamos terminar de verificar o cabeçalho do bloco. Precisamos verificar se o
  compromisso de tx está correto. Vamos somar todos os números dos
  txids no cartão do Bloco Compacto e na coinbase. Eles são iguais
  ao compromisso de tx?

  AÇÃO: Espere os nós calcularem, devem dizer sim.
  ```

### Validando Transações de Bloco

Garantir que o bloco tenha transações válidas é provavelmente a parte mais trabalhosa. Se um nó estiver faltando uma transação, ele terá que usar mensagens de rede para pedi-la aos seus pares.

Roteiro do Instrutor:

  ```
  Em seguida, precisamos garantir que o bloco tenha transações válidas.

  Para fazer isso, precisaremos de uma cópia real de cada uma das transações no
  bloco. Usando a lista de transações no Bloco Compacto,
  procure na sua mempool cada uma das transações listadas.

  Se você não tiver uma transação listada, precisará solicitá-la
  aos seus pares usando a mensagem Enviar Transação.

  AÇÃO: Ajude os nós a encontrar/obter as cópias das transações que eles
  precisam.

  Ok, todos têm as transações de que precisam para validar este bloco.

  Se você não conseguir encontrar as transações ou se uma das transações
  já estiver no conjunto UTXO, este bloco é inválido e você pode descartá-lo.

  Este é um bloco válido, no entanto, e todos têm as transações de que precisam.

  Vamos primeiro verificar a transação coinbase. Ela deve não ter entradas,
  um txid válido e o valor da saída deve ser menor ou igual a
  50 mais as taxas que as transações pagam.

  Quantas taxas as outras transações no bloco pagam?

  R: <varia, dependendo do jogo>

  Quantos bitcoins há nas saídas da transação coinbase?

  R: <varia, deve ser igual a 50 + taxas da pergunta anterior>

  Ótimo. Esta é uma transação coinbase válida.

  Se as transações forem aquelas que você já aprovou, não precisa
  revalidá-las. Isso é uma coisa boa sobre ter transações
  na sua mempool - elas já estão validadas!

  Uma última coisa a verificar nas transações em um bloco é
  que todas elas gastam de UTXOs ou de outras transações
  no mesmo bloco.

  Se alguma transação no bloco listar como uma entrada um txid que não está
  também naquele bloco ou no conjunto UTXO, todo o
  bloco é inválido.
  ```

### Marcando Saídas como Gastas

Roteiro do Instrutor:

  ```
  Agora que sabemos que este bloco é válido, temos uma tarefa final
  para fazer antes de considerarmos este bloco parte da nossa blockchain.

  Precisamos promover todas as transações que estavam dentro do bloco
  da mempool para o conjunto UTXO.

  Também precisamos riscar qualquer entrada que tenha sido gasta neste bloco.

  Encontre a saída que cada entrada neste bloco gasta e marque-a.

  Uma vez que uma saída é gasta, ela é removida do conjunto UTXO e
  não pode ser gasta novamente.

  Qualquer nova saída que foi criada neste bloco é adicionada ao
  conjunto UTXO.

  AÇÃO: Faça os nós marcarem as saídas gastas e colocarem novas transações
  na cesta do conjunto UTXO. Isso inclui a transação coinbase.

  Ok, finalmente, podemos adicionar este bloco à nossa blockchain.

  AÇÃO: Coloque o novo bloco na blockchain (Estojo de Cartão Index) junto
  com a Transação Gênese.
  ```

## Construindo uma Cadeia

Certo. Finalmente estamos prontos para construir uma blockchain.

Roteiro do Instrutor:

  ```
  Finalmente completamos todo o ciclo de vida de uma transação e
  adicionamos novos blocos à cadeia bitcoin. Estamos apenas um bloco
  dentro, no entanto.

  Vamos tentar encontrar o próximo bloco.

  Para todos que *não* venceram este bloco, precisarão atualizar
  seu template de bloco.

  Jogue fora o cabeçalho do bloco e comece de novo, desta vez usando o
  hash do bloco do bloco mais recente que você recebeu e atualize
  a hora para agora.

  Você também precisará retirar quaisquer transações que foram mineradas
  no último bloco. Você pode ter novo espaço, então deve encontrar
  algumas novas transações da mempool para adicionar a ele.

  Não se esqueça de atualizar a transação coinbase se as taxas
  mudarem e recalcular o compromisso de tx no cabeçalho do bloco.

  Depois de ter um template de bloco atualizado, digite os dados do cabeçalho do bloco
  no BASIC e cruze os dedos.

  Que o minerador mais sortudo vença!

  AÇÃO: Entregue o jogo aos nós. Eles agora devem saber
  como minerar blocos, construir cabeçalhos etc.

  AÇÃO: Encerre o jogo após alguns blocos ou quando os participantes do nó
  começarem a perder o interesse.
  ```

## Em Resumo

Nesta parte do LARP, nós:

- Usamos os BASICs para encontrar um nonce vencedor
- Transmitimos uma transação para os pares
- Validamos um novo bloco
- Aprendemos como funciona o protocolo de Bloco Compacto
- Promovemos transações da mempool para o conjunto UTXO
- Construímos uma blockchain

Parabéns, você conseguiu! Você fez a blockchain do Bitcoin ganhar vida.

