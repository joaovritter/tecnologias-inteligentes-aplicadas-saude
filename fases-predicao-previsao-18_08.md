# Fases de um Projeto de Predição/Previsão

## Segredo: qualidade da amostra
- O resultado do modelo depende diretamente da qualidade da amostra usada
- **Amostra**: conjunto de indivíduos, elementos, objetos ou cenários que representam o problema
- Amostra ruim (poucos dados, dados enviesados, dados incompletos) = modelo ruim, não importa o algoritmo usado

## Fase 1 — Entender o problema (predição ou previsão)
- Primeiro passo é definir claramente o que se quer resolver
- Precisa identificar se o problema é de **predição** (classificar/estimar algo sem depender do tempo) ou **previsão** (estimar algo futuro com base em série temporal)
- Essa definição influencia todas as fases seguintes: que tipo de dado buscar, que modelo aplicar, como avaliar o resultado

## Fase 2 — Fonte de dados/amostras para o treinamento
- Buscar de onde vêm os dados que vão treinar o modelo (banco de dados, planilhas, APIs, sensores, etc.)
- Quanto mais representativa e maior a amostra, melhor tende a ser o modelo
- Nessa fase também se avalia se os dados têm qualidade suficiente (completude, confiabilidade, volume)

## Fase 3 — ETL (Extract, Transform, Load) → Pandas
- **Extract**: extrair os dados da fonte original
- **Transform**: limpar e preparar os dados (tratar valores faltantes, remover duplicados, normalizar, converter tipos, etc.)
- **Load**: carregar os dados já tratados numa estrutura pronta para uso (ex.: DataFrame)
- No Python, a biblioteca **Pandas** é a ferramenta padrão pra fazer esse processo, manipulando os dados em formato tabular (DataFrame)

## Fase 4 — Aplicar diferentes modelos para identificar o adequado
- Testar mais de um algoritmo/modelo de machine learning nos dados preparados
- Comparar o desempenho de cada um usando métricas (accuracy, precision, recall, f1-score, etc.)
- Escolher o modelo que apresenta o melhor equilíbrio entre desempenho e adequação ao problema
- Não existe "modelo universal" — o melhor depende do tipo de dado e do problema

## Resumo visual do fluxo
1. Entender o problema → 2. Buscar os dados → 3. Tratar os dados (ETL/Pandas) → 4. Testar modelos → escolher o melhor
