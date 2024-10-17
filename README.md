# Ciencia de dados no RPG de mesa! Analise fatorial dos atributos dos nossos monstros favoritos

20 de junho de 2024

Olá pessoal! Como mencionei anteriormente, estou cursando MBA em Data Science e Analytics na  [MBA USP/Esalq](https://www.linkedin.com/school/mbauspesalq/)  e tenho utilizado o LinkedIn para publicar artigos que me ajudem a aplicar o que aprendo em sala de aula. No último artigo, explorei a análise de clusters para identificar jogadores de perfil semelhante ao do Mbappé.

[Projeto de Ciência de Dados: Identificando jogadores Semelhantes a Mbappé através de Clusters](https://www.linkedin.com/pulse/projeto-de-ci%2525C3%2525AAncia-dados-identificando-jogadores-estaiano-j%2525C3%2525BAnior-tgsaf/?trackingId=5tMQS0MYQv2d%2B4TsjyKMWw%3D%3D)

Nesta semana, o foco foi na  **análise fatorial e PCA**, que será o tema deste novo artigo.

Se antes estavamos no universo do futebol, agora estamos dando um mergulho no mundo do RPG de mesa, vamos estudar os terríveis monstros do famoso universo do D&D.

### Sobre a Base de Dados

Ao explorar o  [Kaggle](https://www.kaggle.com/datasets/jairohernandez/d-and-d-5e-monster-stats), encontrei uma base de dados fascinante que contém informações sobre os atributos dos monstros do D&D 5e. Esta base possui 13 colunas, das quais 9 são numéricas. Adicionei mais uma coluna com os dados de velocidade a pé dos monstros, totalizando 10 variáveis para nosso estudo.

![](https://media.licdn.com/dms/image/v2/D4D12AQGdHVIjz2Q1Sg/article-inline_image-shrink_1000_1488/article-inline_image-shrink_1000_1488/0/1718906288044?e=1734566400&v=beta&t=ftYmo077-wT8BIf3vbhMIQ-04cM2BVT5_CYl8OSiRkc)

### Variáveis Selecionadas para a Análise Fatorial

Entre as variáveis escolhidas para a análise fatorial estão:

-   **Armor Class**: A classe de armadura, ajustada para incluir apenas o valor numérico.
-   **Hit Points**: Os pontos de vida, apresentados como um número inteiro simples.
-   **Speed**: Dados descritivos sobre as capacidades de movimento do monstro.
-   **CR (Challenge Rating)**: O índice de dificuldade, apresentado em formato decimal para facilitar a interpretação.
-   **Atributos**: Seis colunas (STR, DEX, CON, INT, WIS, CHA) contendo os atributos principais, simplificados para valores numéricos.

### Correlação das Variáveis

Após selecionar as variáveis, o próximo passo foi explorar a correlação entre elas para entender como se relacionam com nossos dados.

Identificamos várias correlações significativas, destacadas nas áreas mais escuras do heatmap. Um achado interessante foi a correlação nula entre o atributo de Destreza (DEX) e os outros atributos, indicando que este atributo tem pouca relação com os demais

![](https://media.licdn.com/dms/image/v2/D4D12AQHqRtfLW8HjJg/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1718903536105?e=1734566400&v=beta&t=xX1rLXiUSOEAjX_n0WSodspkX3h3LZTIFebBKCPsZK8)

.

### Análise Fatorial e PCA

Iniciamos a análise fatorial utilizando o PCA para reduzir a dimensionalidade dos dados e identificar padrões subjacentes.

Após calcular os autovalores, decidimos manter três fatores principais, pois dois deles tinham valores significativos (> 1). A inclusão do terceiro fator, com valor próximo a 1, permitiu explicar uma variação acumulada de 82%, o que é considerado bastante informativo para nossa análise.

![](https://media.licdn.com/dms/image/v2/D4D12AQFZOKYdOk9Olg/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1718903551444?e=1734566400&v=beta&t=kYz-cxwKr54N9yYzN9tDhCSg--F2opSCvVlCHBv4MTE)

### Interpretação dos Fatores

Os três fatores selecionados foram interpretados em relação às variáveis originais. O primeiro fator agrupou variáveis que apresentaram alta correlação entre si, o segundo destacou o atributo de Destreza (DEX), e o terceiro revelou informações sobre a distância percorrida a pé (ft speed).

![](https://media.licdn.com/dms/image/v2/D4D12AQE0e6vfJLMKiA/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1718905965072?e=1734566400&v=beta&t=AEd-sToZx3sc7BMVddEnNZtULrfSNB4yfc7pLnB5kmQ)

### Criação do Ranking e Normalização

Depois de criamos nossos fatores, estava na hora de criarmos um ranking único para nos dar o valor combinado dos nossos fatores. multiplicando os valores dos componentes principais de cada observação pelas variâncias correspondentes dos componentes principais. Essa medida composta foi normalizada para uma escala de 0 a 100, representando a força dos monstros de forma comparável.

![](https://media.licdn.com/dms/image/v2/D4D12AQFw3I9LzuXvcw/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1718905986641?e=1734566400&v=beta&t=pFxYERlkiK5VlEUcWflPG8dzSXT4lDT4rvLppwIDclE)

E é isso meus amigos, inicialmente tinhamos que olhar em 10 variáveis para identificar o perigo dos nossos inimigos, mas agora depois da análise fatorial podemos identificar o perigo deles vendo apenas um valor depois da diminuição da dimensionalidade

Nos vemos no próximo artigo, o que será que vem por ai?

