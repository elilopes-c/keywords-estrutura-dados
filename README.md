## ESTRUTURAS DE DADOS:

## * `list`: Usada para criar e manipular listas.
_Imagine uma lista como uma "caixa organizadora" onde você pode guardar vários itens em uma ordem específica. Diferente de uma caixa onde tudo se mistura, na lista você sabe exatamente onde cada item está (pela sua posição, que chamamos de índice). O mais legal é que você pode adicionar, remover e até trocar itens depois de a caixa estar pronta, e pode guardar itens de diferentes tipos (números, textos, outros objetos, etc.) na mesma caixa!_

As listas são coleções ordenadas, mutáveis e que permitem itens duplicados. São definidas usando colchetes `[]`.

**Características Principais:**
    - **Ordenada:** Os itens possuem uma ordem definida, e essa ordem não muda a menos que a lista seja modificada.
    - **Mutável:** Você pode adicionar, remover ou modificar itens após a criação da lista.
    - **Indexada:** Cada item tem um índice (posição) numérico, começando do 0 para o primeiro item.
    - **Permite Duplicatas:** Você pode ter o mesmo valor várias vezes na mesma lista.
    - **Versátil:** Pode armazenar itens de diferentes tipos de dados.

**Sintaxe:**
    ```python
    minha_lista = [item1, item2, item3, ...]
    ```

**Exemplos:**

```python
    # Criando listas
    numeros = [1, 2, 3, 4, 5]
    frutas = ["maçã", "banana", "cereja"]
    mista = [10, "Python", True, 3.14]
    lista_vazia = []

    print(f"Lista de números: {numeros}")
    # Saída: Lista de números: [1, 2, 3, 4, 5]
    print(f"Lista de frutas: {frutas}")
    # Saída: Lista de frutas: ['maçã', 'banana', 'cereja']
    print(f"Lista mista: {mista}")
    # Saída: Lista mista: [10, 'Python', True, 3.14]

    # Acessando itens (por índice)
    print(f"Primeiro número: {numeros[0]}")
    # Saída: Primeiro número: 1
    print(f"Última fruta (índice negativo): {frutas[-1]}")
    # Saída: Última fruta (índice negativo): cereja

    # Fatiamento (slicing) de listas - Funciona como fatiamento de strings!
    print(f"Primeiras duas frutas: {frutas[0:2]}")
    # Saída: Primeiras duas frutas: ['maçã', 'banana']
    print(f"Números do segundo ao quarto: {numeros[1:4]}")
    # Saída: Números do segundo ao quarto: [2, 3, 4]

    # Modificando itens
    frutas[1] = "laranja" # Altera a "banana" para "laranja"
    print(f"Frutas após modificação: {frutas}")
    # Saída: Frutas após modificação: ['maçã', 'laranja', 'cereja']

    # Adicionando itens
    frutas.append("uva") # Adiciona "uva" ao final
    print(f"Frutas após append: {frutas}")
    # Saída: Frutas após append: ['maçã', 'laranja', 'cereja', 'uva']

    frutas.insert(1, "kiwi") # Insere "kiwi" no índice 1
    print(f"Frutas após insert: {frutas}")
    # Saída: Frutas após insert: ['maçã', 'kiwi', 'laranja', 'cereja', 'uva']

    # Removendo itens
    frutas.remove("laranja") # Remove a primeira ocorrência de "laranja"
    print(f"Frutas após remove: {frutas}")
    # Saída: Frutas após remove: ['maçã', 'kiwi', 'cereja', 'uva']

    item_removido = frutas.pop(0) # Remove e retorna o item do índice 0 ("maçã")
    print(f"Item removido com pop: {item_removido}")
    # Saída: Item removido com pop: maçã
    print(f"Frutas após pop: {frutas}")
    # Saída: Frutas após pop: ['kiwi', 'cereja', 'uva']

    # Verificando o tamanho da lista
    print(f"Número de frutas na lista: {len(frutas)}")
    # Saída: Número de frutas na lista: 3

    # Iterando sobre uma lista (usando o for, que será explicado em breve!)
    print("\nMinhas frutas favoritas:")
    for fruta in frutas:
        print(f"- {fruta}")
    # Saída:
    # Minhas frutas favoritas:
    # - kiwi
    # - cereja
    # - uva
``` 

## * `List Comprehension` (Compreensão de Listas)
_Pense na Compreensão de Listas como uma "máquina de fazer listas personalizadas" super eficiente e compacta! Em vez de usar um laço `for` longo com um `if` para criar uma nova lista, você pode fazer tudo em uma única linha, de um jeito muito mais elegante._

_É como se você dissesse ao Python: "Ei, pegue cada item desta lista antiga, faça algo com ele (talvez filtre alguns ou transforme outros) e me dê uma nova lista com os resultados."_

**Estrutura básica:**

```
nova_lista = [expressao for item in iteravel if condicao]
```

- `expressao`: É o que você quer fazer com cada `item` (ex: `item`, `item * 2`, `item.upper()`).
- `item`: Uma variável temporária que representa cada elemento do `iteravel`.
- `iteravel`: A lista ou outra coleção que você está percorrendo (ex: `numeros`, `minha_lista_de_nomes`).
- `if condicao` (opcional): Uma condição para **filtrar** os itens. Se a condição for `True`, o `item` é incluído na nova lista (após a `expressao`). Se for `False`, ele é ignorado.

## * Filtro com Compreensão de Listas

_Imagine que você tem uma cesta de frutas e quer separar apenas as maçãs. A Compreensão de Listas com filtro faz exatamente isso: ela percorre sua lista original e seleciona apenas os itens que atendem a um critério específico, criando uma nova lista só com eles._

**Exemplos:**

### **Versão 1 (Tradicional com `for` e `if`):**
Esta é a forma "passo a passo", onde você cria uma lista vazia, percorre a original e adiciona os itens se eles satisfizerem a condição.

```
numeros = [1, 30, 21, 2, 9, 65, 34]
pares = [] # Começa com uma cesta vazia para os números pares

for numero in numeros: # Para cada número na lista 'numeros':
    if numero % 2 == 0: # Se o número for divisível por 2 (ou seja, for par):
        pares.append(numero) # Adicione esse número par à sua cesta 'pares'

print(pares) # Saída: [30, 2, 34]

```


### **Versão 2 (Compreensão de Lista para Filtro):**
Esta é a forma "mágica" e compacta, fazendo o mesmo que a versão 1 em uma única linha.

```
numeros = [1, 30, 21, 2, 9, 65, 34]
# Filtra: "Para cada número na lista 'numeros', se o número for par, inclua-o na nova lista 'pares'"
pares = [numero for numero in numeros if numero % 2 == 0] 

print(pares) # Saída: [30, 2, 34]
```

## * `Modificação (ou Mapeamento) com Compreensão de Listas`

_Agora, imagine que você tem um conjunto de ingredientes e quer transformá-los em algo novo, como transformar farinha em bolo, ou multiplicar todos os seus números por 2. A Compreensão de Listas para modificação faz exatamente isso: ela percorre sua lista original, aplica uma transformação em cada item e coleta os resultados em uma nova lista._

**Exemplo:**

```
numeros = [1, 30, 21, 2, 9, 65, 34]
# Modifica: "Para cada número na lista 'numeros', calcule o quadrado desse número e inclua-o na nova lista 'quadrado'"
quadrado = [numero ** 2 for numero in numeros] 

print(quadrado) # Saída: [1, 900, 441, 4, 81, 4225, 1156]
```

## * Métodos da Classe List
_Imagine que sua lista é como uma "caixa mágica" que pode guardar um monte de coisas em uma ordem específica. Os métodos são como "botões" ou "comandos especiais" nessa caixa que permitem que você faça diversas ações com os itens que estão dentro dela: adicionar, remover, contar, organizar, e muito mais!_

## * .append()
_Pense no `.append()` como a ação de **colocar um novo item no final da sua caixa mágica**. 
É a forma mais simples de adicionar algo, sempre lá na última posição disponível._

**Exemplo:**
```python
    lista = [] # Sua caixa mágica está vazia
    lista.append(1) # Você adiciona o número 1
    lista.append("Python") # Depois, adiciona a palavra "Python"
    lista.append([40, 30, 20]) # E por último, adiciona uma caixinha menor com três números!
    
    print(lista) # Saída: [1, 'Python', [40, 30, 20]]
```

## * .clear()
_O `.clear()` é como **virar sua caixa mágica de cabeça para baixo e esvaziar tudo o que tem dentro dela**. 
A caixa continua existindo, mas agora está completamente vazia, pronta para novos itens._

**Exemplo:**
```
lista = [1, "Python", 40, 30, 20] # Sua caixa mágica com alguns itens
lista.clear() # Virando a caixa e esvaziando tudo

print(lista) # Saída: []
```

## * .copy()
_O `.copy()` é como **fazer uma fotocópia exata da sua caixa mágica**. 
Você terá uma nova caixa idêntica, mas ela é independente da original. Se você mudar algo em uma, a outra não será afetada._

**Exemplo:**
```
lista = [1, "Python", 40, 30, 20] # Sua caixa mágica original
copia_lista = lista.copy() # Criando uma fotocópia

print(copia_lista) # Saída: [1, 'Python', 40, 30, 20]
```

## * .count()
_O `.count()` é como **perguntar à sua caixa mágica: "Quantas vezes este item específico aparece aqui dentro?"** Ela te dará a contagem exata._

**Exemplo:**
```
cores = ["vermelho", "azul", "verde", "azul"] # Sua caixa mágica com cores
print(cores.count("vermelho")) # Quantos "vermelho"? Saída: 1
print(cores.count("azul"))    # Quantos "azul"? Saída: 2
print(cores.count("verde"))   # Quantos "verde"? Saída: 1
```
## * .extend()
_O `.extend()` é como **pegar todos os itens de outra caixa mágica e adicioná-los um por um ao final da sua caixa atual**. 
É diferente de `.append()` que adicionaria a *outra caixa inteira* como um único item; aqui, você adiciona os *itens da outra caixa*._

**Exemplo:**
```
linguagens = ["python", "js", "c"] # Sua caixa de linguagens
linguagens.extend(["java", "csharp"]) # Adicionando os itens de outra lista um a um

print(linguagens) # Saída: ['python', 'js', 'c', 'java', 'csharp']
```

## * .index()
_O `.index()` é como **perguntar à sua caixa mágica: "Onde está a primeira ocorrência deste item?"** Ela te dirá a posição (o "endereço") da primeira vez que encontrar o item. 
Lembre-se que em Python, as posições começam do 0._

**Exemplo:**
```
linguagens = ["python", "js", "c", "java", "csharp"] # Sua caixa de linguagens
print(linguagens.index("python")) # Onde está "python"? Saída: 0 (primeira posição)
print(linguagens.index("java"))   # Onde está "java"? Saída: 3
```

## * .pop()
_O `.pop()` é como **retirar o último item da sua caixa mágica e te entregar ele de volta**. Você também pode especificar qual item deseja retirar pela sua posição, e ele te entregará esse item._

**Exemplo:**
```
linguagens = ["python", "js", "c"] # Sua caixa de linguagens
print(linguagens.pop())   # Tira e me dá o último. Saída: 'c'
print(linguagens.pop())   # Tira e me dá o último. Saída: 'js'
print(linguagens.pop())   # Tira e me dá o último. Saída: 'python'
print(linguagens.pop(0))  # Tira e me dá o item na posição 0 (se ainda houver)
```

## * .remove()
_O `.remove()` é como **dizer à sua caixa mágica: "Remova a primeira ocorrência deste item que você encontrar!"** 
Diferente do `.pop()`, você diz o *valor* do item, não a posição, e ele não te entrega o item de volta, apenas o remove._

**Exemplo:**
```
linguagens = ["python", "js", "c", "java", "csharp"] # Sua caixa de linguagens
linguagens.remove("c") # Remova a primeira ocorrência de "c"

print(linguagens) # Saída: ['python', 'js', 'java', 'csharp']
```

## * .reverse()
_O `.reverse()` é como **sacudir sua caixa mágica para que todos os itens fiquem na ordem inversa**. O primeiro vira o último, o segundo vira o penúltimo, e assim por diante._

**Exemplo:**
```
linguagens = ["python", "js", "c", "java", "csharp"] # Sua caixa de linguagens
linguagens.reverse() # Invertendo a ordem

print(linguagens) # Saída: ['csharp', 'java', 'c', 'js', 'python']
```

## * .sort()
_O `.sort()` é como **organizar os itens da sua caixa mágica em uma ordem específica (alfabética para textos, numérica para números)**. Ele altera a própria caixa, não cria uma nova._

**Exemplo:**
```
linguagens = ["python", "js", "c", "java", "csharp"] # Sua caixa de linguagens
linguagens.sort() # Organizando em ordem alfabética

print(linguagens) # Saída: ['c', 'csharp', 'java', 'js', 'python']

# Você também pode inverter a ordem (decrescente ou Z-A)
linguagens.sort(reverse=True)
print(linguagens) # Saída: ['python', 'js', 'java', 'csharp', 'c']

# Ou ordenar por um critério específico, como o tamanho das palavras
linguagens.sort(key=lambda x: len(x)) # Ordena pelo tamanho (menor para maior)
print(linguagens) # Saída: ['c', 'js', 'java', 'python', 'csharp']

linguagens.sort(key=lambda x: len(x), reverse=True) # Ordena pelo tamanho (maior para menor)
print(linguagens) # Saída: ['python', 'csharp', 'java', 'js', 'c']
```

## * len() (Função não-método, mas útil para listas)
_Embora `len()` não seja um "botão" na sua caixa mágica (não é um método como os outros que vimos), é como **uma fita métrica que você usa para saber quantos itens no total estão dentro da sua caixa**._

**Exemplo:**
```
linguagens = ["python", "js", "c", "java", "csharp"] # Sua caixa de linguagens
print(len(linguagens)) # Quantos itens tem na caixa? Saída: 5
```

 ## * `Tuplas` (Coleções Imutáveis)
 _Imagine uma `tupla` como uma daquelas caixas organizadoras super especiais que, depois de montadas e preenchidas, **não podem mais ser modificadas**! Uma vez que você coloca algo dentro dela, aquilo fica lá, fixo e seguro. Elas são como listas, mas com um superpoder de **segurança** contra mudanças acidentais._

 São perfeitas para guardar informações que não devem mudar, tipo as coordenadas de um mapa, os dias da semana, ou as configurações iniciais de um programa. Elas garantem que, uma vez definidos, seus dados permanecerão exatamente como você os deixou.

 ### **Criando Tuplas**

 Criar uma tupla é como encher sua caixa organizadora. Você pode fazer isso de várias formas, seja colocando os itens entre parênteses ou até mesmo convertendo outras "caixas" (como textos ou listas) em tuplas.

 **Estrutura básica:**
```
 minha_tupla = (item1, item2, item3)
```

 **Exemplos:**

 #### **Tupla simples com parênteses:**

 _A forma mais comum, onde você lista os itens separados por vírgulas e envolve tudo em parênteses. É como colocar seus brinquedos um por um na caixa._

```
 # Uma tupla de frutas que você tem na geladeira
 frutas = ("laranja", "pera", "uva",)
 print(frutas) # Saída: ('laranja', 'pera', 'uva')
```

 #### **Tupla a partir de um texto:**

 _Você pode transformar cada letra de uma palavra em um item separado da tupla. É como pegar um colar de letras e separar cada uma delas._

```
 # Cada letra da palavra "python" vira um item da tupla
 letras = tuple("python")
 print(letras) # Saída: ('p', 'y', 't', 'h', 'o', 'n')
```

 #### **Tupla a partir de uma lista (ou outras coleções):**

 _Se você tem uma lista e quer que ela se torne "imutável" (protegida contra mudanças), pode convertê-la em uma tupla. É como selar uma lista de compras para que ninguém mude os itens._

``` 
# Uma lista de números que você quer proteger
 lista_de_numeros = [1, 2, 3, 4]
 numeros = tuple(lista_de_numeros)
 print(numeros) # Saída: (1, 2, 3, 4)
```

 #### **Tupla com um único item:**

 _**Atenção!** Se você tem apenas um item, precisa colocar uma vírgula depois dele, mesmo que não haja outro item. Senão, o Python não vai entender que é uma tupla! É como se a vírgula fosse o "sinal" de que a caixa é do tipo tupla, mesmo que só tenha um presente dentro._

```
 # Isso NÃO é uma tupla, é apenas uma string entre parênteses
 errado = ("Brasil")
 print(type(errado)) # Saída: <class 'str'>

 # Isso SIM é uma tupla com um único item
 pais = ("Brasil",)
 print(type(pais)) # Saída: <class 'tuple'>
```

 ---

 ## * `Métodos da Classe Tuple` (Super Poderes das Tuplas)

 _Mesmo que as tuplas sejam "caixas seladas" que você não pode mudar, você ainda pode inspecioná-las e obter informações sobre o que está dentro! Pense nesses métodos como ferramentas especiais para "espiar" e contar o que tem na sua tupla, sem nunca abrir ou alterar o conteúdo._

 ### **`len()` (Contando os Itens)**

 _A função `len()` é como um contador de itens. Ela te diz quantos "presentes" ou "objetos" você colocou na sua tupla. Super útil para saber o tamanho da sua coleção._

 **Exemplos:**

```
 # Uma tupla com diferentes linguagens de programação
 linguagens = ("python", "js", "c", "java", "csharp",)

 # Pergunte ao Python: "Quantos itens tem nesta tupla?"
 total_linguagens = len(linguagens)
 print(total_linguagens) # Saída: 5
```
 
### **`.index()` (Encontrando a Posição de um Item)**

 _O método `.index()` é como um detector de posição. Se você sabe o que está procurando, ele te diz em qual "prateleira" ou "posição" (lembre-se que Python começa a contar do 0!) aquele item específico está guardado dentro da tupla._

 **Exemplos:**

```
 # Uma tupla com linguagens de programação
 linguagens = ("python", "js", "c", "java", "csharp",)

 # Onde está a "java" nesta tupla?
 posicao_java = linguagens.index("java")
 print(posicao_java) # Saída: 3 (porque "java" está na quarta posição, que é o índice 3)

 # Onde está "python" nesta tupla?
 posicao_python = linguagens.index("python")
 print(posicao_python) # Saída: 0 (porque "python" é o primeiro item, no índice 0)
```


 ### **`.count()` (Contando Ocorrências de um Item)**

 _O método `.count()` é como um "fiscal de repetição". Ele te diz quantas vezes um determinado item aparece dentro da sua tupla. Perfeito para descobrir se você repetiu algum item sem querer, ou se há muitos de algo específico._

 **Exemplos:**

```
 # Uma tupla com uma lista de cores, algumas repetidas
 cores = ("vermelho", "azul", "verde", "azul",)

 # Quantas vezes "vermelho" aparece?
 contagem_vermelho = cores.count("vermelho")
 print(contagem_vermelho) # Saída: 1

 # Quantas vezes "azul" aparece?
 contagem_azul = cores.count("azul")
 print(contagem_azul) # Saída: 2

 # Quantas vezes "verde" aparece?
 contagem_verde = cores.count("verde")
 print(contagem_verde) # Saída: 1
```

 ## * `Set` (Conjuntos: Caixas de Itens Únicos e Desorganizados!)
 _Imagine um `set` como uma caixa mágica onde você só pode guardar **itens únicos** e a ordem deles não importa. Se você tentar colocar duas vezes o mesmo item, a caixa magicamente o ignorará e só guardará uma cópia. Além disso, os itens ficam "desorganizados" lá dentro, sem uma ordem fixa! É como uma lista de convidados para uma festa onde não importa a ordem de chegada, e ninguém pode ser convidado duas vezes._

 Sets são ótimos para remover duplicatas de listas, verificar a presença rápida de um item (pois a busca é muito eficiente), e para operações matemáticas de conjuntos, como união e interseção.

 ### **Criando Sets**

 Criar um set é como iniciar sua caixa de itens únicos. Você pode fazer isso usando chaves `{}` ou a função `set()`.

 **Estrutura básica:**

 ```python
 meu_set = {item1, item2, item3}
 meu_set_vazio = set() # Importante: {} cria um dicionário vazio, não um set!
 meu_set_a_partir_de_lista = set([item1, item2])
 ```

 **Exemplos:**

 #### **Set simples com chaves `{}`:**

 _A forma mais comum para criar um set com itens. Se você colocar itens repetidos, o Python automaticamente os removerá, deixando apenas um de cada._

 ```python
 # Um set de cores, com uma cor repetida
 cores_favoritas = {"azul", "verde", "vermelho", "azul"}
 print(cores_favoritas) # Saída: {'azul', 'verde', 'vermelho'} (ordem pode variar)
 ```

 #### **Set a partir de um texto:**

 _Você pode transformar cada letra de uma palavra em um item separado do set. É como pegar um colar de letras e separar cada uma delas, mas sem repetições._

 ```python
 # Cada letra da palavra "banana" vira um item do set (apenas as únicas)
 letras = set("banana")
 print(letras) # Saída: {'a', 'b', 'n'} (ordem pode variar)
 ```

 #### **Set a partir de uma lista:**

 _Se você tem uma lista e quer remover todos os itens duplicados rapidamente, convertê-la em um set é a maneira mais eficiente. É como selar uma lista de compras para que ninguém mude os itens._

 ```python
 # Uma lista com números repetidos
 numeros_repetidos = [1, 2, 2, 3, 4, 4, 5]
 # Convertendo a lista para um set para remover duplicatas
 numeros_unicos = set(numeros_repetidos)
 print(numeros_unicos) # Saída: {1, 2, 3, 4, 5} (ordem pode variar)
 ```

 #### **Set vazio:**

 _Lembre-se que `{}` cria um dicionário vazio. Para criar um set vazio, você precisa usar a função `set()`. É como pegar uma caixa nova, pronta para você colocar seus itens únicos._

 ```python
 # Isso cria um dicionário vazio
 dicionario_vazio = {}
 print(type(dicionario_vazio)) # Saída: <class 'dict'>

 # Isso cria um set vazio
 set_vazio = set()
 print(type(set_vazio)) # Saída: <class 'set'>
 ```

 ---

 ## * `Operações Comuns com Sets` (Interagindo com Suas Coleções Únicas)

 _Sets têm seus próprios "superpoderes" para adicionar, remover e verificar itens, além de operações matemáticas de conjuntos como união, interseção e diferença. Pense nelas como formas de manipular ou combinar suas caixas de itens únicos._

 ### **Adicionando itens: `.add()`**

 _Para colocar um novo item na sua caixa de "coisas únicas". Se o item já estiver lá, nada acontece._

 ```python
 # Um set de frutas
 frutas = {"maçã", "banana"}
 frutas.add("laranja") # Adiciona um novo item
 print(frutas) # Saída: {'maçã', 'banana', 'laranja'} (ordem pode variar)
 frutas.add("maçã") # Tenta adicionar um item que já existe
 print(frutas) # Saída: {'maçã', 'banana', 'laranja'} (continua o mesmo)
 ```

 ### **Removendo itens: `.remove()` e `.discard()`**

 _Duas formas de tirar um item da sua caixa. `.remove()` avisa com um erro se o item não estiver lá (KeyError), enquanto `.discard()` remove sem reclamar, mesmo que o item não esteja presente._

 ```python
 # Um set de números
 numeros = {1, 2, 3, 4}
 numeros.remove(3) # Remove o número 3
 print(numeros) # Saída: {1, 2, 4}

 # numeros.remove(5) # Isso causaria um erro (KeyError), pois 5 não está no set

 numeros.discard(2) # Remove o número 2
 print(numeros) # Saída: {1, 4}
 numeros.discard(5) # Não faz nada, sem erro, pois 5 não está no set
 print(numeros) # Saída: {1, 4}
 ```

 ### **Verificando a existência: `in`**

 _Para saber se um item está presente na sua caixa. É como perguntar: "Este item está nesta coleção?"_

 ```python
 # Um set de animais
 animais = {"cachorro", "gato", "pássaro"}
 print("gato" in animais) # Saída: True
 print("peixe" in animais) # Saída: False
 ```

 ### **Operações de Conjunto (União, Interseção, Diferença, Diferença Simétrica)**

 _Sets são ideais para simular operações matemáticas de conjuntos, que são muito úteis em análise de dados e lógica._

 #### **União (`|` ou `.union()`):**

 _Junta os itens de dois sets, removendo duplicatas. É como combinar o conteúdo de duas caixas de "coisas únicas" em uma só._

 ```python
 set_a = {1, 2, 3}
 set_b = {3, 4, 5}

 # Usando o operador |
 uniao_set = set_a | set_b
 print(uniao_set) # Saída: {1, 2, 3, 4, 5} (ordem pode variar)

 # Usando o método .union()
 uniao_set_metodo = set_a.union(set_b)
 print(uniao_set_metodo) # Saída: {1, 2, 3, 4, 5} (ordem pode variar)
 ```

 #### **Interseção (`&` ou `.intersection()`):**

 _Encontra os itens que estão presentes em **ambos** os sets. É como ver quais itens são comuns às duas caixas._

 ```python
 set_a = {1, 2, 3}
 set_b = {3, 4, 5}

 # Usando o operador &
 intersecao_set = set_a & set_b
 print(intersecao_set) # Saída: {3}

 # Usando o método .intersection()
 intersecao_set_metodo = set_a.intersection(set_b)
 print(intersecao_set_metodo) # Saída: {3}
 ```

 #### **Diferença (`-` ou `.difference()`):**

 _Encontra os itens que estão no primeiro set, mas **não** no segundo. É como "o que eu tenho que você não tem?"_

 ```python
 set_a = {1, 2, 3}
 set_b = {3, 4, 5}

 # Usando o operador -
 diferenca_set = set_a - set_b
 print(diferenca_set) # Saída: {1, 2}

 # Usando o método .difference()
 diferenca_set_metodo = set_a.difference(set_b)
 print(diferenca_set_metodo) # Saída: {1, 2}
 ```

 #### **Diferença Simétrica (`^` ou `.symmetric_difference()`):**

 _Encontra os itens que estão em um dos sets, mas **não em ambos**. É como "o que só você tem ou o que só eu tenho?"_

 ```python
 set_a = {1, 2, 3}
 set_b = {3, 4, 5}

 # Usando o operador ^
 diferenca_simetrica_set = set_a ^ set_b
 print(diferenca_simetrica_set) # Saída: {1, 2, 4, 5} (ordem pode variar)

 # Usando o método .symmetric_difference()
 diferenca_simetrica_set_metodo = set_a.symmetric_difference(set_b)
 print(diferenca_simetrica_set_metodo) # Saída: {1, 2, 4, 5} (ordem pode variar)
 ```
