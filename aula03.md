# Slide 1
As bibliotecas são, na minha opinião, a melhor parte do python. Além da simplicidade da sintaxe e a capacidade de simplesmente poder focar na tarefa que você quer fazer (ao invés de perder tempo com as peculiaridades da linguagem ou o passo a passo necessário em um baixo nível), Python também se destaca na imensa quantidade de bibliotecas. 

#### explicar bibliotecas

bibliotecas são mais uma forma de se trabalhar coma reutilização de código.

bibliotecas são programas inteiros focados em disponibilizar ferramentas para cumprir com uma determinada tarefa.

são basicamente um conjunto de funções e classes que ajudam a se fazer algo no código.

#### exemplos de bibliotecas

Para praticamente tudo que você queira fazer, vai existir uma biblioteca pronta pra isso: 

1. se você quer analisar ou manipular imagens; Pillow, OpenCV
2. se você quer automatizar a interação com uma interface gráfica ou automatizar um comportamento com base no que está sendo exibido na tela em um momento específico; PyAutoGui
3. se você quer trabalhar com computação mais voltada pra ciência de dados e precisa lidar com grandes quantidades de dados de uma forma eficiente; NumPy
4. se você quer extrair informações de uma página da internet; BeautifulSoup
5. se você quer trabalhar com dados em planilhas; Pandas
6. se você quer trabalhar com dados em bancos de dados relacionais; Pandas e SQLAlchemy
7. se você quer criar uma interface web pra um programa em python; Flask
8. se você quer criar uma interface gráfica mais simples sem depender de um navegador; TkTinker
9. se você quer criar testes automatizados para o seu programa; PyTest
10. se você quer que seu programa se comunique com um serviço de terceiro atraves da internet por meio de uma API, como o chatGPT ou algum serviço de texto pra fala, ou simplesmente uma base de dados; Requests

A melhor parte disso tudo é que é muito fácil instalar essas bibliotecas e módulos em python, se o módulo não vier com a linguagem, basta executar um comando no terminal que vai ser tudo instalado e configurado pra você. Você não vai ter que bater cabeça com linker, não vai ter que compilar a biblioteca (que pode acabar tendo outras dependências) com um compilador específico. Nada disso, basta escrever três palavrinhas no terminal e tá tudo feito.

## Slide 2 - import
É simplesmente a palavra chave usada para incluir uma biblioteca no programa. Equivalente ao include em C.
# Slide 3 - Bibliotecas padrão
São as bibliotecas que vem com a linguagem.
\
Não dá pra simplesmente carregar tudo, isso iria ser um desperdício enorme de RAM.
## Slide 4 - random
A random, como o nome sugere, é uma biblioteca que vai permitir que o Python trabalhe com números aleatórios.

VSCode

### Slide 5 - random functions
#### random.choice()
vamo começar criando um programa que gira uma moeda e retorna cara ou coroa.
```py
import random

resultado = random.choice(['cara', 'coroa'])
print(resultado)
# explicar namespaces
# explicar o argumento sep
```
pra acessar as funções dentro da biblioteca random, a gente tem que começar digitando o nome da biblioteca seguido de ponto e a função que a gente quer utilizar, isso é conhecido como namespace, isso é uma forma de separar as funções da biblioteca das funções do programa sendo desenvolvido. Antigamente nos tempos do C, esse conceito de namespaces não existia, então, sempre que um programador ia importar uma biblioteca nova no código, ele tinha que simplesmente torcer pra que essa biblioteca inteira não utilizasse nenhuma função com o mesmo nome que o código dele.

random.choice() vai pegar como argumento um único elemento de agrupamento (ou elemento iterável) e vai retornar um item desse grupo, escolhido aleatoriamente e cada item possui a mesma chance de ser escolhido (50/50; 33/33/33; 25/25/25/25)

Como dito, sep representa qualquer elemento iterável, o que também inclui strings.
```py
import random

resultado = random.choice('Python')
print(resultado)
```

#### random.sample()
se eu quisesse sortear mais de um elemento sem repetições eu poderia utilizar o sample
```py
import random

resultado = random.choices('Python', 2)
print(resultado)
```
k vai indicar a quantidade de resultados que eu espero.
choices vai retornar uma lista com os itens sorteados.

#### random.randint()
outra função comum nesse módulo também a randint que retornar um número aleatório em um dado intervalo de números, todos com a mesma chance.

    criar um dado
```py
dado = random.randint(1, 6)
print(dado)
```

#### random.shuffle()
e pra finalizar, a gente tem o shuffle, do inglês 'embaralhar', como o nome sugere, shuffle vai trocar aleatoriamente as posições dos elementos em uma lista.

é como embaralhar um deck de cartas, todos os elementos vão se manter, somente as ordens vão mudar.

```py
import random

cartas = ['Ás', 'Dama', 'Rei', 'Valete']
random.shuffle(cartas)
print(cartas)
```
um detalhe do shuffle é que ele não retorna nada, ao contrário das outras funções que retornavam um inteiro, uma lista, ou item. Shuffle vai simplesmente embaralhar a lista que foi dada, então, ao invés de retornar uma nova lista embaralhada, ele vai simplesmente modificar a lista que foi passada como argumento.

## Slide 6 - sys
sys é uma biblioteca padrão que fornece acesso a diversas funcionalidades e recursos do sistema:

    argumentos em linha de comando
    encerramento do programa
    
### Slide 7 - sys functions
#### sys.argv
esse sys.argv se refere a uma variável que vai ser atualizada toda vez que o programa for executado.

argv significa "vetor de argumentos", essa é uma variável que vai conter os argumentos inseridos na linha de comando quando a gente executa o programa.

`por que usar essa forma de entrada?`

`python nome.py ...`

vamos reutilizar aquele código da primeira aula que cumprimentava o usuário, só que dessa vez, ao invés de usar input() pra entrada de dados, a gente vai usar os argumentos na linha de comando.
```py
import sys

print(f"oi, {sys.argv[1]}, tudo bem?")
```
`Entrada: python args.py Hugo`

talvez você esteja se perguntando "por que sys.argv[1] é o que contém o primeiro argumento digitado?", "o que tem no índice 0?".

no índice 0 gente tem o caminho do script.

```py
import sys

print(f"oi, {sys.argv[0]}, tudo bem?")
```
`Saída: oi, args.py, tudo bem?`

com isso fora do caminho, voltando no programa funcional, como a gente faria pra incluir o nome e sobrenome de uma pessoa?

se a gente colocar espaços, os dois vão ser atribuídos a índices diferentes.

```py
import sys

print(f"oi, {sys.argv[1]}, tudo bem?")
```
`Entrada: python args.py Hugo Messias`
`Saída: oi, Hugo, tudo bem?`

a solução é usar aspas pra delimitar um argumento que inclui espaços:
```py
import sys

print(f"oi, {sys.argv[1]}, tudo bem?")
```
`Entrada: python args.py "Hugo Messias"`
`Saída: oi, Hugo Messias, tudo bem?`


mas ainda tem um pequeno detalhe com a forma com que a gente implementou isso. Aqui no print, a gente sempre checa o conteúdo no índice 1 do sys.argv. Olha o que acontece se eu não colocar nenhum argumento:
`Entrada: python args.py`
`Saída: IndexError: list index out of range`
vai ser exibido um erro. E esse é um erro bem inocenete de se cometer, se você enviar esse programa a uma outra pessoa, essa pessoa pode não saber que deve inserir um argumento e executar esperando um input, ao invés disso ela vai receber esse erro que, pra quem nunca mexeu na biblioteca sys, não é nada intuitivo.

O certo a se fazer é analisar esses argumentos antes do programa começar de fato, para garantir que a quantidade de argumentos é válida.

Pra conseguir isso, a gente pode fazer o seguinte
`if len()...`
#### len()
len é abreviação de legth, que significa "tamanho", em inglês. É uma função que vai retornar um valor inteiro referente ao tamanho do item entre os parêntesis.

Se for uma lista, vai ser retornado a quantidade de itens, se for uma string, vai ser retornado a quantidade de caracteres, e assim por diante.

nesse caso, a gente vai usar len pra verificar se a quantidade certa de argumentos foi inserida:
#### sys.exit()
`explicar por que len() > 2`
```py
import sys


if len(sys.argv) < 2:
    sys.exit("O programa espera um argumento")

print(f"oi, {sys.argv[1]}, tudo bem?")
```
e dentro do bloco de código do if, a gente vai utilizar o outro caso de uso do sys mostrado no slide, o sys.exit().

esse vai servir para interromper o funcionamento do programa imediatamente (semelhante ao break, que interrompe um loop, o sys.exit() vai interromper o programa como um todo).

e dentro dos parentesis a gente pode colocar uma mensagem explicando o motivo do programa ter sido interrompido.


\
\
como nosso programa só trabalha com um único argumento, a gente pode criar também um limite superior, pra evitar aquele erro de anteriormente sobre a ausência de aspas.
```py
import sys


if len(sys.argv) < 2:
    sys.exit("O programa espera um argumento")
elif len(sys.argv) > 2:
    sys.exit("Argumentos demais! use aspas se quiser inserir \"nome e sobrenome\"")

print(f"oi, {sys.argv[1]}, tudo bem?")
```

# Slide 8 - Bibliotecas Externas (pacotes)
acontece que, apesar de vir com várias bibliotecas pré instaladas, é impossível que essas bibliotecas cubram absolutamente todo caso de uso da linguagem, é por isso que, além das bibliotecas padrão, a gente tem as bibliotecas externas ou pacotes, que são desenvolvidadas e disponibilizadas gratuitamente por membros da comunidade Python.

ao invés de criar uma implementação completamente nova do zero para algo que a gente provavelmente nem sequer entende ainda simplesmente porque não existe uma solução nas bibliotecas padrão, a gente pode simplesmente utilizar uma biblioteca externa com o código que alguém com conhecimento no assunto desenvolveu justamente para nos ajudar nesses momentos.

### PyPI
e um dos lugares em que a gente vai ecessar esses pacotes é no Python Package Index, ou Índice de Pacotes Python.

esse é um repositório com todo tipo de biblioteca desenvolvido para todo tipo de uso. É lugar padrão para se encontrar pacotes em Python.

mas ao invés de ir no site baixar e configurar as bibliotecas manualmente, a gente vai usar uma ferramenta pra isso.

### pip
o pip é uma ferramenta que é instalada junto ao Python quando a gente executa o instalador.

essa ferramenta vai fazer todo o trabalho chato de encontrar a biblioteca, baixar, colocar em uma pasta em que ele fique acessível ao Python e configurar tudo, pra que tudo funcione com uma extrema facilidade.

sem precisar bater cabeça com linker, ou compilar a biblioteca do zero.

antes de mostrar um uso do pip, vamos introduzir a primeira biblioteca externa que a gente vai comentar hoje.

### API
mas antes de ver a biblioteca em si, a gente precisa entender o conceito de API

interface de desenvovimento de aplicações

permite acessar serviços de terceito por meio de código. 

Permite o nosso código se comunique com um serviço de um terceiro.

a gente pode usar como exemplo pra entender esses conceito a API do chatGPT, que consiste basicamente de uma interface que vai levar uma mensagem do nosso código para os computadores da OpenAI, processar uma resposta, e retornar essa resposta para o nosso código, para a gente usar como a gente desejar.

hoje em dia, a esmagadora maioria das APIs é acessível pela internet, como essa do chatGPT, que eu usei de exemplo, basta ter um navegador para a acessar, ou, no nosso caso, um código que aja como um navegador para acessar essa API.

## Slide 12 - requests
é aí que entra a nossa primeira biblioteca externa, a requests, que permite que a gente faça essas requisições web, dentro do Python, como se a gente tivesse acessando por um navegador.

#### instalar a biblioteca
agora que a gente tem o nome do módulo que a gente quer instalar, vamo ver como usar o pip.

`pip install requests`


#### mostrar a API no navegador
bom, antes de partir pro exemplo, pra esse exemplo a gente vai usar a API do Itunes, que é a plataforma de música da Apple. A gente vai usar essa API porque ela é bem simples de ser utilizada, é algo bom para introduzir esse conceito.

como eu falei anteriormente, a maioria das APIs hoje em dia são acessíveis via internet por meio de um navegador, então vamos começar vendo esse acesso em um navegador.

URL: `https://itunes.apple.com/search?entity=song&limit=1&term=cream`

`falar do resultado ser um arquivo de texto, não uma página`
```
pode parecer meio bagunçado, mas segue um padrão (JSON)
  -chaves cercando tudo
  -colchetes no segundo item
  -várias strings e números
  -pares de chaves e valores (como em dicionários)
```

#### JSON
esse padrão é o JSON, ou JavaScript Object Notation, que, apesar de ter JavaScript no nome, é um tipo de agrupagem de dados comum em qualquer linguagem.

como a gente pode ver aqui, isso não passa de texto não formatado organizado de uma forma facilmente legível por um programa.

vamo ver como a gente vai usar isso no python.

`começar com requests.get()`

`atrubuir o resultado a 'resposta'`

`falar do response.json() (vai se tratado como um dicionário, não mais só texto)`
```py
import requests

resposta = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=cream")
print(resposta.json())
```

o código tá praticamente ilegível, a gente tem algumas formas de organizar essa saída em python.

#### pprint
vamos começar vendo uma mais geral que serve pra qualquer estrutura de dados python e, como resposta tá sendo interpretada como dicionário, se aplica aqui também.
```py
import requests
import pprint

resposta = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=cream")
# print(resposta.json())

pprint.pprint(resposta.json())
```

nesse caso, como a única coisa que a gente quer dessa biblioteca é a função pprint, a gente pode usar:
```py
import requests
from pprint import pprint

resposta = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=cream")
pprint(resposta.json())
```

#### json
mas como a gente tá lidando com um arquivo json aqui, o ideal seria usar a biblioteca json, que oferece várias formas de manipular arquivos json, incluindo uma forma de printar um json formatado.

`substituir pprint por json`
```py
import requests
import json

resposta = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=cream")
print(json.dumps(response.json(), indent=2))
```

#### analisar o json no terminal
```py
{ # <== indica que é um dicionário
  "resultCount": 1, # quantidade de resultados
  "results": [ ### <== lista contendo os resultado (é perceitamente aceitável ter listas dentro de dicionários)
    { # <== dicionário com o primeiro resultado (nesse caso, o único)
      "wrapperType": "track",
      "kind": "song",
      "artistId": 200986,
      "collectionId": 1130045243,
...
```
antes de analisar o resultado, vamos decidir um propósito pro nosso programa, tudo que ele faz até o momento é mostrar a resposta da mesma requisição na tela, o que não é lá essas coisas. Ao invés disso, vamos adaptar esse programa pra filtrar esse resultado pra mostrar apenas as informações relevantes, digamos que apenas o nome do artista e o nome da música.

vamos começar analisando esse json pra entender como conseguir esses dados:
```py
...
"wrapperType": "track",
      "kind": "song",
      "artistId": 200986,
      "collectionId": 1130045243,
      "trackId": 1130045662,
      "artistName": "Wu-Tang Clan", # <== artista
      "collectionName": "21 Throwback Jams",
      "trackName": "C.R.E.A.M.", # <== música
      "collectionCensoredName": "21 Throwback Jams",
      "trackCensoredName": "C.R.E.A.M.",
...
```

ok, a gente quer esses dois, vamos começar pegando o artista, pra depois a gente aplicar a mesma lógica à música.

vamos fazer o caminho reverso 
1. álbum está na chave "artistName",
2. essa chave está no primeiro dicionário nessa lista
3. essa lista é o valor da chave results
4. essa chave results é uma das chaves do primeiro dicionário

seguindo esse caminho, a gente tem que resposta['results'] vai conter uma lista de resultados, e em cada um desses resultados, collectionName e trackName vão conter as informações que a gente quer. Como o conteúdo de resposta['results'] é uma lista, a gente pode usar o for para iterar sobre ela e mostrar todos os resultados:

`colocar json() depois de requests.get()`
```py
import requests
import json

resposta = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=cream").json()

for result in resposta['results']:
    print(f"{result['artistName']} - {result['trackName']}")
```

executando, a gente vai ver apenas o nome do álbum e o nome da música

a gente pode vir aqui e aumentar esses resultados
```py
# AUMENTAR "limit=10"
resposta = requests.get("https://itunes.apple.com/search?entity=song&limit=10&term=cream").json()
```


a gente pode melhorar esse programa ainda mais usando sys.argv pra pegar uma entrada do usuário

```py
import requests
import json
import sys

if len(sys.argv) != 2:
     sys.exit()

resposta = requests.get(f"https://itunes.apple.com/search?entity=song&limit=10&term={sys.argv[1]}").json()

for result in resposta['results']:
    print(f"{result['artistName']} - {result['trackName']}")
```
\
\
\
\
\
\
\
\
# Bibliotecas pessoais
`oi.py`
```py
def oi(nome):
    return f"oi, {nome}, tudo bem?"

oi("teste")
```

`main.py`
```py
import oi

oi.oi("Hugo")
```
\
\
\
`oi.py`
```py
def oi(nome):
    return f"oi, {nome}, tudo bem?"

if __name__ == "__main__":
     oi("teste")
```
