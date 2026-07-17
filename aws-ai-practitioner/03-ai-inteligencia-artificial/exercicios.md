# Exercícios — 03. AI — Inteligência Artificial

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_, 6-_, 7-_, 8-_, 9-_, 10-_

## Questões

### 1. Qual é a relação correta entre os termos?
- A) Machine Learning ⊃ Inteligência Artificial ⊃ Deep Learning
- B) Inteligência Artificial ⊃ Machine Learning ⊃ Deep Learning ⊃ IA Generativa
- C) Deep Learning ⊃ Machine Learning ⊃ IA Generativa
- D) São quatro campos independentes e não relacionados

### 2. Uma empresa tem 5 anos de histórico de vendas e quer prever o faturamento do próximo trimestre em reais. Que tipo de problema é esse?
- A) Classificação supervisionada
- B) Regressão supervisionada
- C) Clustering não supervisionado
- D) Aprendizado por reforço

### 3. Um modelo atinge 98% de acurácia no conjunto de treino e 61% no conjunto de teste. O diagnóstico é:
- A) Underfitting
- B) Overfitting
- C) O modelo está bem calibrado
- D) Vazamento de dados no test set

### 4. Um banco quer segmentar clientes, mas não sabe quais grupos existem. Qual abordagem é adequada?
- A) Regressão linear
- B) Classificação multiclasse
- C) Clustering com k-means
- D) Aprendizado por reforço

### 5. Em um sistema de detecção de fraude, qual métrica deve ser priorizada e por quê?
- A) Precision, porque falsos positivos são o pior cenário
- B) Recall, porque deixar passar uma fraude (falso negativo) é o pior cenário
- C) Accuracy, porque resume todos os acertos
- D) RMSE, porque mede o erro médio

### 6. Por que a acurácia é uma métrica enganosa em um dataset com 99,5% de transações legítimas?
- A) Porque a acurácia não funciona em problemas binários
- B) Porque um modelo que sempre prevê "legítimo" atinge 99,5% de acurácia sendo inútil
- C) Porque a acurácia só se aplica a regressão
- D) Porque a acurácia exige dados não rotulados

### 7. Qual algoritmo AWS é tipicamente associado à detecção de anomalias?
- A) k-means
- B) PCA
- C) Random Cut Forest
- D) XGBoost

### 8. O que é RLHF?
- A) Uma técnica de compressão de modelos para reduzir custo de inferência
- B) Reinforcement Learning from Human Feedback — usa rankings humanos para treinar um reward model e alinhar o LLM
- C) Um formato de arquivo para armazenar pesos de redes neurais
- D) Um algoritmo de clustering hierárquico

### 9. Quais são os componentes do aprendizado por reforço?
- A) Features, labels, training set e test set
- B) Agente, ambiente, estado, ação, recompensa e política
- C) Encoder, decoder, atenção e embedding
- D) Prompt, contexto, instrução e saída

### 10. Qual característica define o aprendizado supervisionado?
- A) O uso de dados rotulados com a resposta correta conhecida
- B) A descoberta de estruturas ocultas em dados sem rótulo
- C) O aprendizado por tentativa e erro através de recompensas
- D) A geração de conteúdo novo a partir de um prompt

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — São círculos concêntricos: **IA ⊃ ML ⊃ DL ⊃ GenAI**. A IA Generativa é uma aplicação de Deep Learning, que por sua vez é um tipo de Machine Learning, que é um subcampo da IA.

2. **B** — Prever um **valor numérico contínuo** (faturamento em reais) a partir de dados históricos conhecidos é **regressão supervisionada**. Se fosse prever "vai crescer ou cair" (categoria), seria classificação.

3. **B** — **Overfitting** clássico: o modelo decorou o treino e não generaliza. Underfitting daria desempenho ruim em **ambos** os conjuntos. Mitigações: mais dados, regularização, modelo mais simples, validação cruzada.

4. **C** — Como **não se sabe quais grupos existem**, não há rótulos — logo, aprendizado **não supervisionado** via **clustering (k-means)**. Classificação exigiria as categorias já definidas.

5. **B** — Em fraude, um **falso negativo** (fraude que passa despercebida) causa prejuízo direto, enquanto um falso positivo apenas gera uma verificação extra. Por isso **maximiza-se o recall**. O raciocínio inverso vale para filtros de spam, onde precision importa mais.

6. **B** — Com classes muito **desbalanceadas**, um modelo trivial que sempre responde a classe majoritária alcança acurácia altíssima e recall zero para a classe de interesse. Use **F1-score** ou **AUC-ROC**.

7. **C** — **Random Cut Forest (RCF)** é o algoritmo da AWS para detecção de anomalias, disponível no SageMaker, no Kinesis Data Analytics e por trás do CloudWatch Anomaly Detection. k-means é clustering, PCA é redução de dimensionalidade e XGBoost é supervisionado.

8. **B** — **RLHF** usa comparações humanas entre respostas para treinar um **reward model**, que então guia o ajuste do LLM por aprendizado por reforço. É a técnica central de **alinhamento** de modelos de linguagem.

9. **B** — **Agente, ambiente, estado, ação, recompensa e política**. A letra A descreve aprendizado supervisionado, a C descreve a arquitetura Transformer e a D descreve componentes de um prompt.

10. **A** — A definição de supervisionado é aprender a partir de **dados rotulados** (entrada + resposta correta). B é não supervisionado, C é reforço e D descreve IA Generativa.

</details>
