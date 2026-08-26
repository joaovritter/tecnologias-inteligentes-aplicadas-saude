# Tecnologias Inteligentes Aplicadas à Saúde

## 1. Áreas x aplicação
| Área | Aplicação |
|---|---|
| Medicina/Odontologia | Diagnóstico |
| Enfermagem | Predição e previsão |
| Farmácia | Diagnóstico |

## 2. Frentes de aplicação da IA na saúde
- **Diagnóstico** → reconhecer padrões → precisa de volume de dados → *algoritmos de aprendizado de máquina*
  - Ex.: pacientes com febre eram atendidos antes → padrão identificado após muitas observações
- **Monitoramento** (sensoriamento e atuação) → automação
- **Predição e previsão** → reconhecer padrões → volume de dados → *algoritmos de mineração de dados*
- Predição: classificação = categorização = **etiquetação**
- Previsão: séries temporais = tempo contínuo = **projeção**

## 3. SAD x Sistema de Recomendação
- **SAD**: decide com base em histórico geral de evidências (não só do usuário)
- **Recomendação**: recomenda com base em amostras do usuário específico
- SAD pode ter um sistema de recomendação embutido

## 4. Técnicas de IA da disciplina
**Usadas:**
- Redes neurais → aprendizagem → reconhecimento de padrões (deep learning, machine learning, mineração de dados)
  - mineração de dados = encontrar ouro => o padrão
- Sistemas multiagentes

**Não usadas:**
- Métodos de busca → raciocínio
- Algoritmos genéticos → raciocínio

# Predição x Previsão

## Predição
- Termo mais amplo
- Estima valor/classe/comportamento futuro, presente ou passado desconhecido
- Pode ser classificação (rótulos) ou regressão (números)
- Não precisa envolver o futuro
- Ex.: cliente vai cancelar assinatura; idade de uma pessoa numa foto

## Previsão
- Termo mais específico, ligado a séries temporais
- Estima valores futuros com base em histórico
- Sempre envolve tempo/futuro
- Ex.: temperatura de amanhã; faturamento do próximo trimestre

## Diferença rápida
| | Predição | Previsão |
|---|---|---|
| Escopo | Mais amplo | Mais específico (séries temporais) |
| Passado/presente desconhecido? | Sim | Não |
| Sempre envolve futuro? | Não | Sim |
| Exemplo | Classificar cliente como "alto risco" | Prever faturamento do mês que vem |

## Na mineração de dados
- Modelo não depende do tempo (classificação de imagem, detecção de fraude) → **predição**
- Modelo usa histórico temporal pra estimar o que vai acontecer → **previsão**

## Mais exemplos

**Predição:**
- Diagnosticar se um exame de imagem indica tumor maligno ou benigno
- Classificar um e-mail como spam ou não spam
- Estimar o gênero de uma pessoa a partir da voz
- Identificar se uma transação de cartão é fraudulenta

**Previsão:**
- Prever a demanda de estoque de um produto no próximo mês
- Estimar o número de pacientes que vão dar entrada num hospital na próxima semana
- Prever o preço de uma ação daqui a 30 dias
- Projetar o consumo de energia elétrica de uma cidade no verão

## Truque pra lembrar na prova
- Pergunta envolve tempo/futuro? → **Previsão**
- Pergunta é sobre classificar/estimar algo que já existe, só não se sabe qual é? → **Predição**
