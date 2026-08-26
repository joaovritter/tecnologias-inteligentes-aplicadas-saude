# Métricas do scikit-learn

## accuracy_score
- Proporção de acertos sobre o total de previsões
- Fórmula: (acertos) / (total)
- Cuidado: em dados desbalanceados pode enganar (ex.: 95% de acurácia prevendo sempre a classe majoritária)

## confusion_matrix
- Tabela que cruza classe real x classe prevista
- Mostra: verdadeiro positivo (VP), verdadeiro negativo (VN), falso positivo (FP), falso negativo (FN)
- Base pra calcular as outras métricas (precision, recall, f1)

## classification_report
- Relatório com precision, recall, f1-score e support (qtd de amostras) pra cada classe
- **Precision**: dos que o modelo previu como positivo, quantos eram mesmo (VP / (VP+FP))
- **Recall**: dos que eram realmente positivos, quantos o modelo acertou (VP / (VP+FN))
- Também mostra médias (macro avg, weighted avg)

## f1_score
- Média harmônica entre precision e recall
- Fórmula: 2 * (precision * recall) / (precision + recall)
- Útil quando tem desbalanceamento de classes e precisa de equilíbrio entre precision e recall

## Quando usar cada uma
- Acurácia: dados balanceados, visão geral rápida
- Confusion matrix: entender onde o modelo erra (tipo de erro)
- Precision: quando o custo de falso positivo é alto (ex.: marcar email bom como spam)
- Recall: quando o custo de falso negativo é alto (ex.: não detectar doença)
- F1: quando precisa de equilíbrio entre precision e recall, principalmente com classes desbalanceadas
