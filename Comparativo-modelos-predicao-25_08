# Comparativo entre Modelos de Predição — Base Glicose

Objetivo: testar vários modelos de classificação pra descobrir qual prevê melhor os níveis de glicemia com base em variáveis como insulina, calorias, carboidratos, sono e atividade física (padel).

---

## 1. Importar bibliotecas

```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix, f1_score

# Modelos de classificação
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.naive_bayes import GaussianNB
from sklearn.neighbors import KNeighborsClassifier
from sklearn.svm import SVC
```

Traz tudo que vai ser usado: ferramentas de divisão de dados, padronização, métricas de avaliação e os 7 algoritmos de classificação que vão competir entre si.

---

## 2. Carregar os dados

```python
url = 'https://raw.githubusercontent.com/alexandrezamberlan/tias/refs/heads/main/predicao_previsao_codigos_exemplos/glicose_data.csv'
df = pd.read_csv(url)
```

Lê o CSV direto de uma URL e transforma em DataFrame do Pandas — a estrutura de tabela que o Python usa pra manipular dados.

---

## 3. Definir features e variável alvo

```python
features = ['INSULINA', 'KCAL', 'CARB', 'SONO', 'padel']
target = 'GLICEMIA'

X = df[features]
y = df[target]
```

- **Features (X)**: as variáveis de entrada, o que o modelo vai usar pra "adivinhar" o resultado
- **Target (y)**: a variável que se quer prever (GLICEMIA)

---

## 4. Dividir em treino e teste

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=42, stratify=y)
```

- Separa 70% dos dados pra treinar o modelo e 30% pra testar (o modelo nunca viu esses dados)
- `stratify=y` mantém a proporção das classes igual nos dois conjuntos (evita treino desbalanceado)
- `random_state=42` garante que a divisão seja sempre a mesma se rodar de novo

---

## 5. Padronizar os dados

```python
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

O `StandardScaler` coloca todas as features na mesma escala (média 0, desvio padrão 1). Necessário porque modelos como SVM e KNN calculam distância entre pontos — se uma feature varia de 0 a 1000 e outra de 0 a 1, a maior domina o cálculo sem motivo real.

**Exemplo prático — cuidado antes de padronizar:**
Imagina um formulário com escala Likert (1 a 5) onde a maioria das respostas varia normalmente, mas em 2 a cada 200 respondentes a pessoa marca "5" em tudo, sem variação nenhuma — um padrão de resposta claramente extremo e não representativo do comportamento real. Antes de padronizar, vale identificar esses casos: como é uma exceção rara (1% da amostra) e distorce a distribuição, o ideal é descartar essas linhas do dataset. Se isso não for feito, a padronização vai "esticar" a escala pra acomodar esses outliers, prejudicando a qualidade dos dados dos outros 198 respondentes normais.

---

## 6. Definir os modelos

```python
modelos = {
    'Logistic Regression': LogisticRegression(max_iter=1000),
    'Decision Tree': DecisionTreeClassifier(),
    'Random Forest': RandomForestClassifier(),
    'KNN': KNeighborsClassifier(),
    'Naive Bayes': GaussianNB(),
    'SVM': SVC(),
    'Gradient Boosting': GradientBoostingClassifier()
}
```

Um dicionário com 7 algoritmos diferentes, cada um com uma lógica própria de classificação (árvore, distância, probabilidade, etc.). A ideia é testar todos e comparar.

---

## 7. Treinar, prever e avaliar cada modelo

```python
resultados = []

for nome, modelo in modelos.items():
    modelo.fit(X_train, y_train)
    y_pred = modelo.predict(X_test)

    acc = accuracy_score(y_test, y_pred)
    f1 = f1_score(y_test, y_pred, average='macro', zero_division=0)

    resultados.append((nome, acc, f1))

    print(f"Modelo: {nome}")
    print(f"Acurácia: {acc:.4f}")
    print(f"F1-Score (Macro): {f1:.4f}")
    print("Relatório de Classificação:")
    print(classification_report(y_test, y_pred, zero_division=0))
    print("Matriz de Confusão:")
    print(confusion_matrix(y_test, y_pred))
    print("-" * 60)
```

Para cada modelo:
1. `fit()` — treina com os dados de treino
2. `predict()` — faz a previsão nos dados de teste
3. Calcula **acurácia** e **F1-Score macro** (média do F1 entre todas as classes, sem dar peso pra classe mais frequente)
4. Imprime o `classification_report` (precision, recall, f1 por classe) e a `confusion_matrix`

---

## 8. Ranking final

```python
resultados.sort(key=lambda x: x[2], reverse=True)

print("\nRanking Final dos Modelos:")
print(f"{'Modelo':<25} {'Acurácia':<10} {'F1-Score (Macro)':<15}")
print("-" * 50)
for nome, acc, f1 in resultados:
    print(f"{nome:<25} {acc:<10.4f} {f1:<15.4f}")
```

Ordena os modelos pelo F1-Score macro (do maior pro menor) e imprime a tabela final de comparação.

**Exemplo de saída:**
```
Ranking Final dos Modelos:
Modelo                   Acurácia   F1-Score (Macro)
--------------------------------------------------
Random Forest            0.9200     0.9133
Gradient Boosting        0.9100     0.9041
Logistic Regression      0.8900     0.8800
...
```

---

## O que essa comparação mostra
- **Acurácia**: o quão certo o modelo está no geral
- **F1-Score Macro**: o quão bem ele equilibra o desempenho entre todas as classes (bom pra dados desbalanceados)
- **Matriz de confusão e classificação detalhada**: onde e como cada modelo erra
- **Ranking por F1 Macro**: melhor critério pra escolher o modelo em problemas multiclasse, já que a acurácia sozinha pode enganar
