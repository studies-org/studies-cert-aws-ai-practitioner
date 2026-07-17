# 57. Bônus

> Seção: Bônus · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Esta aula é a **folha de cola final**: os mapeamentos que decidem a maior parte das questões, reunidos em um lugar só.

**Escolha da técnica.** Formato/clareza da resposta → **prompt engineering**. Falta de conhecimento factual/atualizado → **RAG**. Estilo, tom ou tarefa persistente → **fine-tuning**. Domínio com linguagem inteiramente própria e muito texto → **continued pre-training**. Executar ações em sistemas → **Agents**. Bloquear conteúdo → **Guardrails**. Ordem de custo/esforço: **prompt < RAG < fine-tuning < continued pre-training < treinar do zero**.

**Escolha do serviço.** Construir com FMs sem infra → **Bedrock**. Treinar modelo próprio → **SageMaker**. Assistente corporativo pronto → **Amazon Q Business**. Assistente de código → **Q Developer**. Análise de texto (sentimento, entidades, PII) → **Comprehend**. Tradução → **Translate**. Fala→texto → **Transcribe**. Texto→fala → **Polly**. Imagens e vídeo → **Rekognition**. Documentos, formulários e tabelas → **Textract**. Busca empresarial → **Kendra**. Recomendação → **Personalize**. Série temporal → **Forecast/SageMaker Canvas**. Chatbot transacional/URA → **Lex**. Revisão humana → **A2I**. Rotulagem → **Ground Truth/MTurk**. RL → **DeepRacer**.

**Governança e responsabilidade.** Viés e explicabilidade → **Clarify**. Drift → **Model Monitor**. Conteúdo GenAI → **Guardrails**. Transparência → **AI Service Cards / Model Cards**. PII no S3 → **Macie**. Relatórios de conformidade → **Artifact**. Auditoria de API → **CloudTrail**. Versionamento e aprovação de modelos → **Model Registry**.

**Métricas.** Classificação → accuracy, **precision** (evita falso positivo), **recall** (evita falso negativo), F1, AUC-ROC. Regressão → MSE, **RMSE**, MAE, R². Sumarização → **ROUGE**. Tradução → **BLEU**. Semântica → **BERTScore**. Modelo de linguagem → **perplexity** (menor é melhor).

**Custo.** Bedrock: **On-Demand** (variável) · **Provisioned** (constante, exigido para modelos customizados) · **Batch** (~50% off, assíncrono). Reduzir custo: modelo menor, prompt curto, `max tokens` menor, **prompt caching**, **Intelligent Prompt Routing**. **Cobram ociosos**: assinatura do **Q Business**, índice do **Kendra**, **OCUs do OpenSearch**, **endpoints do SageMaker**.

**Os pares que mais confundem:** Transcribe (fala→texto) × Polly (texto→fala) · Textract (documentos) × Rekognition (imagens) · RAG (conhecimento dinâmico) × fine-tuning (estilo persistente) · Clarify (viés) × Model Monitor (drift) · Bedrock (construir) × Q (pronto) · Personalize (recomendar) × Forecast (prever no tempo) · Kendra (buscar) × Comprehend (analisar).

## 🎓 Pontos-chave para a prova

- **Conhecimento que muda → RAG. Estilo persistente → fine-tuning.** Nunca inverta.
- **Temperature não corrige alucinação** — RAG corrige.
- **Menor esforço operacional** → sempre o serviço gerenciado.
- **Remover o atributo sensível não elimina o viés** (proxies).
- **Deny explícito sempre vence** no IAM.
- **Bedrock não é Free Tier**; **ROUGE = sumarização, BLEU = tradução**.
- **Nunca deixe questão em branco** — não há penalidade por erro.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Hierarquia de customização | prompt < RAG < fine-tuning < continued pre-training < do zero |
| Serviço gerenciado | Opção de menor esforço operacional |
| Par confundível | Serviços com funções opostas ou vizinhas frequentemente trocados |
| Palavra-chave de desempate | MOST/LEAST/BEST — define entre alternativas todas corretas |
| Recurso ocioso cobrado | Capacidade provisionada que cobra sem uso |

## 💡 Exemplo prático / caso de uso

Um método de 30 segundos por questão: (1) leia a **última linha** — o que exatamente se pede? (2) Localize a **palavra-chave de desempate** (MOST cost-effective? LEAST operational overhead?). (3) Elimine as duas alternativas absurdas. (4) Entre as duas restantes, aplique o mapeamento acima. (5) Marque e siga. Se travou por mais de 90 segundos, **chute, marque para revisão e vá em frente** — tempo gasto numa questão difícil é tempo roubado de três fáceis lá na frente.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
