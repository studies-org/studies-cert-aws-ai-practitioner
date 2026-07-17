# Exercícios — 05. Amazon Bedrock

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_, 6-_, 7-_, 8-_, 9-_, 10-_

## Questões

### 1. Uma empresa precisa que seu chatbot responda com base em políticas internas atualizadas semanalmente. Qual abordagem é a mais adequada?
- A) Fine-tuning semanal do Foundation Model
- B) RAG com uma Knowledge Base do Bedrock
- C) Aumentar a janela de contexto do modelo
- D) Continued pre-training com os documentos

### 2. Qual afirmação sobre a privacidade dos dados no Amazon Bedrock é correta?
- A) Prompts são usados para melhorar os modelos base dos provedores
- B) Prompts e respostas não são usados para treinar os modelos base nem compartilhados com os provedores
- C) Os dados são compartilhados apenas com o provedor do modelo escolhido
- D) A privacidade só é garantida com Provisioned Throughput

### 3. Uma carga processa 3 milhões de documentos durante a madrugada, sem exigência de latência. Qual modo de inferência minimiza o custo?
- A) On-Demand com streaming
- B) Provisioned Throughput de 6 meses
- C) Batch inference
- D) Real-time inference com prompt caching

### 4. Qual recurso do Bedrock Guardrails ajuda diretamente a reduzir alucinações?
- A) Denied topics
- B) Word filters
- C) Contextual grounding check
- D) Sensitive information filters

### 5. Qual é a diferença central entre fine-tuning e continued pre-training?
- A) Fine-tuning usa dados rotulados (prompt/completion); continued pre-training usa grandes volumes de texto não rotulado do domínio
- B) Fine-tuning é não supervisionado; continued pre-training é supervisionado
- C) Fine-tuning altera o modelo base do provedor; continued pre-training cria uma cópia
- D) Não há diferença técnica, apenas de nomenclatura

### 6. Um agente precisa consultar o status de um pedido em um banco de dados e emitir um reembolso. Qual recurso do Bedrock viabiliza isso?
- A) Knowledge Bases
- B) Agents com Action Groups implementados por Lambda
- C) Model Evaluation
- D) Guardrails com denied topics

### 7. Ao invocar um modelo, a aplicação recebe `AccessDeniedException`. Quais são as duas causas mais prováveis? (Escolha a melhor opção)
- A) Temperature inválida ou max tokens excedido
- B) O modelo não foi habilitado em Model access naquela Região, ou falta a permissão IAM `bedrock:InvokeModel`
- C) O prompt excedeu a janela de contexto
- D) O Guardrail bloqueou a saída

### 8. Qual métrica é tipicamente usada para avaliar tarefas de sumarização?
- A) BLEU
- B) ROUGE
- C) RMSE
- D) AUC-ROC

### 9. Em uma Knowledge Base, o que acontece se o sync da data source não for executado?
- A) A base funciona normalmente, com sync automático a cada consulta
- B) Os documentos não são chunked nem indexados, e a base não retorna resultados
- C) O modelo usa os documentos direto do S3 sem indexação
- D) O sync só é necessário para fontes que não sejam S3

### 10. Uma empresa quer reduzir o custo de um assistente que envia o mesmo system prompt longo em todas as chamadas. Qual otimização é mais direta?
- A) Prompt caching
- B) Aumentar a temperature
- C) Migrar para Provisioned Throughput
- D) Trocar o vector store

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — Conhecimento **que muda com frequência** pede **RAG**. Basta reindexar os documentos; não há re-treino. Fine-tuning semanal seria caro, lento e cristalizaria informação que já nasce desatualizada.

2. **B** — O Bedrock garante que **seus prompts e respostas não treinam os modelos base** e **não são compartilhados com os provedores**. Essa garantia vale em todos os modos de cobrança, não só no Provisioned.

3. **C** — **Batch inference** processa de forma assíncrona via S3 com cerca de **50% de desconto**. É exatamente o caso: volume alto, sem exigência de latência.

4. **C** — **Contextual grounding check** verifica se a resposta está fundamentada na fonte fornecida e é relevante à pergunta, bloqueando saídas abaixo do limiar. Denied topics bloqueia assuntos, word filters bloqueia termos e PII filters protege dados sensíveis.

5. **A** — **Fine-tuning é supervisionado** com pares **prompt→completion** rotulados; **continued pre-training é auto-supervisionado** com grande volume de **texto não rotulado** do domínio. Ambos criam uma cópia privada e nenhum altera o modelo do provedor.

6. **B** — Consultar sistemas e **executar ações** é o papel dos **Agents**, cujas ferramentas são declaradas em **Action Groups** (schema OpenAPI) e implementadas por **Lambda**. Knowledge Bases apenas recupera informação; não age.

7. **B** — As duas camadas independentes são **model access** (habilitação por conta **e por Região**) e a **permissão IAM** (`bedrock:InvokeModel`). Faltar qualquer uma resulta em acesso negado — e a Região errada é a causa mais comum.

8. **B** — **ROUGE** é a métrica de **sumarização** (orientada a recall, compara n-gramas com um resumo de referência). **BLEU** é de **tradução**. RMSE é de regressão e AUC-ROC é de classificação.

9. **B** — O **sync** (ingestion job) é o que dispara chunking, geração de embeddings e indexação no vector store. Sem ele, o índice fica vazio e nenhuma consulta retorna resultado.

10. **A** — **Prompt caching** reaproveita o processamento de porções repetidas do prompt, reduzindo tokens cobrados e latência. Provisioned Throughput garante capacidade mas não elimina o reprocessamento do contexto repetido.

</details>
