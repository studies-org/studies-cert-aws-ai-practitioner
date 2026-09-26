# 33. O Amazon SageMaker

> Seção: SageMaker · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon SageMaker** é a plataforma completa de Machine Learning da AWS, cobrindo **todo o ciclo de vida**: preparar dados, construir, treinar, ajustar, implantar e monitorar modelos. Se o Bedrock é para **consumir e adaptar** Foundation Models prontos, o SageMaker é para **construir, treinar e operar** modelos — inclusive os seus próprios, do zero.

O **SageMaker Studio** é a IDE web unificada. Dentro do ecossistema, os componentes mais cobrados são: **SageMaker Canvas** — construção de modelos **sem código**, por interface visual, voltado a analistas de negócio; **SageMaker Autopilot / AutoML** — automatiza seleção de algoritmo, engenharia de features e tuning; **SageMaker JumpStart** — hub com modelos pré-treinados e Foundation Models prontos para deploy com poucos cliques; **SageMaker Data Wrangler** — preparação e transformação visual de dados; **SageMaker Feature Store** — repositório central de features reutilizáveis entre times e modelos; **SageMaker Ground Truth** — rotulagem de dados, com apoio humano e rotulagem automatizada; **SageMaker Clarify** — detecção de **viés** e **explicabilidade** (SHAP); **SageMaker Model Monitor** — monitora **data drift** e **model drift** em produção; **SageMaker Pipelines** — orquestração de MLOps; e **SageMaker Model Cards** — documentação de governança do modelo.

As **opções de inferência** do SageMaker também caem: **Real-time endpoint** (baixa latência, cobra por hora enquanto existir), **Serverless inference** (escala a zero, ideal para tráfego intermitente), **Asynchronous inference** (payloads grandes, fila) e **Batch transform** (lote sobre dados no S3).

A comparação **Bedrock × SageMaker** é praticamente garantida na prova. **Bedrock**: serverless, FMs de terceiros via API, sem gestão de infraestrutura, foco em GenAI, menor esforço. **SageMaker**: controle total, treina modelos próprios com qualquer algoritmo/framework, você escolhe instâncias, maior esforço e maior flexibilidade. Se a questão pede "sem gerenciar infraestrutura, usando FMs prontos" → **Bedrock**. Se pede "treinar um modelo customizado com nossos dados e nosso algoritmo" → **SageMaker**.

Cuidado prático: **endpoints do SageMaker cobram por hora enquanto existirem**, mesmo sem tráfego. É a fonte de fatura surpresa mais comum em laboratórios de ML.

## 🎓 Pontos-chave para a prova

- SageMaker cobre o **ciclo completo de ML**; Bedrock foca em **consumir/adaptar FMs**.
- **Canvas** = sem código; **Autopilot** = AutoML; **JumpStart** = modelos pré-treinados prontos.
- **Ground Truth** = rotulagem; **Data Wrangler** = preparação; **Feature Store** = features reutilizáveis.
- **Clarify** = **viés + explicabilidade**; **Model Monitor** = **drift** em produção.
- Inferência: **real-time, serverless, asynchronous e batch transform**.
- **Endpoints cobram por hora mesmo ociosos** — delete após o laboratório.
- "Treinar modelo próprio" → SageMaker. "Usar FM sem infra" → Bedrock.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| SageMaker Studio | IDE web unificada para ML |
| SageMaker Canvas | Construção de modelos ML sem código |
| Autopilot (AutoML) | Automação de seleção de algoritmo, features e tuning |
| JumpStart | Hub de modelos pré-treinados e FMs |
| Ground Truth | Serviço de rotulagem de dados |
| Data Wrangler | Preparação e transformação visual de dados |
| Feature Store | Repositório centralizado de features |
| Clarify | Detecção de viés e explicabilidade de modelos |
| Model Monitor | Monitoramento de drift de dados e de modelo |
| Pipelines | Orquestração de fluxos de MLOps |
| Model Cards | Documentação de governança de um modelo |
| Data drift | Mudança na distribuição dos dados de entrada ao longo do tempo |

## 💡 Exemplo prático / caso de uso

Uma fintech precisa de um modelo de risco de crédito treinado nos **seus próprios dados históricos**, com algoritmo específico e exigência regulatória de **explicar cada decisão**. Bedrock não serve — não é um problema de Foundation Model. A escolha é **SageMaker**: **Data Wrangler** prepara os dados, **Autopilot** testa algoritmos, **Clarify** verifica viés contra grupos protegidos e gera explicações **SHAP** para o regulador, **Model Monitor** detecta **drift** quando o perfil dos solicitantes muda, e **Model Cards** documenta tudo para auditoria.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
