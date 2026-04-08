### Como prever o futuro?



##### A fórmula principal



Quando você joga um dado, todos os resultados possíveis têm a mesma probabilidade de ocorrer. Já que há seis resultados possíveis e cada um deles é igualmente provável, a probabilidade de cada resultado é 1/6.



Na estatística, usamos a letra **P** para denotar a probabilidade e a letra **A** para denotar um evento de interesse. Portanto, a notação **P(A)** descreve a probabilidade do evento **A**.



A probabilidade **P(A)** pode ser calculada da seguinte maneira:



\# de resultados que satisfaçam o evento sobre / # do total de resultados

​

​Se o evento **A** for definido como "conseguir um número igual ou maior do que 5", então **P(A)** é (**1 + 1) / 6 = 1/3.**





Muitos outros cenários possuem essa propriedade. Por exemplo, ao tirar uma carta aleatoriamente de um baralho de 52 cartas, todas as cartas têm a mesma possibilidade de serem tiradas. Se o evento A for definido como "tirar um oito de copas" (ou alguma outra carta específica), então a probabilidade P(A) será 1/52.



Podemos generalizar esse cenário. Se…



* um experimento é executado uma vez,
* a probabilidade de cada resultado é a mesma e
* existem n resultados possíveis,



então a probabilidade de ocorrência de cada um dos resultados é 1/n.



Isso revela uma propriedade crucial da probabilidade: a soma das probabilidades de todos os resultados possíveis em um experimento deve ser igual a 100% ou 1. Isso garante que um dos resultados possíveis vai ocorrer.



Ao jogar um dado, há seis resultados possíveis, e cada um possui uma probabilidade de 1/6. A soma dessas probabilidades é **1/6 + 1/6 + 1/6 + 1/6 + 1/6 + 1/6 = 1**. Assim, temos uma garantia de que o resultado do dado vai ser **1, 2, 3, 4, 5** ou **6**.



#### Eventos e espaços amostrais



O conjunto de todos os resultados possíveis de um experimento é chamado de espaço amostral e costuma ser representado como S.



Para ilustrar, considere o exemplo de jogar um dado uma vez. O espaço amostral associado a esse evento é o seguinte:



##### S={1,2,3,4,5,6}





**Pergunta**

Vamos voltar para o exemplo com bilhetes de rifa. Temos o mesmo conjunto que antes, mas os resultados mudaram. O bilhete #1 ganha $100, os bilhetes #2 e #3 ganham $10 cada, o bilhete 4 ganha outro bilhete da rifa e o resto dos bilhetes não são vencedores. Como fica S nessa situação?



**{#1 ($100), #2 ($10), #3 ($10), #4 (novo bilhtete), #5 (-), #6 (-), #7 (-), #8 (-), #9 (-), #10 (-)}**

Todos os bilhetes devem ser inclusos no espaço amostral.



Agora vamos jogar dois dados ao invés de um só. Este é o espaço amostral quando dois dados são jogados:

**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\espaco\_amostral\_quando\_dois\_dados\_sao\_jogados.png"**



O documento fala sobre o espaço amostral de jogar dois dados, onde cada par é o resultado do primeiro e do segundo dado. Ao adicionar apenas um dado, o espaço amostral cresce de 6 resultados para 36. Como cada dado é independente do outro, todos os 36 resultados têm a mesma chance de ocorrer. As probabilidades ainda podem ser calculadas da mesma maneira.



#### A lei dos grandes números



Ao estimar a probabilidade de um evento, podemos confiar em um teorema muito útil, a lei dos grandes números. Essa lei afirma que quanto mais vezes um experimento é repetido, mais próxima estará a frequência relativa de determinado evento (o número de vezes que o evento ocorre dividido pelo número de vezes que o experimento é repetido) de sua verdadeira probabilidade.



Por exemplo, já sabemos que, ao jogarmos uma moeda, a probabilidade de sair cara é de 50%. Entretanto, se não tivéssemos essa informação, poderíamos estimar a probabilidade jogando uma moeda muitas vezes e analisando o número de caras e o número de jogadas.



A lei dos grandes números afirma que conforme o número de jogadas se aproxima do infinito, a frequência relativa desse evento vai se aproximar da real probabilidade do evento.



As probabilidades de eventos complexos são estimadas fazendo experimentos muitas vezes e usando frequências relativas para estimar as probabilidades.



#### Probabilidades de espaço amostral em Python



Em Python, cálculos simples de probabilidades baseados em espaços amostrais como esses são feitos com facilidade usando o operador lógico **==** e a função **len()**.



* Usar **==** identifica as linhas que vão satisfazer o evento.
* **len()** fornece a contagem das linhas que satisfazem ao evento.



Aqui está um exemplo:



Você criou uma playlist no Spotify com duas colunas: **'Artist'** (artista) e **'Song'** (música).



**import pandas as pd**



**cool\_rock = pd.DataFrame(**

    \*\*{\*\*

&nbsp;       \\\*\\\*'Artist': \\\\\\\[\\\*\\\*

            \\\*\\\*'Queen',\\\*\\\*

            \\\*\\\*'Queen',\\\*\\\*

            \\\*\\\*'Queen',\\\*\\\*

            \\\*\\\*'Pink Floyd',\\\*\\\*

            \\\*\\\*'Nirvana',\\\*\\\*

            \\\*\\\*'AC/DC',\\\*\\\*

            \\\*\\\*'AC/DC',\\\*\\\*

            \\\*\\\*'Scorpions',\\\*\\\*

            \\\*\\\*'Scorpions',\\\*\\\*

            \\\*\\\*'Scorpions',\\\*\\\*

        \\\*\\\*],\\\*\\\*

        \\\*\\\*'Song': \\\\\\\[\\\*\\\*

            \\\*\\\*'The Show Must Go On',\\\*\\\*

            \\\*\\\*'Another One Bites The Dust',\\\*\\\*

            \\\*\\\*'We Will Rock You',\\\*\\\*

            \\\*\\\*'Wish You Were Here',\\\*\\\*

            \\\*\\\*'Smells Like Teen Spirit',\\\*\\\*

            \\\*\\\*'Highway To Hell',\\\*\\\*

            \\\*\\\*'Back in Black',\\\*\\\*

            \\\*\\\*'Wind Of Change',\\\*\\\*

            \\\*\\\*'Still Loving You',\\\*\\\*

            \\\*\\\*'Send Me An Angel',\\\*\\\*

        \\\*\\\*],\\\*\\\*

    \\\*\\\*}\\\*\\\*





**)**

**print(cool\_rock)**





result:

                \*\*Artist                        Song\*\*



**0       Queen         The Show Must Go On**

**1       Queen  Another One Bites The Dust**

**2       Queen            We Will Rock You**

**3  Pink Floyd          Wish You Were Here**

**4     Nirvana     Smells Like Teen Spirit**

**5       AC/DC             Highway To Hell**

**6       AC/DC               Back in Black**

**7   Scorpions              Wind Of Change**

**8   Scorpions            Still Loving You**

**9   Scorpions            Send Me An Angel**



Qual é a probabilidade de que a primeira música tocada seja **"Smells Like Teen Spirit"**?



Para identificar os resultados satisfatórios para esse evento, use == e use len() duas vezes: uma para calcular a quantidade de resultados que satisfazem o evento e outra para contar o tamanho do espaço amostral.



**print(**

\*\*len(cool\\\_rock\\\[cool\\\_rock\\\['Song'] == 'Smells Like Teen Spirit'])\*\*

\\\*\\\*/ len(cool\\\\\\\_rock)\\\*\\\*





**)**







result:

**0.1**



Após ativar o modo aleatório, você precisa calcular a probabilidade de que a primeira música seja da banda **'Queen'**. Escreva o código para esse cálculo.



**import pandas as pd**



**cool\_rock = pd.DataFrame(**

    \*\*{\*\*

&nbsp;       \\\*\\\*'Artist': \\\\\\\[\\\*\\\*

            \\\*\\\*'Queen',\\\*\\\*

            \\\*\\\*'Queen',\\\*\\\*

            \\\*\\\*'Queen',\\\*\\\*

            \\\*\\\*'Pink Floyd',\\\*\\\*

            \\\*\\\*'Nirvana',\\\*\\\*

            \\\*\\\*'AC/DC',\\\*\\\*

            \\\*\\\*'AC/DC',\\\*\\\*

            \\\*\\\*'Scorpions',\\\*\\\*

            \\\*\\\*'Scorpions',\\\*\\\*

            \\\*\\\*'Scorpions',\\\*\\\*

        \\\*\\\*],\\\*\\\*

        \\\*\\\*'Song': \\\\\\\[\\\*\\\*

            \\\*\\\*'The Show Must Go On',\\\*\\\*

            \\\*\\\*'Another One Bites The Dust',\\\*\\\*

            \\\*\\\*'We Will Rock You',\\\*\\\*

            \\\*\\\*'Wish You Were Here',\\\*\\\*

            \\\*\\\*'Smells Like Teen Spirit',\\\*\\\*

            \\\*\\\*'Highway To Hell',\\\*\\\*

            \\\*\\\*'Back in Black',\\\*\\\*

            \\\*\\\*'Wind Of Change',\\\*\\\*

            \\\*\\\*'Still Loving You',\\\*\\\*

            \\\*\\\*'Send Me An Angel',\\\*\\\*

        \\\*\\\*],\\\*\\\*

    \\\*\\\*}\\\*\\\*





**)**



**desired\_artist = 'Queen'**



**desired\_outcomes = len(cool\_rock\[cool\_rock\['Artist'] == desired\_artist])**

**total\_outcomes =len(cool\_rock)**

**probability = desired\_outcomes / total\_outcomes**



**print(probability)**



result:

**0.3**

