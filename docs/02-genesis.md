# Gênese: O LARP Começa

A primeira fase do LARP é sobre desempacotar o que está no software bitcoin-core que seu nó baixou, inspecionando e verificando o bloco e a transação da gênese.

Isso nos introduz a blocos, transações, coinbases, validação e o 'bloco gênese'.

Tempo estimado: 15 minutos

## Índice

  * [Materiais Usados](#materiais-usados)
  * [Desempacotando o bitcoin-core](#desempacotando-o-bitcoin-core)
  * [O Bloco e a Transação Gênese](#o-bloco-e-a-transação-gênese)
  * [Introdução ao conjunto UTXO](#introdução-ao-conjunto-utxo)
  * [Identificando Nossas Saídas](#identificando-nossas-saídas)
  * [Verificando o Cabeçalho do Bloco Gênese](#verificando-o-cabeçalho-do-bloco-gênese)
    * [O 'tx commitment'](#o-tx-commitment)
    * [Calculando o hash do bloco](#calculando-o-hash-do-bloco)
  * [Em Resumo](#em-resumo)

## Materiais Usados

Nesta fase do LARP, usaremos os seguintes itens:

  - quase tudo, mas especialmente:
  - a blockchain;
  - o bloco gênese;
  - a transação gênese;
  - o cesto do conjunto UTXO;
  - cartão de chave secreta;
  - o minerador BASIC;

Coisas que *não* usaremos nesta fase do LARP (mas podem passar pelo nosso cesto de nós como parte de [Desempacotando o bitcoin-core](#desempacotando-o-bitcoin-core)).

  - a primeira transação da rede;
  - a corda;
  - tesouras;
  - cartões de rede;
  - marcador de quadro branco;
  - cabeçalhos de mensagens de rede (argolas de fichário);
  - adesivos de chave + cadeado;
  - carimbo aprovado;
  - canetas;
  - transações em branco;
  - cabeçalhos de bloco em branco;
  - templates de bloco em branco;
  - cartões de bloco compacto em branco;
  - cartão de pontuação do nó;
  - listas de verificação de tx + bloco;

## Desempacotando o bitcoin-core

A primeira coisa que fazemos é dar uma volta pelo que está nos nós de todos. Normalmente, fazemos isso desempacotando os cestos até chegarmos ao item final no fundo: os próprios cestos.

Aqui está uma lista aproximada e explicação de cada item. Você deve ler isso enquanto passa pelos itens, segurando-os um por um enquanto tira as coisas e as coloca na mesa.

- *cartões de transação*: Estes são os cartões de transação em branco que usaremos para fazer novas transações de bitcoin.
- *argolas de fichário*: Estes são nossos cabeçalhos de mensagens de rede. Eles nos permitem enviar mensagens entre nós.
- *envelopes/templates de bloco*: Estes são templates de bloco. Vamos usá-los para construir novos blocos.
- *cartões de Cabeçalho de Bloco em branco*: estes são cabeçalhos de bloco em branco.
- *adesivos de chave + cadeado*: Estas chaves e cadeados são para garantir e gastar bitcoin em transações.
- *carimbo aprovado*: Vamos usar isso para marcar transações como validadas.
- *canetas*: Sem explicação, apenas tire-as
- *marcador de quadro branco*: Isto é para escrever mensagens de rede.
- *minerador*: Este é nosso "BASIC" ou 'ASIC Básico'. Vamos usá-lo para validar blocos e minerar novos.
- *cartões de rede*: Estes são nossos cartões de rede, eles nos permitem enviar mensagens para outros nós na rede.
- *cartões de txid de bloco compacto*: Usados para enviar informações sobre blocos para nossos pares na rede.
- *cartão de pontuação do nó*: Para contar os pontos do nó no final.
- *listas de verificação de tx e bloco*: Úteis para verificar os dados que recebemos pela rede.
- *cestos de mempool + utxo*: Estes são nossos cestos para transações que recebemos pela rede.
- *cartão de chave secreta*: Esta é a chave secreta do seu nó. Não diga a ninguém qual é. É assim que você identificará moedas que pode gastar na blockchain.
- *blockchain/suporte de cartão de índice*: Esta é a nossa blockchain. Vamos ver o que está dentro.

Nota: Recomendo terminar na blockchain / suporte de cartão de índice como
o item final que você segura para explicar.

## O Bloco e a Transação Gênese

Roteiro do instrutor para a exploração do bloco gênese.

	Dentro da blockchain você encontrará um único bloco. Chamamos isso de 'bloco gênese'.
    Está incluído em cada download do bitcoin-core. Vem com o seu nó de bitcoin.

	Um bloco tem um cabeçalho de bloco na frente e transações dentro dele.
    Quantas transações há dentro deste bloco?

	R: 1

	Qual é o ID da transação desta transação?

	R: eagle33

	Quantas entradas ela tem?

	R: 0.

	Alguém sabe por que esta transação tem zero entradas?

	R: É uma transação de coinbase. É onde novos bitcoins entram no suprimento.
    Para nosso jogo, cada coinbase pode criar até 50 novos bitcoins.

	Vamos olhar para as saídas desta transação, a transação gênese. Quantas saídas há?

	R: 4 saídas

	O valor das saídas soma 50?

	R: Não, estamos perdendo uma.

	Para onde foi aquele bitcoin extra?

	R: Ele simplesmente não foi adicionado ao suprimento total de bitcoin.
    O minerador que fez a transação de coinbase pode adicionar até 50 bitcoins na coinbase, mas não precisa.
    Existem alguns blocos no bitcoin onde isso aconteceu.

## Introdução ao conjunto UTXO

Em seguida, introduzimos o conceito de manter transações que estão dentro de blocos (mas não gastas!) no conjunto UTXO.

Roteiro do instrutor:

	Esta transação está em um bloco. Agora é considerada 'minerada' ou 'confirmada'.
    Colocamos transações mineradas ou confirmadas em um dos dois cestos que temos.

	Em qual cesto você acha que uma transação confirmada vai?

	R: o conjunto UTXO

	Certo, transações confirmadas vão para o conjunto UTXO até que todas as suas saídas sejam gastas,
    momento em que podemos colocá-las de volta em seus envelopes de bloco.

	AÇÃO: Coloque a transação gênese no cesto do conjunto UTXO. Deve haver agora uma transação no conjunto UTXO.

	Há uma transação em nosso conjunto UTXO. Quantas saídas há nessa transação?

	R: 4 saídas

_Nota de Protocolo_: A primeira transação de coinbase no bloco gênese tecnicamente *não* está incluída no conjunto UTXO. Porque não está no conjunto UTXO, é considerada não gastável. Provavelmente foi um erro da parte de Satoshi, mas estamos mantendo as coisas assim. O jogo LARP não segue o protocolo exatamente: adicionamos nossa transação gênese ao conjunto UTXO, o que torna todas as suas saídas elegíveis para serem gastas em outras transações.

## Identificando Nossas Saídas

Roteiro do instrutor:

	Cada nó de bitcoin aqui deve ter recebido uma carteira com uma chave secreta nela. Este é o cartão com uma chave colorida.

	AÇÃO: Dê aos nós alguns segundos para encontrar a cor da chave secreta.

	Devemos ser capazes de identificar bitcoins que pertencem à nossa carteira encontrando saídas de transações no conjunto UTXO que combinem com sua chave secreta.
    Se você atualmente tem bitcoins bloqueados na sua chave, levante a mão.

	NOTA: Apenas 4 dos 6 nós terão bitcoins bloqueados no conjunto UTXO neste ponto.

Isso é bastante curto, mas uma maneira importante para as pessoas começarem a associar seu saldo de bitcoin como números em saídas no conjunto UTXO.

## Verificando o Cabeçalho do Bloco Gênese

Estamos mudando de tópico aqui um pouco, mas esta é a última tarefa que temos para a parte 'gênese' do LARP.

Roteiro do instrutor:

	Sempre que recebermos um novo bloco, devemos verificar se o cabeçalho do bloco é válido.
    Provavelmente deveríamos ter feito isso antes de colocar quaisquer transações dentro dele no conjunto UTXO, mas tudo bem.

	De agora em diante, vamos verificar o cabeçalho do bloco antes de olhar para as transações nele.
    Para o bloco gênese, está tudo bem fazer as coisas um pouco fora de ordem.

	Para verificar um cabeçalho de bloco, precisaremos calcular o hash do bloco. Precisaremos usar nossos BASICs para isso.

	AÇÃO: Segure um BASIC. Dê aos nós um momento para encontrar os seus.

### O 'tx commitment'

Roteiro do instrutor:

	Antes de podermos usar os BASICs, no entanto, precisamos verificar uma das informações no cabeçalho do bloco.
    Esse é o campo 'compromisso de tx' ou compromisso de transação.

	O propósito deste campo é garantir que as transações dentro do bloco realmente pertencem ao bloco que o minerador intencionou construir.

	Para este LARP, nosso compromisso de tx é a soma de todos os números nos IDs das transações dentro do bloco.

	Qual é o número do ID da transação que estava neste bloco?

	R: 33 (o ID da transação era eagle33)

	O tx commitment é igual a isso?

	R: Sim, o compromisso de tx no bloco gênese é 33.

	Agora que estamos confiantes de que as transações no bloco correspondem ao cabeçalho do bloco, estamos prontos para calcular o hash do bloco.

_Nota de Protocolo_: O 'compromisso de transação' real é uma raiz de Merkle de todos os IDs de transação do bloco. Não temos uma maneira rápida e fácil de construir uma raiz de Merkle. Em vez disso, apenas usamos algumas contas básicas.

### Calculando o hash do bloco

Roteiro do instrutor:

	Ligue seu BASIC deslizando o interruptor na lateral para a posição de ligado.

	Agora, só precisamos digitar as informações do cabeçalho do bloco e ele nos dará um hash do bloco.

	AÇÃO: Insira o primeiro campo do cabeçalho do bloco, o `hash do bloco anterior` no BASIC.
    Pressione o '#' para avançar para o próximo campo para inserir.

	Para inserir um campo, pressione a tecla '#'. Se você cometer um erro, pode excluir dígitos pressionando a tecla '*'.

	Vamos terminar de inserir todas as informações do cabeçalho do bloco no hash do bloco.

	AÇÃO: o hash do bloco deve ser mostrado na tela ao final da inserção de todos os dados.
    Escreva o hash do bloco mostrado no cabeçalho do bloco, no espaço à esquerda do título "cabeçalho do bloco".

	AÇÃO: Dê aos nós algum tempo para completar isso e escrever seu hash no cabeçalho do bloco.
    Segure um cartão de exemplo para que todos possam ver. Ande por aí e certifique-se de que todos estão obtendo o hash correto.

	Qual hash de bloco todos conseguiram para o bloco gênese?

	R: FIXME: hash do bloco gênese

	Este é um hash de bloco válido?

	R: Sim.

	Como sabemos que é um hash de bloco válido?

	R: É um número menor que o campo `alvo` no cabeçalho do bloco.

	Certo. O alvo é atualizado sempre que temos um 'ajuste de dificuldade'. Por enquanto, ficará em 8500.

	Ok. Como o hash do bloco é menor que o alvo, temos um bloco válido.

	Vamos escrever o hash do bloco na transação gênese, para sabermos de qual bloco esta transação veio.
    Isso tornará mais fácil colocar a transação de volta no envelope do bloco depois que todas as suas saídas forem gastas.

	AÇÃO: Escreva o hash do bloco, FIXME, no verso da transação no conjunto UTXO. Segure-o para que outros nós possam ver o que você fez.

## Em Resumo

Nesta parte do LARP, nós:

- Desempacotamos um nó de bitcoin core
- Encontramos a primeira transação de coinbase
- Identificamos as partes de uma transação
- Introduzimos o conjunto UTXO
- Descobrimos a chave secreta de cada nó
- Encontramos UTXOs que pertencem à nossa chave no conjunto UTXO
- Verificamos um cabeçalho de bloco usando o BASIC

Agora estamos prontos para passar para a validação e escrita de transações.
