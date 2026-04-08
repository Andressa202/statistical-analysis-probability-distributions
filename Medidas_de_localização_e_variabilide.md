#### Medidas de localização



medianas e médias, são valores usados para descrever dados numéricos. Esses valores também são chamados de medidas de localização ou de posição.

Às vezes, a média também é chamada de medida algébrica de localização.



A mediana é uma medida de localização estrutural. Você pode mudar quase todos os valores do conjunto de dados, e ainda assim a mediana permanece a mesma. Como exemplo, vamos continuar trabalhando com o conjunto de dados do quiz e calcular a média e a mediana em Python.



**data = pd.Series(\[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10])**

**print('A média é', data.mean())**

**print('A mediana é', data.median())**



result:

**A média é 5.0**

**A mediana é 5.0**



Agora vamos ver como a média e a mediana são afetadas quando modificamos os dados. Primeiro, dividimos todos os valores estritamente menores do que 5 por 10 e multiplicamos todos os valores estritamente maiores do que 5 por 10 (o número 5 deve ser deixado como está). Vamos encontrar as novas mediana e média do conjunto de dados atualizado.



**data\_new = pd.Series(\[0, 0.1, 0.2, 0.3, 0.4, 5, 60, 70, 80, 90, 100])**

**print('A nova média é', data\_new.mean())**

**print('A nova mediana é', data\_new.median())**



result:

**A nova média é 36.90909090909091**

**A nova mediana é 5.0**



A média mudou, mas a mediana permaneceu a mesma.Além disso, se houver valores atípicos no conjunto de dados, será necessário usar a mediana, como você aprendeu no sprint de manipulação de dados. Tenha em mente que a média de um conjunto de dados contendo valores atípicos pode ser enganosa.



#### Medidas de variabilidade



Apenas as medidas de localização não são suficientes para compreender os dados. Você também vai querer saber como os valores estão dispersos (ou espalhados) em torno da média ou mediana.

A mediana representa o valor no meio de uma distribuição, e os quartis representam outros locais importantes. Que locais são esses?



* O primeiro quartil (Q1) representa o valor no percentil 25 da distribuição dos dados. O percentil 25 é o valor abaixo do qual estão 25% dos dados.
* O segundo quartil (Q2) representa o valor no percentil 50 da distribuição dos dados, que é equivalente à mediana. Da mesma forma que o percentil 25, o percentil 50 é o valor abaixo do qual estão 50% dos dados.
* O terceiro quartil (Q3) representa o valor no percentil 75 da distribuição dos dados.

Veja como isso fica quando consideramos um exemplo simples de distribuição de idades nas imagens'mediana=(3+3)\_dividopor2=3' **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\mediana=(3+3)\_dividopor2=3.png"**



Muitas vezes, visualizamos quartis em uma forma de um diagrama de caixa (ou boxplot). Para o exemplo acima, ele fica assim  imagem 'diagrama\_de\_caixa'  **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\diagrama\_de\_caixa.png"**



Confira o que diz o diagrama de caixa:



* O valor mínimo é 1 ano de idade. Ele está localizado no final do bigode esquerdo.
* O primeiro quartil: 2 anos de idade.
* O segundo quartil: 3 anos de idade.
* O terceiro quartil: 5 anos de idade.
* O máximo é 6 anos de idade. Ele está localizado no final do bigode direito.



A distância entre o Q1 e o Q3 é chamada de **intervalo interquartil** (ou **IQR** – sigla do inglês para **"interquartile range"**). Ele mede a amplitude da meia metade dos dados. Em outras palavras, é o intervalo dos 50% dos dados no meio da amostra.



Para construir diagramas de caixa em Python, é comum usar a biblioteca Seaborn, que fornece capacidades de visualização parecidas às da biblioteca Matplotlib que usamos antes, mas com uma funcionalidade um pouco diferente. A primeira diferença é que precisamos importar a Seaborn.



**import seaborn as sns**

Depois, construímos um diagrama de caixa assim:



**import pandas as pd**



**dataset = pd.Series(\[1, 1, 2, 2, 2, 3, 3, 3, 3, 4, 5, 5, 6, 6])**

**sns.boxplot(dataset)**



Mas como medir a dispersão em torno da medida algébrica de localização, a média?



A primeira (e mais fácil) abordagem é encontrar a distância média entre a média e todos os outros valores. Vamos calculá-la agora.



**import pandas as pd**



**data = pd.Series(\[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10])**

**mean\_value = data.mean()**

**spacing\_all =  data - mean\_value**

**spacing\_all\_mean = spacing\_all.mean()**



**print(spacing\_all\_mean)**



Parece que a distância média é zero, o que parece fazer absolutamente zero sentido! Ainda mais porque sabemos que os valores no conjunto de dados são todos diferentes. Vamos ter que usar outra abordagem…

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



### Variância



Como isso é possível quando todos os valores no conjunto de dados são diferentes? Vamos rever o conjunto de dados: \[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]. A média desse conjunto era 5.



Calculamos a distância a partir de cada elemento do conjunto de dados até a média. Para isso, subtraímos a média de cada valor no conjunto de dados. Confira como:



* 0 - 5 = -5
* 1 - 5 = -4
* 2 - 5 = -3
* …
* 8 - 5 = 3
* 9 - 5 = 4
* 10 - 5 = 5



E para calcular a distância média, somamos todas as diferenças. Algumas dessas distâncias eram positivas, e outras eram negativas, então elas se anularam, o que resultou em uma soma de 0.



Agora vamos nos livrar dos sinais e tornar todos os valores positivos elevando-os ao quadrado:



* (0 - 5)² = -5² = 25
* (1 - 5)² = -4² = 16
* (2 - 5)² = -3² = 9
* …
* (8 - 5)² = 3² = 9
* 9 - 5 = 4² = 16
* 10 - 5 = 5² = 25



σ²= ∑(xᵢ−μ) ² sobre n



 Na fórmula acima:



* σ² é a variância
* Σ é o sinal de soma
* xᵢ representa um valor do conjunto de dados
* µ é a média
* n é o número de valores no conjunto de dados

​

O sinal de sigma (σ² ) foi escolhido para a variância porque ele denota o som "s", como em "standard" (padrão). Na próxima lição, você vai aprender que a raiz quadrada da variância é o **desvio padrão**.



Então, o que a variância significa? Ela mostra o grau de espalhamento no conjunto de dados. Quanto mais espalhados estão os dados, maior é a variância em relação à média.



Confira o gráfico. Há 3 distribuições com variâncias diferentes. **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\grafico\_variancias\_diferentes.png"**





**Em qual caso a variância é zero?**  Quando todos os valores do conjunto de dados são iguais!



Apenas quando todos os valores forem iguais, as distâncias entre a média e os valores serão iguais a zero, assim como a soma dos quadrados desses valores. Em todos outros casos, vai haver uma variância diferente de zero, mesmo que muito pequena.

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

#### 

#### Covariância



Muitas vezes, será do nosso interesse saber como uma variável depende de outra. Por exemplo, como o preço de uma casa depende do tamanho dela.



Para verificar esse tipo de dependência, podemos calcular a covariância entre duas variáveis multiplicando suas diferenças pela média. A covariância é uma medida da dependência linear.



Covariância= ∑ in(xᵢ− x̄)(yᵢ− ȳ) sobre n  **#consultar a formula correta no google**





* Continuando com o exemplo, xᵢ representa o tamanho de uma casa em metros quadrados, e yᵢ representa o preço em dólares.
* n é o número de valores no conjunto de dados (o número de casas e os respectivos preços).
* Σ é o símbolo de soma.
* x̄ é o tamanho da média das casas no conjunto de dados.
* ȳ é a média dos preços das casas no conjunto de dados.



Se a covariância for igual a zero, isso indica que não há nenhuma relação direcional entre as variáveis. O valor de covariância pode ser qualquer valor do infinito negativo até o infinito positivo. Um valor negativo indica uma relação inversa, enquanto um valor positivo indica uma relação direta.



O que uma covariância negativa indica?



* Quanto mais distante de 0 estiver o valor da covariância, maior será a dependência entre duas variáveis. E quando a covariância for 0, não haverá nenhuma dependência.



* Valores negativos e próximos de 0 indicam uma relação negativa fraca. Quanto mais próximo de 0 o valor, menor é a dependência entre as variáveis.





#### Implementação em Python



Para calcular a variância em Python, vamos precisar da biblioteca **NumPy**, a irmã mais velha da biblioteca Pandas que você já conhece. Enquanto a Pandas é boa para estruturas, a NumPy é usada para funções matemáticas complexas. Ela é importada assim:



**import numpy as np**



A variância de um conjunto de dados pode ser encontrada usando o método **var()**:



**import numpy as np**



**x = \[1, 2, 3, 4, 5, 6]** # conjunto de dados



**variance = np.var(x)**

**print(variance)**



result:

**2.9166666666666665**



E calculamos a covariância assim:



**import numpy as np**



**x = \[1, 2, 3, 4, 5, 6] # conjunto de dados 1**

**y = \[41, 62, 89, 96, 108, 115] # conjunto de dados 2**



**covariance\_matrix = np.cov(x,y)** # calculando a matriz de covariância

**covariance = covariance\_matrix\[0]\[1]** # extraindo a covariância como um valor

**print(covariance)**



result:

**51.5**



A função **cov()** na **NumPy** retorna um vetor **2D,** no qual o valor no índice **\[0]\[1]** é a covariância entre **x** e **y.**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



#### Desvio padrão e distribuição normal



Se os dados iniciais fossem medidos em, digamos, metros, usuários ou dólares, a variância seria medida nos quadrados dessas mesmas medidas. Acontece que, muitas vezes, isso é pouco prático para o uso cotidiano.



Para voltar às unidades originais, precisamos (isso mesmo!) tirar a raiz quadrada da variância. O valor resultante é conhecido como **desvio padrão** que, às vezes, é chamado de std.



Você provavelmente já viu "std" no resultado do método **describe()**. Se não, confira um exemplo:



**import pandas as pd**



**s = pd.Series(\[1, 2, 3, 4, 5, 6])**

**s.describe()**



result:

**count    6.000000**

**mean     3.500000**

**std      1.870829**

**min      1.000000**

**25%      2.250000**

**50%      3.500000**

**75%      4.750000**

**max      6.000000**

**dtype: float64**





Entre as várias métricas de dispersão, o desvio padrão é o mais usado, já que ele tem as mesmas unidades de medida que os dados.



O desvio padrão é denotado pelo sigma minúsculo. O sigma foi escolhido porque tem a denotação do som do "s", assim como em "standard" (padrão), e a variância é sigma ao quadrado (ou seja, desvio padrão ao quadrado). Então a fórmula para o desvio padrão é esta:





σ= V ∑(x i−μ) 2 dobre n # consultar a formula correta no google

​



 O desvio padrão de um conjunto de dados pode ser calculado com o método **std()** da biblioteca NumPy:



**import numpy as np**



**x = \[1, 2, 3, 4, 5, 6]** # conjunto de dados



**standard\_deviation = np.std(x)**

**print(standard\_deviation)**



result:

**1.707825127659933**

​

Imagine que você já sabe a variância de um conjunto de dados. Nesse caso, você pode usar o método **sqrt()** da NumPy para calcular o desvio padrão:



**import numby as np**



**variance = 3.5**

**standard\_deviation = np.sqrt(variance)**

**print(standard\_deviation)**



result:

**1.8708286933869707**



#### Distribuição normal



A **distribuição normal**, também conhecida como a **distribuição Gaussiana**, é a distribuição mais usada para muitas variáveis. Ela é conhecida por sua curva simétrica em forma de sino e pode ser usada em várias aplicações estatísticas, como análises de pesquisas, controle de qualidade e até alocação de recursos. Geralmente ela tem essa aparência:  **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\distribuicao\_normal.png"**



Como sabemos, distribuições normais são simétricas em volta da média, ou do centro de um gráfico. Isso significa que os dados próximos da média ocorrem com mais frequência do que os dados que estão longe dela.



Uma distribuição desse tipo pode ser definida por dois parâmetros:



* **a média** (ou o valor médio), que é o valor máximo do gráfico em relação ao qual o gráfico é sempre simétrico
* **o desvio padrão**, que determina a dispersão a partir da média



Assim como na variância, um desvio padrão menor (comparado à média) produz uma curva mais íngreme, enquanto um desvio padrão maior (também comparado à média) produz uma curva mais plana:  **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\grafico\_ desvio\_padrao.png"**





Se os dados seguirem uma distribuição normal, uma regra importante será aplicada: a regra dos três sigmas. Essa regra afirma que quase todos os valores (99,7%) caem em um intervalo específico. Este é o intervalo:



#### (μ−3σ,μ+3σ)



Lembre-se de que **µ** representa a média e **σ** representa o desvio padrão. Em outras palavras, 99,7% de todos os valores estão em um intervalo de 3 desvios padrão à esquerda e à direita da média. Aqui está uma ilustração da regra dos três sigmas para distribuições normais:  **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\ilustracao\_regra\_dos\_tres\_sigmas\_para\_distribuicoes\_normais.png"**



Essa regra nos permite não apenas encontrar um intervalo que certamente contém quase todos os valores da variável, mas também nos ajuda a detectar valores que estão fora dela. Tais valores são chamados de atípicos. Eles merecem atenção, já que a presença deles nos dados pode produzir informações importantes sobre a variável ou revelar erros de medição e problemas parecidos.

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



Encontre o desvio padrão do conjunto de dados **data = pd.Series(\[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]) e** armazene-o na variável **standard\_dev.** Em seguida, imprima os resultados.



**import pandas as pd**

**import numpy as np**



**data = dp.Series(\[0,1,2,3,4,5,6,7,8,9,10])**



**standard\_dev = np.std(data)**

**print(standard\_dev)**



result:

**3.1622776601683795**







* Calcule o desvio padrão da variância e armazene o resultado na variável adv\_std.
* Com base na média e no desvio padrão, calcule o limite superior do intervalo que represente 99,7% dos usuários. Armazene o valor resultante na variável adv\_time.
* Imprima o texto O tempo de exibição da mensagem é seguido do seu resultado





**import numpy as np**



**adv\_mean = 3**

**adv\_var = 0.25**

**av\_std = np.sqrt(adv\_var)**



**adv\_time = adv\_mean + 3 \* adv\_std**

**print('O tempo de exibição da mensagem é', adv\_time)**



result:

**O tempo de exibição da mensagem é 4.5**







#### tarefa



* Comece calculando a média esperada de respostas corretas dos participantes. Com base na porcentagem média dos participantes que responderam corretamente (3% ou 0.03) e no número esperado de participantes (6000), calcule a média e armazene o valor resultante na variável quiz\_mean.
* Em seguida, usando o número total de participantes esperados (6000) e uma porcentagem fornecida para o desvio padrão (0.4% ou 0.004), calcule o desvio padrão do número das pessoas que vão comparecer. Esse valor, σ, deve ser armazenado na variável quiz\_std.
* Por fim, determine um intervalo para o número de vencedores. Conforme a regra dos três sigmas, esse intervalo se estende três desvios padrão à esquerda e à direita da média. Calcule os limites desse intervalo e armazene o limite inferior na variável quiz\_bottom\_line e o limite superior na variável quiz\_top\_line.
* Imprima os resultados no formato exigido.



**quiz\_mean = 6000 / 100 \* 3**

**quis\_std = 6000 / 100 \* 4**



**quiz\_bottom\_line = quiz\_mean - 3 \* quiz\_std**

**quis\_tio\_line = quiz\_mean + 3 \* quiz\_std**



**print('Intervalo:', quiz\_bottom\_line, '-', quiz\_top\_line)**



result:

**Intervalo: 108.0 - 252.0**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



#### Dados assimétricos e valores atípicos



Em vários casos, os dados da vida real são distribuídos normal e simetricamente. No entanto, conjuntos de dados podem ser assimétricos, ou "dispersos", tanto em uma direção positiva quanto negativa.

**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\Dados\_assimetricos\_ a\_direita.png"**





Para saber se os dados são assimétricos, observe o histograma e localize um pico, que representa os valores mais frequentes. Uma distribuição de dados com mais valores à direita do pico do que à esquerda (como acima) é chamada **assimétrica à direita**. Isso é **assimetria positiva**.



Se o conjunto de dados tem mais valores à esquerda, ele é **assimétrico à esquerda**. Essa é, como você pode adivinhar, uma assimetria negativa. Continuando com o exemplo da pesquisa, se a maioria dos entrevistados fossem jovens e não idosos, os resultados seriam assimétricos com concentração à esquerda.



O gráfico abaixo contém dois subgráficos, e cada um exibe uma distribuição de tempo gasto. O subgráfico esquerdo mostra a distribuição na forma de um diagrama de caixa, enquanto o direito mostra um histograma normal girado em 90 graus no sentido anti-horário, o que facilita a comparação com o diagrama à esquerda.



**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\dois\_subgraficos\_de\_distribuicao\_de\_tempo\_gasto.png"**



O diagrama de caixa à esquerda mostra Q1, a mediana (ou Q2) e Q3. Anteriormente, aprendemos que um diagrama de caixa exibe os valores mínimo e máximo, localizados nos finais dos bigodes. No entanto, o que a seção preta em negrito no intervalo entre 650 e 1.000 representa? Ainda não aprendemos sobre isso.



Se ampliarmos a imagem, veremos que a seção em negrito não é uma linha, mas pontos.



**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\diagrama\_de\_caixa\_ampliado.png"**



Esses são valores atípicos, extremos que se desviam significativamente do padrão geral dos valores de um conjunto de dados. Mas e como determinar se um valor tem um desvio significativo do padrão geral? Há uma regra para isso: se algum valor estiver 1,5 vez o intervalo interquartil (IQR, na sigla em inglês) à esquerda do Q1 ou 1,5 vez o IQR à direita do Q3, ele é considerado atípico.



**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\imagens\\diagrama\_valores\_atipicos.png"**

