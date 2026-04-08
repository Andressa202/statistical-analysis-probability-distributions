### Variáveis contínuas e discretas



Lembre-se de que uma variável quantitativa (às vezes chamada de "variável numérica") pega valores numéricos de um intervalo (por exemplo, 1, 2, 3.78, -100.5), enquanto uma variável categórica (às vezes chamada de "variável qualitativa") pega valores de um conjunto limitado de valores não numéricos.





**Variáveis contínuas** assumem valores numéricos a qualquer nível de precisão. Isso significa que, por exemplo, tempo de espera (que pode ser medido em horas, minutos, segundos – por exemplo, 2,5 minutos) ou peso (quilos, gramas – por exemplo, 4.275 kg) são exemplos de variáveis contínuas, já que esses valores podem ser medidos em uma escala contínua.



Em contraste, **variáveis discretas** só podem ser medidas em números inteiros sem unidades menores. Por exemplo, não podemos ter 4,25 pítons ou 2,4 olhos em um gato. Essas medidas precisam ser variáveis discretas.



Para concluir, variáveis discretas assumem números com um degrau exato entre os valores. Agora vamos praticar!



#### Histogramas de frequência



Então: como criamos um histograma para variáveis contínuas? Uma ideia que faz sentido é dividir o intervalo de possíveis valores em intervalos e então contar o número de vezes que os valores aparecem em cada um.

Ao criar um histograma, podemos ajustar o número de barras usadas especificando o parâmetro bins=. Por exemplo, definir bins=4 cria 4 barras, o que funciona bem para variáveis discretas. No entanto, para variáveis contínuas, precisamos passar uma lista com os limites dos intervalos, e não um único número inteiro, como 4.

Compare os dois histogramas abaixo. O azul foi criado com o parâmetro bins= definido em 4, enquanto o laranja foi construído com uma lista com os limites dos intervalos:



**import pandas as pd**



**data = pd.Series(\[11, 20, 22, 31, 32, 33, 41, 42, 43, 44, 51, 52, 53, 54, 55, 61, 62, 63, 64, 65, 66, 71, 72, 73, 74, 75, 76, 77, 81, 82, 83, 84, 85, 86, 87, 88, 91, 92, 93, 94, 95, 96, 97, 98, 99])**



**data.hist(bins=4, alpha=0.5)**  # constrói um histograma com quatro barras



**data.hist(**

&nbsp;   \*\*bins=\\\[11, 20, 30, 40, 50, 60, 70, 80, 90, 99], alpha=0.7\*\*


**)**  # constrói um histograma com nove barras, cujos limites estão listados, e com um argumento alpha que gera um gráfico opaco



#### Histogramas de densidade





Vamos dar uma olhadinha na barra da imagem 'histograma\_calculo\_de\_area' e fazer algumas anotações:



* A primeira barra tem uma largura de 2 (de 2 a 4) e uma frequência de 3.
* A segunda barra tem uma largura de 4 (de 4 a 8) e uma frequência de 6.
* A última barra tem uma largura de 2 (de 8 a 10) e uma frequência de 4.



Vamos calcular as áreas das barras e compará-las. Para refrescar a memória, a área de um retângulo é a largura multiplicada pela altura, então:



* A área da primeira barra é 2 x 3 = 6
* A área da segunda barra é 4 x 6 = 24
* A área da terceira barra é 2 x 4 = 8



Embora a barra tenha uma frequência apenas duas vezes maior do que a primeira (6 vs 3), a área dela é quatro vezes maior (24 vs 6). Como podemos lidar com diferenças nos tamanhos das áreas ao comparar frequências que caem em barras diferentes?



Uma abordagem alternativa seria exibir densidades de frequência em vez de frequências. Mas o que são densidades de frequência e como podemos mudar de frequências normais para elas? Vamos explorar esse conceito agora.



Para calcular a densidade de uma frequência, divida a frequência (a altura de uma barra) pela largura da barra :



* A primeira barra tem uma densidade de frequência de 1,5 (3 dividido por 2).
* A segunda barra tem uma densidade de frequência de 1,5 (6 dividido por 4).
* A terceira barra tem uma densidade de frequência de 2 (4 dividido por 2).

Vamos reconstruir o gráfico, mas, desta vez, o eixo Y vai exibir a densidade de frequência, não a frequência normal (IMAGEM: 'densidade\_de\_frequencia':



Um histograma que exibe densidades de frequência em vez de frequências, conforme descrito, é chamado de histograma de densidade.



Agora vamos calcular as áreas das barras no histograma de densidade que acabamos de construir:



* A área da primeira barra é 2 x 1,5 = 3
* A área da segunda barra é 4 x 1,5 = 6
* A área da terceira barra é 2 x 2 = 4



Os histogramas de densidade, assim como histogramas normais, também são usados para exibir a distribuição de frequência. Essas áreas representam as diferenças reais entre as frequências. Precisamente, cada área representa uma frequência. Quanto maior a área da barra, mais alta é a frequência. Essa é uma maneira alternativa para visualizar frequências.

