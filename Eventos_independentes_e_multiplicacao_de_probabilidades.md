Digamos que temos interesse na soma total quando os dois dados são jogados. Podemos visualizar todos os resultados possíveis assim: **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\diagrama\_de\_espaco\_amostral.png"**



Esse é um diagrama de espaço amostral. Os números ao longo dos eixos representam os resultados de cada dado, e as interseções representam a soma dos resultados dos dois dados.



O diagrama mostra que há apenas um resultado (dos 36 possíveis) em que a soma resulta em 2, em comparação aos outros seis em que a soma é igual a 7.





#### Eventos mais complicados



Podemos usar o último exemplo para examinar eventos mais complicados. Por exemplo, considere a questão de quantos resultados dão uma soma maior do que 8 quando jogamos dois dados. Contar o número de células azuis abaixo (ou seja, as células que satisfazem esse evento) retorna uma resposta de 10.



Podemos reformular a pergunta assim: qual é a probabilidade de jogar dois dados e obter uma soma maior do que 8? **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\digrama\_soma\_maior\_do\_que8.png"**



Se definirmos o evento A como "obter uma soma maior do que 8", então a probabilidade de A é P(A) **= 10/36 = 27,7%.**  



#### Intersecção de eventos



É possível que um resultado seja associado a múltiplos eventos. Por exemplo, os seguintes eventos compartilham resultados:



* Evento A – a soma de dois dados é maior que 8
* Evento B – os dados exibem o mesmo número



imagem: **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\Interseccao\_de\_eventos.jpg"** 



Observe que se ambos os dados exibem 5 ou 6, então ambos os eventos A e B ocorrem.

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

#### Diagramas de Venn



Para ilustrar a ocorrência de ambos os eventos (como A e B acima, quando ambos os dados exibiram 5 ou 6), podemos usar um diagrama de Venn. Ele não exibe pontos amostrais, apenas a intersecção relevante entre os eventos: **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\interseccao\_Diagama \_de\_Venn.png"**



Eventos que não podem ocorrer simultaneamente no mesmo experimento são chamados mutuamente exclusivos — eles não se intersectam no diagrama de Venn: **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\mutuamente\_exclusivos\_diagrama\_de\_Venn.png"**



A probabilidade de intersecção de eventos mutuamente exclusivos é 0.



Se os eventos A e B são mutuamente exclusivos, quer dizer que P(A e B) = 0. Como você pode ver acima, se o evento A ocorre, não há como o evento B também ter ocorrido.



Se eventos mutuamente exclusivos cobrem todo o espaço amostral, então a soma de suas probabilidades será igual a 1.



Por exemplo, vamos considerar os seguintes eventos:



* Os dois dados exibem o mesmo número (células vermelhas na imagem abaixo).
* O primeiro dado exibiu um número maior do que o segundo (células verdes).
* O segundo dado exibiu um número maior do que o primeiro (células azuis).



Todos os pontos amostrais estão inclusos nesses eventos; eles cobrem todo o espaço amostral. As probabilidades são 6/36, 15/36 e 15/36, respectivamente. Juntas, elas somam 1: (6 + 15 + 15) / 36 = 1.



#### Eventos independentes e dependentes



Eventos são chamados de **independentes** se a ocorrência de um não afeta a probabilidade de outro.



Se o evento A = chove e B = você vai para o trabalho de guarda-chuva, então a probabilidade de B vai depender da probabilidade de A. Esses são eventos **dependentes**.



##### Probabilidades de eventos independentes



Se os eventos A e B são independentes, então **P(A e B)** é igual a **P(A) x P(B)**.



Isso quer dizer que você precisa apenas saber as probabilidades individuais para calcular a probabilidade de ambos ocorrerem.



Observação: Isso NÃO é caso para eventos dependentes.



Exemplo



Sejam os eventos A e B iguais a…



* A = o primeiro dado exibe 3
* B = o segundo dado exibe 5



Esses eventos são independentes: o resultado do primeiro dado não tem efeito no segundo. Já que cada lançamento de um dado tem a mesma probabilidade de resultar em um valor de 1 a 6, sabemos que P(A) = 1/6 e P(B) = 1/6. Usando a fórmula apresentada acima, podemos calcular P(A e B) = 1/6 × 1/6 = 1/36.



Visualmente, percebemos que esse cálculo está correto ao observarmos 1 resultado entre os 36 que satisfazem tanto A quanto B.



**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\eventos\_independentes.png"**





O site é composto por seções, essas seções são compostas por subseções e as subseções são compostas por páginas, como demonstrado no gráfico.

**"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\exemplo\_exercicio.png"**



Um usuário vai da página inicial do site para uma das seções, depois para uma subseção e depois para uma página. Sempre que um link é clicado, cada opção possível é igualmente provável. Qual é a probabilidade de que ele vai abrir a subseção necessária?



Aproximadamente 4,63% (A probabilidade de escolha de uma das 4 seções possíveis é 1/4. A probabilidade de escolha de uma das 3 subseções possíveis é 1/3. A probabilidade de escolha de uma das 5 páginas do nosso interesse, do total de 9 páginas na subseção, é 5/9. Resposta: 1/4 \* 1/3 \* 5/9 = 5/108 ≈ 0,046296 ≈ 4,63%)





#### Fundamentos da combinatória e mais problemas de probabilidades



##### Permutações. Como calcular o fatorial



Para calcular o número de permutações de n elementos, os matemáticos usam esta fórmula:



##### Pn=n!



Você talvez não tenha encontrado o sinal "!" em expressões matemáticas até agora. Ele é chamado de fatorial e significa o produto de números naturais de 1 a n. Ou seja:



##### n!=1⋅2⋅3⋅...⋅(n−1)⋅n



Então, para os três cursos diferentes, há 3! = 1 x 2 x 3 = 6 percursos educacionais diferentes.



#### Como calcular fatoriais em Python



Quando o valor de n é pequeno, n! pode ser calculado de cabeça. Para valores maiores de n, é mais conveniente automatizar o processo. Para fazer isso, você pode usar a função **factorial()** do módulo math da biblioteca padrão de Python.



\# Importe a função factorial do módulo math

**from math import factorial**



\# Defina o número necessário de cursos

**courses\_amount = 3**



\# Calcule o fatorial de 3 (o valor da variável courses\_amount)

**result = factorial(courses\_amount)**



\# Imprima o resultado

**print(result)**



result

**6**



#### Combinações



a fórmula para calcular o número de combinações de k elementos de n opções possíveis. A fórmula é a seguinte:



Ckn = n! sobre k!⋅(n−k)!​ **# consultar formula no google**



formula : **"C:\\Users\\andre\\OneDrive\\Documentos\\estudos\\Ciência\_de\_Dados\_tripleTen\\Sprint\_4\_tripleTen\\anotacoes\\Teoria\_da\_probabilidade\\imagens\\formula\_combinacoes.jpg"**



O mesmo pode ser calculado em Python:



**from math import factorial**



\# Defina os valores para as variáveis n e k

**n = 5**

**k = 3**



\# Faça os cálculos

**combinations = factorial(n) / (factorial(k) \* factorial(n-k))**

**print(combinations)**



result

**10.0**



**No seu exemplo:**



**n = 5 (total de elementos)**

**k = 3 (elementos escolhidos)**

**C(5,3) = 5! / (3! × 2!)**



**Cálculo passo a passo:**

**C(5,3) = 5! / (3! × 2!)**

       **= 120 / (6 × 2)**

       **= 120 / 12**

       **= 10**



##### Tarefa 

Os clientes estavam insatisfeitos com a dificuldade de vencer o prêmio principal, então você alterou as regras. Agora os jogadores podem escolher três tarefas para começar o jogo. A ordem das tarefas não importa, o importante é a combinação delas. Se os jogadores conseguirem adivinhar a "combinação secreta", eles recebem um código promocional.



Para garantir equidade, você precisa calcular a probabilidade de receber o código promocional usando as seguintes variáveis:



* **tasks** — número total de tarefas disponíveis
* **chosen** — número de tarefas escolhidas no começo do jogo
* **combinations** — número total de possíveis combinações de 3 tarefas a partir das 10 disponíveis
* **probability** — probabilidade final de receber o código promocional



Implemente um programa que calcule a probabilidade de receber o código promocional usando as variáveis acima.



##### código 



**from math import factorial**



**tasks = 10**

**chosen = 3**



**combinations = factorial(tasks) / (factorial(chosen)\* factorial(tasks - chosen))**

**probability = 1 / combinations**



**print(probability)**



result:

**0.008333333333333333**

















































