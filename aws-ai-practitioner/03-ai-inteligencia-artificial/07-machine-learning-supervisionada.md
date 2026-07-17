# 7. Machine Learning Supervisionada

> Seção: AI — Inteligência Artificial · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

No **aprendizado supervisionado**, o modelo aprende a partir de dados **rotulados** — cada exemplo traz as features de entrada e a resposta correta (*label*). O objetivo é aprender a função que mapeia entrada → saída e depois aplicá-la a dados novos. A palavra-chave que denuncia supervisionado numa questão é **"rotulado"** ou **"histórico com resultado conhecido"**.

Existem **dois tipos de problema supervisionado**. **Classificação** prevê uma categoria discreta: e-mail é spam ou não (binária), a foto é gato/cachorro/pássaro (multiclasse), o cliente vai ou não cancelar. **Regressão** prevê um valor numérico contínuo: o preço da casa, a temperatura de amanhã, a receita do próximo trimestre. Confundir os dois é um erro frequente — "prever quanto" é regressão, "prever qual" é classificação.

As **métricas de avaliação** diferem conforme o tipo. Para classificação: **Accuracy** (proporção de acertos totais), **Precision** (dos que previ como positivos, quantos eram mesmo — penaliza falso positivo), **Recall** (dos positivos reais, quantos eu encontrei — penaliza falso negativo), **F1-score** (média harmônica de precision e recall) e **AUC-ROC** (capacidade de separar as classes). Para regressão: **MSE**, **RMSE**, **MAE** e **R²**.

O trade-off precision/recall é um clássico da prova. Em **detecção de fraude ou diagnóstico de câncer**, deixar passar um caso positivo é gravíssimo — então **priorize recall**. Em um **filtro de spam**, marcar um e-mail legítimo como spam é o dano maior — então **priorize precision**. Quando as classes são muito desbalanceadas (99% de transações legítimas), **accuracy é enganosa**: um modelo que diz "nunca é fraude" acerta 99% e é inútil. Use F1 ou AUC nesses casos.

A ferramenta para ler tudo isso é a **matriz de confusão**, que cruza previsto × real em quatro quadrantes: **VP** (verdadeiro positivo), **VN** (verdadeiro negativo), **FP** (falso positivo — "alarme falso") e **FN** (falso negativo — "deixou passar").

## 🎓 Pontos-chave para a prova

- Supervisionado exige **dados rotulados**.
- **Classificação** → categoria discreta. **Regressão** → valor numérico contínuo.
- **Precision** penaliza falso positivo; **Recall** penaliza falso negativo.
- Fraude/doença → **maximize recall**. Spam → **maximize precision**.
- Com classes **desbalanceadas**, accuracy engana — prefira **F1** ou **AUC-ROC**.
- Regressão usa **MSE / RMSE / MAE / R²**, nunca accuracy.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Label | Resposta correta conhecida de um exemplo de treino |
| Classificação | Prever uma categoria discreta |
| Regressão | Prever um valor numérico contínuo |
| Accuracy | (VP+VN) / total — proporção de acertos |
| Precision | VP / (VP+FP) — confiabilidade das previsões positivas |
| Recall (Sensibilidade) | VP / (VP+FN) — cobertura dos positivos reais |
| F1-score | Média harmônica entre precision e recall |
| AUC-ROC | Área sob a curva ROC; poder de separação entre classes |
| Matriz de confusão | Tabela cruzando previsões e valores reais (VP/VN/FP/FN) |
| RMSE | Raiz do erro quadrático médio; métrica de regressão |

## 💡 Exemplo prático / caso de uso

Um hospital cria um modelo de triagem para detectar uma doença grave. Ele tem 97% de accuracy, mas só 40% de recall — está deixando passar 6 em cada 10 doentes. Como o custo de um **falso negativo** (mandar um doente para casa) é muito maior que o de um **falso positivo** (pedir um exame extra), a equipe ajusta o limiar de decisão para elevar o recall, aceitando queda na precision. A accuracy alta era um artefato do desbalanceamento das classes.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
