# Extensões - coisas para tentar

Aqui estão algumas ideias de coisas para tentar de forma diferente quando você executar o próximo LARP. Recomendo não tentar variações com um público novo no protocolo bitcoin, mas essas são ótimas coisas para adicionar quando os participantes do jogo se sentirem confortáveis com a jogabilidade.

## Índice

  * [Lojas de Bitcoin](#lojas-de-bitcoin)
  * [Impulso do BASIC](#impulso-do-basic)
  * [Reajuste de Dificuldade](#reajuste-de-dificuldade)
  * [Transações Substituíveis na Mempool](#transações-substituíveis-na-mempool)

## Lojas de Bitcoin

Peça aos participantes que tragam itens para vender por bitcoin para seus pares.

Faça com que cada nó precise criar uma transação comprando e uma transação vendendo algo toda vez que ganharem um bloco.

## Impulso do BASIC

Compre ou construa mais BASICs. Como facilitador, ofereça-os para venda aos nós por bitcoin.

Informe-os quantas confirmações sua transação precisa antes de considerar a venda final.

## Reajuste de Dificuldade

Na blockchain regular do bitcoin, a dificuldade muda a cada 2016 blocos. No LARP, podemos atualizar a dificuldade a cada 5 blocos.

Depois que o 5º bloco for minerado, peça aos nós que recalcularem o alvo que vai em cada cabeçalho de bloco.

Use os cartões de Cálculo de Dificuldade incluídos para ajudar a resolver isso.

O 6º bloco na rede deve ter o valor de alvo correto. Se o alvo estiver errado, o bloco é considerado inválido.

## Transações Substituíveis na Mempool

Esta modificação tem a ver com quais transações são permitidas na mempool.

Se um nó decidir que quer gastar uma saída que já tem uma transação gastando-a na mempool, geralmente é considerado inválido.

Com esta regra, qualquer nova transação que queira gastar uma saída que outra transação já está gastando agora é *permitida*, mas deve pagar o dobro da taxa da transação que está expulsando da mempool.
