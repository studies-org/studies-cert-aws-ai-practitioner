# Exercícios — 08. Serviços de IA na AWS

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_, 6-_, 7-_, 8-_, 9-_, 10-_

## Questões

### 1. Uma seguradora precisa extrair pares chave-valor e tabelas de formulários de sinistro em PDF. Qual serviço é o adequado?
- A) Amazon Rekognition
- B) Amazon Textract
- C) Amazon Comprehend
- D) Amazon Kendra

### 2. Qual pipeline permite dublar automaticamente um vídeo do inglês para o português?
- A) Polly → Translate → Transcribe
- B) Transcribe → Translate → Polly
- C) Comprehend → Translate → Rekognition
- D) Textract → Translate → Polly

### 3. Um e-commerce quer exibir "recomendado para você" na home, em tempo real. Qual serviço é o correto?
- A) Amazon Forecast
- B) Amazon Personalize
- C) Amazon Kendra
- D) Amazon Comprehend

### 4. Uma empresa precisa prever a demanda de produtos nos próximos 6 meses com base no histórico de vendas, considerando sazonalidade. Qual é o tipo de problema?
- A) Recomendação, resolvido com Amazon Personalize
- B) Previsão de séries temporais, resolvido com Amazon Forecast ou SageMaker Canvas
- C) Classificação, resolvido com Amazon Comprehend
- D) Busca, resolvido com Amazon Kendra

### 5. Qual serviço implementa revisão humana de previsões de ML quando o confidence score é baixo?
- A) Amazon Mechanical Turk
- B) Amazon Augmented AI (A2I)
- C) SageMaker Clarify
- D) Amazon Comprehend

### 6. Uma empresa quer construir uma URA telefônica com fluxo transacional (consultar saldo, informando tipo de conta). Qual serviço é o mais adequado?
- A) Amazon Lex integrado ao Amazon Connect
- B) Amazon Polly com SSML
- C) Amazon Bedrock com um FM generativo
- D) Amazon Kendra

### 7. Qual é a diferença entre Amazon Rekognition e Amazon Textract na detecção de texto?
- A) Rekognition extrai formulários e tabelas; Textract detecta texto em cenas
- B) Rekognition detecta texto curto em imagens/cenas; Textract extrai texto estruturado de documentos (formulários, tabelas)
- C) Ambos fazem exatamente o mesmo, mudando apenas o preço
- D) Rekognition só processa vídeo; Textract só processa imagem

### 8. Um hospital precisa rotular imagens médicas confidenciais para treinar um modelo. Qual força de trabalho é apropriada?
- A) Amazon Mechanical Turk (public workforce)
- B) Private workforce no SageMaker Ground Truth
- C) Vendor workforce sem acordo de confidencialidade
- D) Qualquer uma; os dados são anonimizados automaticamente

### 9. No AWS DeepRacer, o que determina o comportamento aprendido pelo carro?
- A) O algoritmo PPO escolhido
- B) A função de recompensa escrita pelo usuário
- C) A resolução da câmera frontal
- D) O número de waypoints da pista

### 10. Qual serviço analisa o sentimento em relação a entidades específicas dentro de um mesmo texto?
- A) Amazon Comprehend com targeted sentiment
- B) Amazon Kendra com relevance tuning
- C) Amazon Translate com custom terminology
- D) Amazon Personalize com filters

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — **Textract** extrai **formulários (FORMS)** e **tabelas (TABLES)** de documentos. A palavra "formulário"/"documento" na questão praticamente sempre aponta para Textract, não para Rekognition.

2. **B** — **Transcribe** (áudio → texto), **Translate** (traduz o texto) e **Polly** (texto → áudio no novo idioma). A ordem importa: inverter Transcribe e Polly é o distrator clássico.

3. **B** — **Personalize** entrega recomendações personalizadas em tempo real via **Campaign**, usando a mesma tecnologia da Amazon.com. Forecast prevê séries temporais e Kendra faz busca — nenhum dos dois recomenda itens.

4. **B** — Prever valores futuros a partir de histórico **com dimensão temporal e sazonalidade** é **previsão de séries temporais**. O serviço histórico é o **Amazon Forecast**, hoje em descontinuação, com a AWS recomendando as capacidades de forecasting do **SageMaker Canvas**.

5. **B** — **Amazon A2I** implementa **human-in-the-loop**, acionando revisão quando o **confidence score** cai abaixo de um limiar, quando o impacto é alto ou por amostragem aleatória. O MTurk pode ser a *workforce* usada pelo A2I, mas não é o serviço que orquestra o fluxo.

6. **A** — **Lex** é feito para diálogos **estruturados e transacionais** (intents, slots, fulfillment via Lambda) e integra nativamente com o **Amazon Connect** para telefonia. Um FM generativo seria menos determinístico e mais difícil de auditar nesse fluxo.

7. **B** — **Rekognition** detecta **texto curto em cenas** (placas, legendas em fotos). **Textract** extrai **texto estruturado de documentos**, preservando formulários e tabelas.

8. **B** — Dados médicos confidenciais **jamais** devem ir para o **MTurk (public workforce)**. A opção correta é a **private workforce** — a própria equipe do hospital — no **SageMaker Ground Truth**.

9. **B** — A **função de recompensa** define o objetivo, e o comportamento emerge do treino. Recompensar a linha central produz um carro cauteloso; recompensar velocidade produz um carro rápido e instável. O PPO é apenas o algoritmo de otimização.

10. **A** — O **targeted sentiment** do **Comprehend** identifica o sentimento em relação a **entidades específicas**, capturando nuances como "o produto é ótimo (positivo), mas a entrega foi péssima (negativo)" dentro de uma única avaliação.

</details>
