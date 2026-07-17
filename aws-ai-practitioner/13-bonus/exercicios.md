# Exercícios — 13. Bônus (revisão geral)

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_, 6-_, 7-_, 8-_, 9-_, 10-_

## Questões

### 1. Uma empresa quer que o modelo escreva sempre no tom e no formato institucional da marca, de forma persistente. Qual técnica é a adequada?
- A) RAG com Knowledge Base
- B) Fine-tuning
- C) Aumentar a temperature
- D) Prompt caching

### 2. Qual conjunto descreve corretamente a ordem crescente de custo e esforço?
- A) Fine-tuning < prompt engineering < RAG < treinar do zero
- B) Prompt engineering < RAG < fine-tuning < continued pre-training < treinar do zero
- C) RAG < prompt engineering < treinar do zero < fine-tuning
- D) Treinar do zero < fine-tuning < RAG < prompt engineering

### 3. Um assistente de IA precisa consultar uma API de estoque e criar um pedido. Qual recurso do Bedrock é necessário?
- A) Knowledge Bases
- B) Guardrails
- C) Agents com Action Groups
- D) Model Evaluation

### 4. Qual métrica é apropriada para avaliar um sistema de tradução automática?
- A) ROUGE
- B) BLEU
- C) RMSE
- D) Recall

### 5. Uma questão pede a solução com "LEAST operational overhead" para RAG sobre documentos no S3. Qual é a resposta esperada?
- A) Construir o pipeline com Lambda, embeddings próprios e OpenSearch autogerenciado
- B) Bedrock Knowledge Bases
- C) Treinar um modelo do zero no SageMaker
- D) Instalar um banco vetorial em instâncias EC2

### 6. Qual afirmação sobre viés algorítmico é correta?
- A) Remover as colunas de raça e gênero elimina o viés do modelo
- B) Variáveis proxy podem reproduzir o viés mesmo sem o atributo sensível explícito
- C) Viés só existe em modelos de deep learning
- D) O viés é sempre introduzido pelo algoritmo, nunca pelos dados

### 7. Quais recursos continuam cobrando mesmo sem uso? (Escolha a melhor opção)
- A) Modelos habilitados em Model access do Bedrock
- B) Endpoints real-time do SageMaker, índices Kendra, OCUs do OpenSearch e assinaturas do Q Business
- C) Prompts salvos e Guardrails criados
- D) Buckets S3 vazios

### 8. Um pipeline precisa converter gravações de call center em texto e depois analisar o sentimento. Qual sequência é correta?
- A) Polly → Comprehend
- B) Transcribe → Comprehend
- C) Comprehend → Transcribe
- D) Textract → Translate

### 9. Qual serviço deve ser usado para detectar viés e explicar previsões de um modelo de crédito?
- A) SageMaker Model Monitor
- B) SageMaker Clarify
- C) Bedrock Guardrails
- D) AWS Config

### 10. Uma aplicação recebe respostas erradas porque o FM desconhece os produtos lançados este mês. Qual é a causa e a solução?
- A) Temperature muito alta; reduzir para 0
- B) Knowledge cutoff do modelo; implementar RAG com dados atualizados
- C) Max tokens insuficiente; aumentar o limite
- D) Falta de Guardrails; ativar content filters

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — **Estilo, tom e formato persistentes** são o caso clássico de **fine-tuning**: o comportamento é gravado nos pesos, o prompt fica menor e a resposta fica consistente. RAG serve para conhecimento factual, não para estilo.

2. **B** — A hierarquia é **prompt engineering < RAG < fine-tuning < continued pre-training < treinar do zero**, tanto em custo quanto em esforço. A prova espera que você sempre comece pela opção mais barata que resolve.

3. **C** — Consultar APIs e **executar ações** exige **Agents com Action Groups** (schema OpenAPI + Lambda). Knowledge Bases apenas recupera informação; Guardrails apenas filtra conteúdo.

4. **B** — **BLEU** avalia **tradução** (precisão de n-gramas contra referências). **ROUGE** avalia **sumarização**. RMSE é de regressão e recall é de classificação.

5. **B** — "**LEAST operational overhead**" aponta sempre para o **serviço gerenciado**. **Knowledge Bases** entrega chunking, embeddings, indexação e sincronização prontos. As outras opções são exatamente o trabalho manual que a palavra-chave manda evitar.

6. **B** — O viés vive nos **dados**, e **variáveis proxy** (CEP, nome, escola) o carregam mesmo sem o atributo sensível na tabela. É por isso que a mitigação exige medir **disparate impact** (com Clarify), e não apenas remover colunas.

7. **B** — Todos são **capacidade provisionada**: endpoint real-time do SageMaker cobra por hora, Kendra cobra por hora de índice, OpenSearch Serverless cobra por OCU e o Q Business cobra por assinatura de usuário. Habilitar um modelo no Bedrock ou criar um Guardrail não gera custo por si só.

8. **B** — **Transcribe** converte a fala em texto e o **Comprehend** analisa o sentimento desse texto. Polly faria o caminho inverso (texto → fala), e Textract é para documentos.

9. **B** — **SageMaker Clarify** cobre exatamente os dois requisitos: **detecção de viés** (pré e pós-treino) e **explicabilidade** via SHAP — indispensável num modelo de crédito sujeito a exigência regulatória de explicação.

10. **B** — O modelo tem um **knowledge cutoff**: ele não conhece nada posterior ao seu treino, e produtos lançados este mês estão fora dele. A solução é **RAG**, dando acesso aos dados atuais. Ajustar temperature ou max tokens não cria conhecimento que o modelo nunca teve.

</details>
