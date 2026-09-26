# 8. Machine Learning Não Supervisionada

> Seção: AI — Inteligência Artificial · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

No **aprendizado não supervisionado**, os dados **não têm rótulos**. O modelo precisa descobrir estrutura escondida sozinho. A pergunta muda de "qual é a resposta certa?" para "que padrões existem aqui?". A palavra-chave numa questão é **"sem rótulos"**, **"descobrir grupos"** ou **"não sabemos as categorias de antemão"**.

As três tarefas principais são: **Clustering** (agrupamento), **Redução de dimensionalidade** e **Detecção de anomalias**. No **clustering**, o algoritmo agrupa exemplos semelhantes — o caso clássico é segmentação de clientes, onde você não sabe quais são os segmentos até o modelo revelá-los. O algoritmo mais cobrado é o **k-means**, em que você define *k* (o número de clusters) e o algoritmo posiciona os centroides iterativamente.

A **redução de dimensionalidade** comprime muitas features em poucas, preservando o máximo de informação. O algoritmo emblemático é o **PCA (Principal Component Analysis)**. Serve para visualização, para reduzir custo computacional e para mitigar a "maldição da dimensionalidade". A **detecção de anomalias** encontra pontos que fogem do padrão — fraude, falha de equipamento, intrusão de rede — e o algoritmo da AWS aqui é o **Random Cut Forest (RCF)**, usado no SageMaker, no Kinesis Data Analytics e no CloudWatch Anomaly Detection.

Um quarto tipo aparece de vez em quando: **regras de associação** (*market basket analysis*), que descobre que "quem compra pão e manteiga tende a comprar leite".

Um ponto conceitual importante: **embeddings**, que serão centrais no RAG (aula 23), são vetores numéricos que representam o significado de um texto ou imagem. Textos com sentido semelhante ficam próximos no espaço vetorial — e essa proximidade é justamente o tipo de estrutura que métodos não supervisionados exploram.

Existe ainda o **aprendizado semi-supervisionado**, que combina uma pequena quantidade de dados rotulados com um grande volume de dados não rotulados — útil quando rotular é caro.

## 🎓 Pontos-chave para a prova

- Não supervisionado = **dados sem rótulos**; o objetivo é descobrir estrutura.
- **Clustering** (k-means) → segmentação de clientes, agrupamento de documentos.
- **Redução de dimensionalidade** (PCA) → compressão de features, visualização.
- **Detecção de anomalias** (Random Cut Forest) → fraude, falhas, outliers.
- Se a questão diz "não sabemos as categorias de antemão", é **não supervisionado**.
- Se diz "temos o histórico com o resultado conhecido", é **supervisionado**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Clustering | Agrupar exemplos semelhantes sem rótulos prévios |
| k-means | Algoritmo de clustering baseado em *k* centroides |
| PCA | Principal Component Analysis — redução de dimensionalidade |
| Random Cut Forest | Algoritmo AWS de detecção de anomalias |
| Anomalia (outlier) | Ponto que desvia significativamente do padrão |
| Embedding | Vetor numérico que representa o significado de um dado |
| Semi-supervisionado | Mistura de poucos dados rotulados com muitos não rotulados |
| Dimensionalidade | Número de features de um conjunto de dados |

## 💡 Exemplo prático / caso de uso

Um varejista tem 2 milhões de clientes e nenhuma segmentação definida. Em vez de inventar categorias no achismo, aplica **k-means** sobre frequência de compra, ticket médio e recência. O algoritmo revela cinco grupos naturais — entre eles "compradores de alto valor e baixa frequência" e "caçadores de promoção". Ninguém rotulou nada; a estrutura emergiu dos dados. Se depois o time quiser **prever** a qual grupo um novo cliente pertence, aí sim vira um problema **supervisionado**, usando os clusters como rótulos.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
