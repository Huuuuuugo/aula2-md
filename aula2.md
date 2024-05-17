# Slide 1 - Intro

# Slide 2 - Listas
A gente vai começar essa aula falando de uma estrutura que já foi abordada na primeira aula. As lista.
\
Bom, como eu disse na primeira aula, uma lista vai ser uma estrutura que vai agrupar elementos para serem reutilizados mais à frente no código.

## Slide 3 - Tipos de listas
Aqui nesse slide, a gente pode ver mais alguns detalhes sobre as listas em python.
\
Primeiramente, a gente tem aqui a forma de se declarar uma lista em python. Algo que já foi abordado na primeira aula. Basta atribuir, a uma variável, um grupo de elementos separados por vírgula e cercados por colchetes.

Aqui embaixo, a gente tem duas características das listas em python, elas são heterogêneas e multidimensionais. Bom, esses dois conceitos são algo que a gente já viu em algumas outras disciplinas, mas, relembrando: uma lista heterogênea é uma lista que vai conter dados de diferentes tipos, numa mesma lista a gente pode ter int, float, str, efim, diferentes tipos de dados. Vamo começar vendo esse conceito no VSCode.

Digamos que a gente queira armazenar os dados de um determinado usuário, de determindo serviço, a gente pode usar uma lista heterogênea pra isso.

Digamos que isso seja para um serviço de streming, a gente vai começar digitando o nome da lista, e dentro dessa lista a gente vai digitar as informações desse usuário: nome, idade, email, status da assinatura.
```py
usuario = [
    "João da Silva", # nome
    30, # idade
    "joao@gmail.com", # email
    True # status da assinatura
    ]
```
E assim a gente conseguiu armazenar as informações do usuário "João da Silva" em uma única estrutura. Usando uma lista heterogênea. Uma lista contendo o nome, como uma string, a idade, como inteiro, o email, como string, e o status da assinatura, como booleana.
\
\
\
Em contraste a listas heterogêneas, a gente tem as listas homogêneas, que são listas que vão armazenar apenas um tipo de dado.
\
Um exemplo disso seria a lista de gêneros faoritos desse usuário:
```py
generos_favoritos = ["Ação", "Terror", "Suspense"]
```
Essa é uma lista que contém apenas dados do tipo string, e, por tanto, é uma lista homogênea. Então, isso quer dizer que python é capaz de lidar com listas homogêneas e heterogêneas de forma dinâmica, basta colocar os elementos e eles vão ser agrupados, independente do tipo.
\
\
\
Outra coisa mencionada no slide também foram listas multidimensionais.

Bom, listas muldimensionais não mais são do que listas dentro de listas. Acontece que, como a gente viu, python consegue lidar com listas heterogêneas, listas com dados de diferentes tipos, esses diferentes tipos também inclui outras listas.

Então, além de lidar com `apontando pro exemplo de lista heterogênea` strings, inteiros e booleanos, em uma lista, python também consegue lidar com outra lista dentro dessa lista, e isso é o que a gente chama de listas multidimensionais.

A gente pode criar um exemplo aqui de lista muldimensional simplesmente adicionando a lista de gêneros favoritos à lista do usuário. Fazendo isso, essa lista vai passar de heterogênea para mltidimensional e heterogênea.
```py
usuario = [
    "João da Silva", # nome
    30, # idade
    "joao@gmail.com", # email
    True, # status da assinatura
    ["Ação", "Terror", "Suspense"] # gêneros favoritos
    ]
```

Outro exemplo bem claro de listas multidimensionais são as matrizes. 

Quem também tá tendo a disciplina de Métodos Numéricos já deve saber bem, mas matrizes são estruturas da matemática que vão armazenar dados em linhas e colunas. A gente pode aplicar essa ideia à listas multidimensionais da seguinte forma:
```py
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```
Organizando dessa forma, a gente tem uma lista para cada linha, e um elemento para cada coluna.
\
E essa forma mais comum de se representar uma matriz em python.
\
\
\
\
\
Agora que a gente já aprendeu um pouco sobre listas, a gente pode avançar pra parte de manipulação dessa estrutura. 
\
A gente viu com declarar uma lista com dados heterogêneos, homogêneos e multidimensionais. Vamos ver agora como manusear esses dados.

## Slide 4 - Indexação
A indexação é a forma mais básica de manipulação de dados em estruturas de dados. É algo que está presente em basicamente toda linguagem que possua estrutras de dados, é algo que existe em C, em Java, em Javascript, enfim, é uma abordagem que não se limita ao python.

Essa técnica consiste, basicamente, em associar um valor numérico a cada elemento da lista, permitindo que a gente referencie esse elemento a partir desse valor numérico, `exemplos do slide` aqui a gente pode ver alguns exemplos de indexação: a gente vai simplesmente escrever o nome da lista e o índice, o valor numérico, associado ao valor que a gente quer.

Aqui a gente tem também um ídice negativo, a gente vai comentar isso melhor depois.

E esse índice, em python, assim como na maioria das outras linguagens, começa a contar a partir do 0 e vai sendo incrementado de 1 em 1, conforme a gente vai adicionando elementos à lista.

E, como a gente pode ler aqui em baixo, essa é uma técnica voltada a acessar ou modificar um elemento específico. Então, a indexação vai lidar com um elemento de cada vez. É um número pra um elemento.

Voltando aqui no VSCode:

#### indexação em lista heterogêneas
```py
usuario = [
    "João da Silva", # nome
    30, # idade
    "joao@gmail.com", # email
    True, # status da assinatura
    ["Ação", "Terror", "Suspense"] # gêneros favoritos
    ]
```
Nessa lista, a gente teria "João da Silva", como elemento 0, 30, como elemento 1, "joao@gmail.com", como elemento 3 e assim por diante.

A gente pode confirmar isso usando a indexação pra resgatar esses valores:
```py
    print(usuario[0])
```
`João da Silva`

Executando isso, a gente vai ver que a sída é "João da Silva", que é o que foi armazenado no índice 0. Continuando:
```py
    print(usuario[1])
```
`30`

Ao executar isso, a gente vai ver que o que vai ser exibido é 30, que é o conteúdo no índice 1. Continuando pro 2:
```py
    print(usuario[2])
```
`joao@gmail.com`

Executando a gente vai ver o email do Joâo.

E indexando 3, vai ser exibido True:
```py
    print(usuario[3])
```
`True`

#### substitução de um valor por meio do índice
E isso não se limita só à leitura, eu posso também escrever naquele elemento da lista usando a indexação.

Digamos que eu queira cancelar a assinatura do João, eu posso simplesmente fazer o seguinte:
```py
    usuario[3] = False
```
E ao printar a lista:
```py
    usuario[3] = False
    print(usuario)
```

A gente vai ver que o status da assinatura do João foi atualizado pra False.

#### indexação em listas multidimensionais

Então, até aqui a gente viu o uso do índice na porção unidimensional dessa lista, que é bem simples, a gente só coloca o nome da lista e o ídice do elemento que a gente quer ver ou modificar. 

Mas e o que acontece se eu colocar o índice de uma lista? Olhando aqui nos elementos da lista 'usuario', a gente vê que o último elemento é outra lista, a lista de gêneros favoritos desse usuário, então, o que vai acontecer se eu indexar esse elemento, esse de índice 4?

Bom, o que vai acontecer é bem intuitivo, na verdade, a gente vai receber toda a lista.
```py
    print(usuario[3])
```
`["Ação", "Terror", "Suspense"]`

Agora digamos que a gente queira puxar um elemento específico, como esse "Terror", dessa lista, pra isso a gente vai fazer o seguinte:
```py
    print(usuario[3][1])
```
`Terror`

Executando a gente vai ver "Terror" no terminal. O que a gente fez aqui foi, basicamente, indexar a primeira lista, com `usuario[3]`, e depois a segunda lista, com esse segundo índice `[1]`.
\
\
\
E o mesmo vale pra essa matriz:
```py
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```
Se a gente quiser o elemento na segunda linha e terceira coluna, a gente vai digitar:

Lembrando que, como a gente começa a contar do zero, a segunda linha vai ser 1, e a terceira coluna vai ser 2.
```py
print(matriz[1][2])
```
`6`

#### índices negativos
Antes de finalizar esse assunto de indexação, vamos falar um pouco dos índices negativos, que a gente viu lá no slide.

Bom, a ideia dos índices negativos é quase a mesma da dos não negativos, a única diferença é que eles vão percorrer a lista de trás para a frente.

Então, se eu digitar:
```py
    print(usuario[-1])
```
Ao invés de receber o elemento na posição 1, eu vou receber o elemento na última posição.

`["Ação", "Terror", "Suspense"]`

Que é essa lista.

E se eu digitar -2, eu vou receber o penúltimo:
```py
    print(usuario[-1])
```
`False`

E assim por diante.

A ideia é a mesma, só que esses vão percorrer de trás para a frente.

E esse uso de índices negativos é um diferencial do python, nem toda linguagem que tem indexação, tem índices negativos.
\
\
\
Bom, continuando, além de adicionar índices negativos, python também acrescenta a essa ideia de indexação de outra forma.

## Slide 5 - Slicing

Com o slicing, ou fatiamento.

Como a gente discutiu anteriormente, a função da indexação era referenciar um valor único na lista, certo?

Bom, o fatiamento é uma forma de acessar uma porção da lista, ou seja, vários elementos da lista.

Então é como a indexação, só que pra multiplos valores.

Voltando no VSCode:

Pra esse exemplo, a gente vai criar uma lista nova.

Digamos que seja uma lista de compras:
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
```
#### start

Para pegar uma fatia dessa lista, a gente vai começar com o índice em que a gente quer começar a fatiar:
```py
compras[1]
```

#### stop

Em seguida, dois pontos e o elemento em que a gente quer parar:
```py
compras[1:2]
```

Mas tem um detalhe.

Usando aquela lógica dos ídices contados a partir do zero, aqui a gente estaria instruindo o programa a pegar a partir do índice 1, que contém 'ovos', até o índice 2, que contém 'pão'. Nessa lógica, a gente deveria ver no terminal uma lista contendo os elementos ['ovos', 'pão'].

Porém, se eu executar o programa, a gente vai ver que não é bem assim.

`['ovos']`

Vai ser exibido apenas ['ovos']
\
\
Bom, o motivo de isso acontecer é bem simples na verdade. Esse segundo número. Esse logo após os dois pontos. Ele não segue aquela lógica de iniciar contagem no zero, ele conta a partir do 1, então, apesar do índice de início ser contado a partir do zero, o ídice de parada vai ser contado a partir do 1. 

Então esse à esquerda vai começar a contar do zero e esse à direita vai começar a contar do 1. O que quer dizer que 1, quando à esquerda dos dois pontos, se refere ao mesmo elemento que dois, quando à direita dos dois pontos. 

Então esses dois elementos estão se referindo a 'ovos', por isso que quando a gente executa isso, o resultado é uma lista contendo somente 'ovos'

Entâo, se a gente quiser pegar a lista contendo ['ovos', 'pão'], a gente vai começar pegando o elemento `apontando pra lista` 0 > 1, elemento 1, que é ovos, como inicial. E o elemento 1 > 2 > 3, que é pão, como elemento de parada.

Executando isso, a gente vai ver a lista esperada.

#### indices negativos

E esse fatiamento, assim com a indexação normal, pode usar índices negativos

Se eu quisesse, por exemplo, pegar do segundo elemento até o fim da lista, eu poderia usar um índice negativo:
```python
compras[1:-1]
```
`['ovos', 'pão', 'maçã', 'banana']`
E isso iria me retornar tudo do elemento 1 até o fim da lista

Na verdade, tem uma forma ainda mais direta de se conseguir isso, basta omitir esse último elemento, que ele vai ser presumido como o fim da fila.
```python
compras[1:]
```
`['ovos', 'pão', 'maçã', 'banana']`

Além disso, se a gente omitir esse primeiro valor, ele vai ser presumido como início da fila.

Então, se eu quiser uma lista do início até o terceiro elemento, 'pão', eu posso simplesmente:
```python
compras[:3]
```
`['leite', 'ovos', 'pão']`

#### step
Além desses dois parâmetros, de incio e parada, a gente também tem um teceiro parâmetro pro fatiamento, que é o salto.

O salto vai definir quantos elementos vao ser pulados por vez.

Então, se eu fizer o seguinte

```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
print(compras[::2])
```
`['leite', 'pão', 'banana']`

`explicar a saída um sim, outro não`

#### step negativo

Um uso muito comum desse parâmetro de salto é na inversão de estruturas. Se eu colocar um salto de -1, a lista vai ser percorrida de trás pra frente.
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
print(compras[::-1])
```
`['banana', 'maçã', 'pão', 'ovos', 'leite']`

# Slide 6 - Strings

## Slide 7 - Indexação e Fatiamento

```py
texto = "Python"
```
`pegar o primeiro índice`
`pegar o último índice`
`pegar uma fatia`
`inverter a string`

Mesma ideia, só que em strings.

# Slide 8 - Métodos
## Slide 9 - Métodos de strings
#### lower / upper
como o resultado de input() é uma string, eu posso colocar o método direto depois do input
```py
entrada = input().lower()
print(entrada)
```
lower() vai servir para normalizar a entrada do usuário, deixando tudo minúsculo, útil em aplicações case-insensitive.

#### strip
o strip vai servir para remover os espaços em branco à esquerda ou direita da string
```py
entrada = input().strip()
print(entrada)
```

#### encadeamento de métodos
é possível colocar método depois de método para todos atuarem em uma mesma string
```py
entrada = input().strip().lower()
print(entrada)
```

#### count
vai retornar o índice da posição onde uma determinada substring aparece

últil para checar quantas vezes algo aparece na string
`Entrada: uma string qualquer com vários espaços`
```py
entrada = input().strip().lower()
print(entrada.count(' '))
```

#### replace
substitui uma porção da string por outra string

`Entrada: python é complicado`
```py
entrada = input().strip().lower()
print(entrada.replace('python', 'java'))
```

#### split
o split vai pegar uma string, separá-la em cada ocorrência de um determinado caractere, e retornar uma lista contendo todas as string separadas
`Entrada: joão da silva`

`Entrada: 10 25 33 40 21`
```py
entrada = input().strip().lower()
print(entrada.split(' '))
```


## Slide 10 - Métodos Listas
#### append
adiciona o elemeto do parentese ao fim da lista

voltando no código da lista de compras
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
```
a gente pode adicionar elementos a essa lista usando append()

`Entrada: batata`
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
compras.append(input())
print(compras)
```

#### pop
vai remover um elemento da lista

por padrão, remove o último elemento.
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
compras.pop()
print(compras)
```
mas é capaz de remover qualquer elemento, basta especificar o índice dentro dos parenteses
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
compras.pop(0)
print(compras)
```

pra quem se lembra da diferença entre listas e pilhas, com essa função pop, a gente pode simular a função de qualquer um dos dois com uma lista em python.

#### index
vai devolver o índice do elemento especificado entre o parenteses
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
print(compras.index('pão'))
```

dá pra combinar isso com o pop, pra remover um elemento específico da lista com input
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
i = compras.index(input())
compras.pop(i)
print(compras)
```

#### copy
copy, como o nome sugere, vai criar uma cópia de uma lista.

mas pra entender o uso do copy a gente precisa antes entender que, em python, quando a gente atribui uma lista a uma outra variável, a gente não tá criando uma cópia dessa lista, e sim uma referencia a essa lista.
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
lista2 = compras
```
as duas variáveis vão apontar para a mesma lista, então, se eu modificar uma, a outra também vai ser modificada
```py
compras = ['leite', 'ovos', 'pão', 'maçã', 'banana']
lista2 = compras
lista2.pop()

print(compras)
```

# Slide 11 - Dicionários
## Slide 12 - Conceitos
Em Python, um dicionário é uma estrutura de dados que permite armazenar pares de chave-valor. É semelhante a uma lista, mas em vez de usar índices numéricos para acessar elementos, um dicionário usa chaves para acessar seus valores associados de forma rápida e eficiente.

É paralelo a uma variável comum, a gente vai ter um identificador textual e um valor armazenado, só que em uma estrutura que armazena vários elementos separados por vírgula e fechados por chaves.

voltando naquela primeira lista, a gente tem um exemplo bem claro de um dicionário:
```py
usuario = {
    "nome": "João da Silva",
    "idade": 30,
    "email": "joao@gmail.com",
    "assinatura": True,
    "favoritos": ["Ação", "Terror", "Suspense"]
}
```
`indexação por chave`
`atualização de um valor por chave (assinatura)`

## Slide 13 - Métodos
#### key
retorna uma lista com todas as chaves do dicionário
```py
usuario = {
    "nome": "João da Silva",
    "idade": 30,
    "email": "joao@gmail.com",
    "assinatura": True,
    "favoritos": ["Ação", "Terror", "Suspense"]
}
print(usuario.keys())
```

#### values
retorna uma lista com os valores no dicionário
```py
usuario = {
    "nome": "João da Silva",
    "idade": 30,
    "email": "joao@gmail.com",
    "assinatura": True,
    "favoritos": ["Ação", "Terror", "Suspense"]
}
print(usuario.values())
```

#### pop
remove um par de cave-elemento especificado por chave
```py
usuario = {
    "nome": "João da Silva",
    "idade": 30,
    "email": "joao@gmail.com",
    "assinatura": True,
    "favoritos": ["Ação", "Terror", "Suspense"]
}
usuario.pop('favoritos')
print(usuario)
```


#### update
atualiza o valor de em uma chave exixtente ou adiciona um par de chave-valor novo ao dicionário.

```py
usuario = {
    "nome": "João da Silva",
    "idade": 30,
    "email": "joao@gmail.com",
    "assinatura": True,
    "favoritos": ["Ação", "Terror", "Suspense"]
}
usuario.update({"assinatura": False})
print(usuario)
```
como aqui eu coloquei uma chave que já existia, o valor só foi atualizado.

```py
usuario = {
    "nome": "João da Silva",
    "idade": 30,
    "email": "joao@gmail.com",
    "assinatura": True,
    "favoritos": ["Ação", "Terror", "Suspense"]
}
usuario.update({"plano": "básico"})
print(usuario)
```
como aqui eu coloquei uma chave inexistente, foi adicionada uma nova entrada no dicionário.
