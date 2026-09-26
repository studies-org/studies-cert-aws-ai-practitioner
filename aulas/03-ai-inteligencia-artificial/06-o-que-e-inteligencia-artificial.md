# 6. O Que é Inteligência Artificial

> Seção: AI — Inteligência Artificial · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**Inteligência Artificial (IA)** é o campo amplo que busca fazer máquinas executarem tarefas que normalmente exigiriam inteligência humana: perceber, raciocinar, aprender e decidir. A relação entre os termos que caem na prova é de **círculos concêntricos**: IA contém **Machine Learning (ML)**, que contém **Deep Learning (DL)**, que contém a **IA Generativa (GenAI)**.

**Machine Learning** é o subconjunto da IA em que o sistema **aprende padrões a partir de dados** em vez de seguir regras escritas à mão. Você não programa "se o e-mail contém 'promoção' então é spam"; você mostra milhares de e-mails rotulados e o algoritmo descobre os padrões sozinho. **Deep Learning** usa **redes neurais com muitas camadas** e se destaca em dados não estruturados — imagens, áudio e texto. **IA Generativa** usa deep learning para **criar conteúdo novo** (texto, imagem, código, áudio) em vez de apenas classificar ou prever.

O vocabulário de dados é cobrado com frequência. **Dados estruturados** vivem em tabelas com esquema fixo (banco relacional, CSV). **Semiestruturados** têm marcação mas não esquema rígido (JSON, XML). **Não estruturados** não têm formato predefinido (texto livre, imagens, vídeo, áudio) — e é justamente aí que deep learning brilha.

O ciclo de vida de ML também aparece: **coleta de dados → preparação/feature engineering → treinamento → avaliação → implantação (deployment) → monitoramento**. No treinamento, os dados são divididos em **training set** (o modelo aprende), **validation set** (ajusta hiperparâmetros) e **test set** (avalia de forma imparcial em dados nunca vistos).

Dois problemas fundamentais fecham a aula. **Overfitting**: o modelo decora o treino e vai mal em dados novos — alta acurácia no treino, baixa no teste. **Underfitting**: o modelo é simples demais e vai mal em ambos. Um **viés (bias)** alto tende a underfitting; uma **variância (variance)** alta tende a overfitting — e o objetivo é equilibrar os dois.

## 🎓 Pontos-chave para a prova

- Hierarquia: **IA ⊃ Machine Learning ⊃ Deep Learning ⊃ IA Generativa**.
- ML **aprende com dados**; sistemas baseados em regras são programados explicitamente.
- **Deep Learning** = redes neurais multicamadas, forte em dados **não estruturados**.
- **Overfitting** = ótimo no treino, ruim no teste (alta variância). **Underfitting** = ruim em ambos (alto viés).
- Divisão de dados: **training / validation / test** — o test set jamais é usado para ajustar o modelo.
- **Inferência** é usar o modelo treinado para gerar previsões; **treinamento** é aprender os parâmetros.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Inteligência Artificial | Campo amplo de máquinas executando tarefas cognitivas |
| Machine Learning | Subconjunto da IA que aprende padrões a partir de dados |
| Deep Learning | ML com redes neurais profundas; forte em dados não estruturados |
| IA Generativa | Subconjunto do DL que cria conteúdo novo |
| Overfitting | Modelo decora o treino e generaliza mal |
| Underfitting | Modelo simples demais; erra treino e teste |
| Inferência | Uso do modelo treinado para produzir previsões |
| Feature | Variável de entrada usada pelo modelo |
| Label | Resposta correta conhecida usada no treino supervisionado |
| Dados não estruturados | Texto, imagem, áudio e vídeo, sem esquema fixo |

## 💡 Exemplo prático / caso de uso

Uma seguradora treina um modelo para prever fraude. Na validação ele acerta 99% no conjunto de treino, mas só 62% no conjunto de teste — sinal clássico de **overfitting**. As correções típicas são: coletar mais dados, simplificar o modelo, aplicar regularização ou usar validação cruzada. Perceber o diagnóstico a partir do par de métricas (treino alto / teste baixo) é exatamente o que a prova pede.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
