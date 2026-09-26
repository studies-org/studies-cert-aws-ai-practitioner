# 48. Responsabilidades com AI

> Seção: Práticas e Responsabilidades de IA · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**IA Responsável** é o conjunto de práticas para desenvolver e operar sistemas de IA de forma **justa, transparente, segura e confiável**. Não é discurso: no Domínio 4 (14% do exame) a AWS cobra os **oito pilares** que ela mesma define.

Os **oito pilares da IA Responsável da AWS** são: **Fairness** (equidade — o sistema trata grupos diferentes de forma justa); **Explainability** (explicabilidade — é possível entender por que o modelo decidiu aquilo); **Robustness** (robustez — o sistema se mantém confiável sob variação e estresse); **Privacy & Security** (dados protegidos e usados adequadamente); **Governance** (políticas, papéis e processos definidos); **Transparency** (usuários sabem que estão interagindo com IA e conhecem suas limitações); **Veracity & Robustness** (as saídas são corretas e verificáveis); **Safety** (o sistema não causa dano); e **Controllability** (é possível monitorar e intervir no comportamento).

O problema central é o **viés (bias)**. Suas fontes: **viés nos dados** (o histórico reflete desigualdades do mundo real — se a empresa só contratou homens para engenharia, o modelo aprende isso), **viés de amostragem** (o dataset não representa a população), **viés algorítmico** e **viés de confirmação** na interpretação dos resultados. As **métricas de equidade** incluem *demographic parity*, *equal opportunity* e *disparate impact*. O ponto contraintuitivo que a prova adora: **remover o atributo sensível (raça, gênero) NÃO elimina o viés**, porque outras variáveis atuam como **proxy** (CEP correlaciona com raça, por exemplo).

A **explicabilidade** distingue **modelos interpretáveis** (regressão linear, árvores de decisão — a lógica é legível) de **modelos black-box** (deep learning — alto desempenho, baixa transparência). Há um **trade-off real** entre precisão e interpretabilidade. Ferramentas como **SHAP** e **LIME**, disponíveis via **SageMaker Clarify**, explicam previsões de modelos complexos atribuindo importância a cada feature.

As ferramentas AWS que materializam cada pilar: **SageMaker Clarify** (viés + explicabilidade), **Model Monitor** (drift), **Bedrock Guardrails** (segurança de conteúdo), **Amazon A2I** (supervisão humana), **AI Service Cards** (transparência sobre limitações e usos apropriados), **Model Cards** (documentação de governança) e **Model Evaluation** (avaliação de qualidade e toxicidade).

## 🎓 Pontos-chave para a prova

- Pilares AWS: **fairness, explainability, robustness, privacy & security, governance, transparency, veracity, safety, controllability**.
- **Viés vem principalmente dos dados** — o modelo reproduz desigualdades históricas.
- **Remover o atributo sensível não elimina o viés** (variáveis proxy).
- **Trade-off** entre precisão (black-box) e interpretabilidade (modelos simples).
- **SHAP/LIME** via **SageMaker Clarify** explicam modelos complexos.
- **AI Service Cards** documentam limitações e usos apropriados dos serviços AWS.
- Decisões de **alto risco** exigem **human-in-the-loop (A2I)**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Fairness | Tratamento equitativo entre grupos |
| Explainability | Capacidade de explicar por que o modelo decidiu |
| Interpretabilidade | Modelo cuja lógica é diretamente legível |
| Black-box | Modelo de alto desempenho e baixa transparência |
| SHAP / LIME | Técnicas de atribuição de importância a features |
| Variável proxy | Feature que substitui indiretamente um atributo sensível |
| Disparate impact | Efeito desproporcional sobre um grupo protegido |
| AI Service Card | Documento AWS sobre uso, limitações e equidade de um serviço |
| Human-in-the-loop | Supervisão humana em decisões consequentes |

## 💡 Exemplo prático / caso de uso

Um banco treina um modelo de crédito com 10 anos de histórico e remove `raça` e `gênero` das features, acreditando ter resolvido a questão. O **SageMaker Clarify** revela **disparate impact**: a taxa de aprovação para moradores de certos CEPs é drasticamente menor. O **CEP virou proxy de raça**. O modelo aprendeu a discriminar sem nunca ver o atributo — porque o **viés estava nos dados**, não na coluna. As correções envolvem rebalancear os dados, aplicar restrições de fairness, monitorar métricas por grupo e manter **revisão humana (A2I)** nas negativas.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
