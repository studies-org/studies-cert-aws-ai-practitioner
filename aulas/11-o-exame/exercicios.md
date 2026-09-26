# Exercícios — 11. O Exame

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_

## Questões

### 1. Uma empresa precisa de um chatbot sobre 10 mil documentos internos atualizados semanalmente, com o MENOR esforço operacional. Qual solução atende melhor?
- A) Fine-tuning semanal de um FM com os documentos
- B) Bedrock Knowledge Bases (RAG gerenciado)
- C) Construir um pipeline próprio com Lambda, embeddings customizados e OpenSearch autogerenciado
- D) Treinar um modelo do zero no SageMaker

### 2. Qual é a estratégia correta diante de uma questão cuja resposta você desconhece?
- A) Deixar em branco para evitar a penalidade por erro
- B) Eliminar as alternativas absurdas, marcar para revisão e sempre responder algo
- C) Escolher sempre a alternativa mais longa
- D) Pular e não voltar, para economizar tempo

### 3. Uma questão pergunta pela solução "MOST cost-effective" para processar 5 milhões de documentos sem exigência de latência. O que isso indica?
- A) Que várias alternativas podem funcionar, e a palavra-chave de custo aponta para batch inference
- B) Que a resposta deve ser sempre o maior modelo disponível
- C) Que a latência é o critério decisivo
- D) Que a solução deve usar Provisioned Throughput

### 4. Quais domínios concentram a maior parte do exame AIF-C01?
- A) Segurança e Governança, somando 52%
- B) Fundamentos de IA Generativa e Aplicações de Foundation Models, somando 52%
- C) Fundamentos de IA/ML, com 60%
- D) IA Responsável, com 40%

### 5. Um candidato precisa converter texto em áudio para uma URA. Qual serviço é o correto?
- A) Amazon Transcribe
- B) Amazon Polly
- C) Amazon Comprehend
- D) Amazon Translate

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — Três palavras-chave decidem: "documentos internos" → **RAG**; "atualizados semanalmente" → **elimina fine-tuning**; "menor esforço operacional" → **elimina construir o pipeline manualmente**. Resposta: **Knowledge Bases**, o RAG gerenciado do Bedrock.

2. **B** — **Não há penalidade por erro** na AWS, então deixar em branco é estritamente pior que chutar. A técnica correta é eliminar os distratores óbvios, marcar para revisão e voltar na segunda passada — mas **sempre deixando uma resposta marcada**.

3. **A** — Palavras como **MOST cost-effective**, **LEAST operational overhead** e **FASTEST** existem justamente porque **várias alternativas funcionam tecnicamente**. Elas são o critério de desempate. Volume alto + sem exigência de latência + custo mínimo = **batch inference** (~50% de desconto).

4. **B** — **Fundamentos de IA Generativa (24%)** + **Aplicações de Foundation Models (28%)** = **52%**. Por isso Bedrock, prompt engineering e RAG merecem a maior fatia do seu tempo de estudo.

5. **B** — **Polly = texto → fala (TTS)**. Transcribe faz o inverso (fala → texto). Esse par invertido é um dos erros mais comuns do exame — memorize pela inicial: **P**olly **P**roduz áudio.

</details>
