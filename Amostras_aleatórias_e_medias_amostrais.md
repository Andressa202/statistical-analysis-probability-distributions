### Amostras aleatórias e médias amostrais



Alguns conjuntos de dados podem ter várias partes de tamanho desigual que diferem muito em relação ao parâmetro que você está estudando. Nesses casos, é uma boa ideia pegar amostras aleatórias proporcionais de cada parte e depois combiná-las. O resultado é uma **amostra estratificada**, que é mais representativa do que uma amostra aleatória seria. Chamamos de "estratificada" porque dividimos a população em **estratos**, ou grupos, unidos por uma característica comum. Esses estratos são então usados para produzir amostras aleatórias.



**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Testes\_de\_hipoteses\\imagens\\amostra\_aleatoria.png"**



É possível estimar a média de uma população estatística usando a média de uma amostra. Quanto maior a amostra, mais precisa será a média da população – e isso funciona para populações estatísticas com qualquer distribuição.





### Formulação de hipóteses bicaudais





Probabilidade de o valor ficar entre 733 e 1247

P(a≤X≤b) = P(X≤b) – P(X≤a) = P(X≤1247) – P(X≤733) = 98.95%





#### Testes de hipóteses em Python. Valores-p



A função **scipy.stats.ttest\_1samp (array, popmean)** é usada para testar hipóteses do tipo "a média da população é igual a x".



**ttest** significa teste t. **1samp** significa que estamos trabalhando com uma amostra e comparando-a com um determinado valor.



Passamos estes parâmetros para a função:



* **array** é um vetor que contém a amostra.
* **popmean** é a média proposta que estamos testando.



Quando chamada, a função retorna a estatística de diferença entre popmean e a média da amostra do vetor array. 



ex: 

Uma amostra de 200 pessoas foi retirada dos registros do tempo gasto no site. Vamos testar a hipótese do seu parceiro. Para isso, vamos conduzir um teste e comparar o valor-p resultante com o limiar que definiremos como 5%.





**from scipy import stats as st**

**import numpy as np**

**import pandas as pd**



**time\_on\_site = pd.read\_csv('user\_time.csv')**



**interested\_value = 120** # tempo gasto no site



**alpha = .05** # significância estatística crítica (limiar)



\# executando um teste

**results = st.ttest\_1samp(**

&#x20;   **time\_on\_site,** 

&#x20;   **interested\_value)**



\# imprimindo o valor-p resultante

**print('valor-p: ', results.pvalue)**



\# comparando o valor-p com o limiar

**if (results.pvalue < alpha):**

&#x20;   **print("Rejeitamos a hipótese nula")**

**else:**

&#x20;   **print("Não podemos rejeitar a hipótese nula")**



result:

**valor-p:  \[0.27702871]**

**Não podemos rejeitar a hipótese nula**





### Formulação de hipóteses unicaudais

##### Exemplo

Você está vendendo melancias online. Para vender todas antes do final da estação, você contratou alguns profissionais de desenvolvimento web para criar uma página de destino chamada Watermelon Life. Observando as estatísticas, você notou que quanto mais as pessoas rolavam pelo site (quanto mais blocos visualizavam), mais compravam melancias. A média de blocos visualizados é 4,867.



Por insistência dos designers, você alterou os primeiros blocos para atender a novas diretrizes, e o número de pedidos não mudou. Mas talvez os usuários tenham começado a fazer compras mais rápido. Vamos verificar se é esse o caso: se for, os usuários agora decidem fazer compras após visualizar apenas os primeiros blocos da página de destino, portanto, o número de blocos que veem deve ser menor.



Usaremos uma amostra de 100 compradores aleatórios. O conjunto de dados é o número de blocos visualizados da página de destino. A nossa hipótese nula é que o número de blocos visualizados da página de destino é maior ou igual a 4,867



**from scipy import stats as st**

**import pandas as pd**



**screens = pd.Series(\[4, 2, 4, 5, 5, 4, 2, 3, 3, 5, 2, 5, 2, 2, 2, 3, 3, 4, 8, 3, 4, 3, 5, 5, 4, 2, 5, 2, 3, 7, 5, 5, 6,  5, 3, 4, 3, 6, 3, 4, 4, 3, 5, 4, 4, 8, 4, 7, 4, 5, 5, 3, 4, 6, 7, 2, 3, 6, 5, 6, 4, 4, 3, 4, 6, 4, 4, 6, 2, 6, 5, 3, 3, 3, 4, 5, 3, 5, 5, 4, 3, 3, 3, 1, 5, 4, 3, 4, 6, 3, 1, 3, 2, 7, 3, 6, 6, 6, 5, 5])**



**prev\_screens\_value = 4.867** # número médio de blocos visualizados



**alpha = 0.05**  # nível de significância



**results = st.ttest\_1samp(screens, prev\_screens\_value)**



\# teste unilateral: o valor-p será reduzido pela metade

**print('valor-p: ', results.pvalue / 2)**



\# teste unilateral à esquerda:

\# rejeitar a hipótese apenas se a média da amostra for significativamente menor que o valor proposto

**if (results.pvalue / 2 < alpha) and (screens.mean() < prev\_screens\_value):**

&#x20;   **print("Rejeitamos a hipótese nula")**

**else:**

&#x20;   **print("Não podemos rejeitar a hipótese nula")**



result:

**valor-p:  1.3358596895543794e-06**

**Rejeitamos a hipótese nula**



Como você pode ver no código, em um teste unilateral com a hipótese alternativa "O número de blocos visualizados diminuiu", a hipótese nula é rejeitada se duas condições forem atendidas:



* &#x20;O valor observado é menor do que o previsto.



* A diferença entre os valores é estatisticamente significativa (dividimos o valor-p que obtivemos do teste bilateral por 2).



Se o teste fosse unilateral à direita com a hipótese alternativa "O valor observado é maior que o previsto", um dos sinais **"<"** mudaria para **">"**. As últimas linhas de código ficariam assim:



**if (results.pvalue / 2 < alpha) and (screens.mean() > prev\_screens\_value):**

&#x20;   **print("Rejeitamos a hipótese nula")**

**else:**

&#x20;   **print("Não podemos rejeitar a hipótese nula")**





### Hipótese sobre a igualdade das médias de duas populações



Para testar a hipótese de que as médias das duas populações estatísticas são iguais com base nas amostras retiradas delas, aplique a função **scipy.stats.ttest\_ind(array1, array2, equal\_var)**.



Passamos estes parâmetros para a função:



* **array1** e **array2** são vetores contendo as amostras
* **equal\_var** (variância igual) é um parâmetro que especifica se as variâncias das populações devem ou não ser consideradas iguais. Ele é passado como **equal\_var = True** ou **equal\_var = False** (True significa que consideramos as variâncias iguais, False significa que não). Sabemos que as variâncias podem ser diferentes. Para ter uma ideia de duas populações com variâncias (e valores das médias) diferentes, veja este exemplo com 2 populações aleatórias:



**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Testes\_de\_hipoteses\\imagens\\exemplo\_populacao\_aleatoria.png"**



##### exemplo:



Vamos considerar um exemplo com dois conjuntos de dados: o valor gasto em compras feitas em um mês por visitantes provenientes de dois canais diferentes. Você tem uma amostra aleatória de 30 compras de cada canal.



**from scipy import stats as st**

**import numpy as np**



**sample\_1 = \[3071, 3636, 3454, 3151, 2185, 3259, 1727, 2263, 2015,** 

&#x20;           **2582, 4815, 633, 3186, 887, 2028, 3589, 2564, 1422, 1785,** 

&#x20;           **3180, 1770, 2716, 2546, 1848, 4644, 3134, 475, 2686,** 

&#x20;           **1838, 3352]**



**sample\_2 = \[1211, 1228, 2157, 3699, 600, 1898, 1688, 1420, 5048, 3007,** 

&#x20;           **509, 3777, 5583, 3949, 121, 1674, 4300, 1338, 3066,** 

&#x20;           **3562, 1010, 2311, 462, 863, 2021, 528, 1849, 255,** 

&#x20;           **1740, 2596]**



**alpha = 0.05**  # nível crítico de significância estatística

\# se o valor-p for menor que alfa, rejeitamos a hipótese nula



**results = st.ttest\_ind(sample\_1, sample\_2)** # executando um teste



**print('valor-p: ', results.pvalue)** # extraindo o valor-p



**if results.pvalue < alpha:** # comparando o valor-p com o limiar

&#x20;   **print("Rejeitamos a hipótese nula")**

**else:**

&#x20;   **print("Não podemos rejeitar a hipótese nula")**



result:

**p-value:  0.1912450522572209**

**Não podemos rejeitar a hipótese nula**





#### Tarefa 

Temos dois conjuntos de dados: a profundidade de visitas ao site de diferentes grupos de usuários para os meses de verão e outono. Teste a hipótese de que as profundidades de visitas do site são iguais. Por exemplo, talvez no verão os visitantes não se aprofundem tanto no conteúdo, o que seria algo a ser considerado ao planejar uma campanha publicitária para esses meses. O nível de significância deve ser 0,05.



Não esperamos que as variâncias sejam as mesmas, então defina o parâmetro **equal\_var** como **False**. Você pode executar **np.var(pages\_per\_session\_autumn)**, etc. para verificar a variação do conjunto.



**from scipy import stats as st**

**import numpy as np**



**pages\_per\_session\_autumn = \[7.1, 7.3, 9.8, 7.3, 6.4, 10.5, 8.7,** 

&#x20;                           **17.5, 3.3, 15.5, 16.2, 0.4, 8.3,** 

&#x20;                           **8.1, 3.0, 6.1, 4.4, 18.8, 14.7, 16.4,** 

&#x20;                           **13.6, 4.4, 7.4, 12.4, 3.9, 13.6,** 

&#x20;                           **8.8, 8.1, 13.6, 12.2]**

**pages\_per\_session\_summer = \[12.1, 24.3, 6.4, 19.9, 19.7, 12.5, 17.6,** 

&#x20;                           **5.0, 22.4, 13.5, 10.8, 23.4, 9.4, 3.7,** 

&#x20;                           **2.5, 19.8, 4.8, 29.0, 1.7, 28.6, 16.7,** 

&#x20;                           **14.2, 10.6, 18.2, 14.7, 23.8, 15.9, 16.2,** 

&#x20;                           **12.1, 14.5]**



**alpha = 0.05# seu código: defina um nível crítico de significância estatística**



**results = st.ttest\_ind(pages\_per\_session\_autumn, pages\_per\_session\_summer, equal\_var=False)**# seu código: teste a hipótese de que as médias das duas populações independentes são iguais

**np.var(pages\_per\_session\_autumn)**

**print('valor-p:', results.pvalue)** # seu código: imprima o valor-p obtido)



**if results.pvalue < alpha:**

&#x20;   **print("Rejeitamos a hipótese nula")**

**else:**

&#x20;   **print("Não podemos rejeitar a hipótese nula")**



result:

**valor-p: 0.002200163165401993**

**Rejeitamos a hipótese nula**





### Hipótese sobre a igualdade das médias de amostras pareadas





Para testar a hipótese de que as médias de duas populações são iguais para amostras dependentes (pareadas) em Python, precisamos usar esta função: **scipy.stats.ttest\_rel()**.



Ela só precisa de dois parâmetros: vetores com dados de antes e depois. As matrizes precisam ser do mesmo tamanho.



Temos dois conjuntos de dados: peso do pacote, em gramas, antes de alterar o método de cálculo do frete e o peso depois (para os mesmos clientes repetidos). Vamos testar a hipótese de que o peso do pacote não mudou, embora o método de cálculo do frete tenha mudado.



**from scipy import stats as st**

**import numpy as np**



**before = \[157, 114, 152, 355, 155, 513, 299, 268, 164, 320,** 

&#x20;                   **192, 262, 506, 240, 364, 179, 246, 427, 187, 431,** 

&#x20;                   **320, 193, 313, 347, 312, 92, 177, 225, 242, 312]**



**after = \[282, 220, 162, 226, 296, 479, 248, 322, 298, 418,** 

&#x20;                **552, 246, 251, 404, 368, 484, 358, 264, 359, 410,** 

&#x20;                **382, 350, 406, 416, 438, 364, 283, 314, 420, 218]**



**alpha = 0.05**  # nível crítico de significância estatística



**results = st.ttest\_rel(before, after)**



**print('valor-p: ', results.pvalue)**



**if results.pvalue < alpha:**

&#x20;   **print("Rejeitamos a hipótese nula")**

**else:**

&#x20;   **print("Não podemos rejeitar a hipótese nula")**



result:

**valor-p:  0.005825972457958989**

**Rejeitamos a hipótese nula**



#### Tarefa 

Temos dois conjuntos de dados: o número de balas compradas por jogadores ávidos de um jogo online, antes e depois da inclusão de uma mecânica que fornece incentivos para disparos em rajadas. Teste a hipótese de que os jogadores começaram a usar mais balas depois que o novo recurso foi incluído.



Pense na palavra "mais" na hipótese acima. Ela sugere a necessidade de um teste unilateral ou bilateral?





**from scipy import stats as st**

**import numpy as np**

**import pandas as pd**



**bullets\_before = \[821, 1164, 598, 854, 455, 1220, 161, 1400, 479, 215,** 

&#x20;         **564, 159, 920, 173, 276, 444, 273, 711, 291, 880,** 

&#x20;         **892, 712, 16, 476, 498, 9, 1251, 938, 389, 513]**



**bullets\_after = \[904, 220, 676, 459, 299, 659, 1698, 1120, 514, 1086, 1499,** 

&#x20;        **1262, 829, 476, 1149, 996, 1247, 1117, 1324, 532, 1458, 898,** 

&#x20;        **1837, 455, 1667, 898, 474, 558, 639, 1012]**



**print('média antes:', pd.Series(bullets\_before).mean())**

**print('média depois:', pd.Series(bullets\_after).mean())**



**alpha = 0.05**



**results = st.ttest\_rel(**

&#x20;   **bullets\_before,** 

&#x20;   **bullets\_after)**



**print('valor-p:', results.pvalue / 2) # seu código: imprima o valor-p obtido)**



**if (results.pvalue / 2 < alpha) and (pd.Series(bullets\_after).mean() > pd.Series(bullets\_before).mean()):**



&#x20;   **print("Rejeitamos a hipótese nula")**

**else:**

&#x20;   **print("Não podemos rejeitar a hipótese nula")**



result:

**média antes: 591.7333333333333**

**média depois: 932.0666666666667**

**valor-p: 0.005394751910405561**

**Rejeitamos a hipótese nula**













































