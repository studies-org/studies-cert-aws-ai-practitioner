# 50. Serviços IA para Responsabilidade

> Seção: Práticas e Responsabilidades de IA · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Esta aula conecta cada **princípio** de IA responsável ao **serviço AWS** que o implementa. A prova adora esse mapeamento — dado um problema, qual ferramenta usar.

**Viés e explicabilidade → SageMaker Clarify.** Detecta viés **antes** do treino (nos dados: um grupo está sub-representado?), **depois** do treino (nas previsões: a taxa de acerto difere por grupo?) e explica previsões individuais com **SHAP**. É a resposta para "detectar viés" e "explicar a decisão do modelo".

**Drift em produção → SageMaker Model Monitor.** Modelos degradam porque o mundo muda. Monitora **data drift** (a distribuição das entradas mudou), **model quality drift** (a acurácia caiu), **bias drift** (o viés surgiu com o tempo) e **feature attribution drift**. Integra com CloudWatch para alertas.

**Segurança de conteúdo em GenAI → Bedrock Guardrails.** Filtra conteúdo nocivo, bloqueia tópicos, protege PII, verifica **grounding** contra alucinação e barra **prompt attacks**.

**Supervisão humana → Amazon A2I.** Revisão humana em decisões de baixa confiança ou alto impacto.

**Transparência → AI Service Cards.** Documentos publicados pela AWS descrevendo casos de uso pretendidos, **limitações**, escolhas de design responsável e considerações de equidade de cada serviço de IA. **Model Cards** é o equivalente para os **seus** modelos, documentando propósito, dados, métricas e riscos.

**Qualidade → Bedrock Model Evaluation.** Métricas automáticas (incluindo **toxicity**) e avaliação humana.

**Privacidade → Amazon Macie** (descobre PII no S3), **Comprehend PII detection** (detecta e reda PII em texto), **KMS** (criptografia) e **PrivateLink/VPC** (isolamento de rede).

**Governança → SageMaker Model Registry** (versionamento e aprovação de modelos), **AWS Config**, **CloudTrail** e **Audit Manager**.

O padrão a memorizar: **Clarify = viés/explicabilidade** · **Model Monitor = drift** · **Guardrails = conteúdo GenAI** · **A2I = humano** · **Service/Model Cards = transparência** · **Macie = PII no S3**.

## 🎓 Pontos-chave para a prova

- **SageMaker Clarify** → viés (pré e pós-treino) + explicabilidade (**SHAP**).
- **SageMaker Model Monitor** → **data drift**, model quality drift, bias drift.
- **Bedrock Guardrails** → segurança de conteúdo, PII, grounding, prompt attacks.
- **Amazon A2I** → human-in-the-loop.
- **AI Service Cards** → transparência dos serviços AWS; **Model Cards** → dos seus modelos.
- **Amazon Macie** → descoberta de PII no S3; **Comprehend** → redação de PII em texto.
- **Model Registry** → versionamento e aprovação; **CloudTrail** → auditoria.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| SageMaker Clarify | Detecção de viés e explicabilidade |
| Model Monitor | Monitoramento de drift em produção |
| Data drift | Mudança na distribuição dos dados de entrada |
| Model quality drift | Queda da qualidade das previsões ao longo do tempo |
| AI Service Card | Documento AWS com limitações e usos apropriados de um serviço |
| Model Card | Documentação de governança de um modelo próprio |
| Model Registry | Catálogo versionado de modelos com fluxo de aprovação |
| Amazon Macie | Descoberta e classificação de dados sensíveis no S3 |

## 💡 Exemplo prático / caso de uso

Uma empresa monta a governança de IA de ponta a ponta: **Clarify** roda a cada treino e barra o deploy se o disparate impact ultrapassar o limite; **Model Cards** documenta propósito, dados e métricas de cada modelo; **Model Registry** exige aprovação formal antes da promoção; **Model Monitor** alerta via CloudWatch quando há **drift**; **A2I** revisa decisões de alto impacto; **Guardrails** protege o assistente generativo; **Macie** varre o S3 em busca de PII exposto; e **CloudTrail** registra tudo. Cada peça responde a um pilar — e é assim que "IA responsável" deixa de ser slide e vira arquitetura.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
