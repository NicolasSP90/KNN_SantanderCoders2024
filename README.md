![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![pyenv](https://img.shields.io/badge/pyenv-white?style=for-the-badge)
![poetry](https://img.shields.io/badge/poetry-d0d4fc?style=for-the-badge)
![ipykernel](https://img.shields.io/badge/ipykernel-3670A0?style=for-the-badge)
![draw.io](https://img.shields.io/badge/draw.io-F2931E?style=for-the-badge)

# Visão Geral
Terminada a disciplina Lógica de Programação da trilha de Engenharia de Dados do Santander Coders 2024, da parceria entre Ada Tech e Santander Open Academy. Tivemos o desafio de criar e implementar um algoritmo de KNN a partir de conceitos básicos de programação e lógica e sem o auxílio de bibliotecas externas.

# Algorítmo KNN
O KNN (K-Nearest Neighbors) é um modelo supervisionado de machine learning que pode ser utilizado tanto para classificação quanto para regressão. O desafio envolve criar e utilizar o modelo para corretamente classificar o perfil de investidores baseado nas carteiras de investimento.

# O Projeto
Iniciei o projeto com um fluxo do processo para entender o que precisaria fazer. Quando verificava que uma situação não estava nos conformes, primeiro verifiquei a lógica do fluxo e depois voltei para os códigos. Segue o fluxograma geral do algorítmo criado:

<img src="Assets/Projeto_KNN - 0.png">

O algorítmo deve retornar uma resposta baseado nos K valores mais próximos de determinado dado de entrada (Valor Input) em relação a dados já existentes (Dados). Cada bloco colorido é uma função criada, ou uma lógica específica do programa.

O valor de K (inpout do usuário para saber quantos "vizinhos" serão considerados) determina o tamanho de duas listas utilizadas: uma para armazenar os valores de resposta (resp_k) dos dados conhecidos ("Agressivo", "Conservador", "Moderado") e outra para os valores de distância euclidiana (dist_k).

O primeiro passo do programa é separar os dados do conjunto recebido. A função retorna duas listas, uma com a classificação e outra com os valores numéricos das carteiras de clientes. Segue a lógica:

<img src="Assets/Projeto_KNN - 1.png">

As duas listas de retorno alimentam a função do KNN. Neste ponto, é realizada uma iteração com base no indice da lista de carteiras (que tem o mesmo comprimento que a lista de classificação gerada, sendo assim, percorre o indice de ambas as listas simultaneamente). Para cada elemento do indice da lista de carteiras é calculada a distância do elemento de entrada que deve ser classificado. Se as listas de distância ou de resposta (dist_k e resp_k) tiver menos que K elementos, serão apenas adicionados. Se tiverem K elementos, será verificado o maior valor da lista de distancia (dist_k) e o indice associado a ele. Se o elemento for MAIOR que a distância euclidiana recem calculada, substituir o elemento. Seguem as lógicas:

Distância Euclidiana:

Além do mencionada acima, foi adicionada uma pequena validação de dados para garantir que ou será feito o cálculo em cima de dois elementos numéricos informados (float e int) ou serão feitos os cálculos de acordo com duas coleções de mesmo tipo e mesmo tamanho.

<img src="Assets/Projeto_KNN - 2.png">

Listas de K elementos:

Ressaltar apenas que esse bloco de código não é uma função, mas sim um pedaço da lógica aplicada do código principal, apenas separado apra melhor visualização.

<img src="Assets/Projeto_KNN - 3.png">

A partir das listas de k elementos, foi criada uma função de resposta, baseado na regra do problema proposto: para regressão utilizar média dos valores e para classificação (problema atual), utilizar moda.

<img src="Assets/Projeto_KNN - 4.png">

Para verificação da moda, é criado um dicionário onde as chaves são as definições de classificação e os valores são a contagem de cada classificação nas listas de dist_k e resp_k. Caso só exista UM valor máximo, será retornada a classificação que mais se repete.

- E se a quantidade de valores de classificação resultar em empate? Ex: 2x "Agressivo" e 2x "Moderado"? ou 2x "Agressivo", 2x "Moderado" e 2x "Conservador"

Para esse caso o dicionário de decisão passa a ser somente o relacionado aos valores que mais se repetem e então é criado um segundo dicionário onde as chaves são novamente as definições de classificação, mas os valores são a MENOR distância euclidiana de cada uma das classificações. Nesse caso, é retornada a classificação de MENOR distância.

- E se as distâncias euclidianas de duas ou mais classificações forem as mesmas?

Nesse caso o ideal é verificar com a equipe de negócio qual o melhor plano e estratégia. Para esse caso em específico, Assumi que o melhor resultado seria o que trouxesse o menor risco para o cliente, considerando que devem ser ofertados produtos e ativos de menor risco. Caso o perfil do cliente seja de maior risco, é mais provável que uma segunda verificação ocorra conforme a carteira de ativos financeiros vá sendo atualizada e incrementada.

# Conclusão

Não apenas o output do código, mas também outros testes e tratamentos de erros foram realizados. De maneita geral o algorítmo se comportou bem e teve uma boa avaliação na classificação das carteiras de clientes.

## Métricas de Treino:

<img src="Assets/Projeto_KNN - 5.png">

## Output da Implementação

<img src="Assets/Projeto_KNN - 6.png">