# 🎓 Plano de Estudos — AWS Certified AI Practitioner (AIF-C01)

Material completo de estudo para a certificação **AWS Certified AI Practitioner**, organizado aula por aula, com exercícios no estilo do exame e um painel de acompanhamento de desempenho.

## 🎯 Objetivo

Preparar para o exame **AIF-C01** através de um ciclo estruturado: **assistir → ler → exercitar → corrigir → revisar**. Cada aula do curso tem um arquivo `.md` que condensa o que realmente cai na prova, e cada seção termina com exercícios corrigidos automaticamente pelo Claude Code.

### Sobre o exame

| Item | Valor |
|------|-------|
| Código | AIF-C01 |
| Nível | Foundational |
| Questões | 65 (50 pontuadas + 15 experimentais) |
| Duração | 90 minutos |
| Nota de corte | **700** (escala de 100 a 1000) |
| Custo | US$ 100 |
| Validade | 3 anos |

### Domínios e pesos

| Domínio | Peso | Seções deste repositório |
|---------|-----:|--------------------------|
| 1 — Fundamentos de IA e ML | 20% | 03, 07 |
| 2 — Fundamentos de IA Generativa | 24% | 04, 05 |
| 3 — Aplicações de Foundation Models | **28%** | 05, 06, 08 |
| 4 — Diretrizes de IA Responsável | 14% | 09 |
| 5 — Segurança, Conformidade e Governança | 14% | 09, 10 |

> Os domínios 2 e 3 somam **52%** da prova. As seções 04, 05, 06 e 08 merecem a maior parte do seu tempo.

## 📁 Estrutura

```
aws-ai-practitioner/
├── 01-iniciando/                          # Aulas 1–2   · Visão geral do exame
├── 02-a-aws/                              # Aulas 3–5   · Nuvem, Free Tier, conta
├── 03-ai-inteligencia-artificial/         # Aulas 6–9   · IA, ML supervisionado/não sup./reforço
├── 04-engenharia-de-prompt/               # Aulas 10–13 · Prompts, parâmetros, técnicas
├── 05-amazon-bedrock/                     # Aulas 14–25 · FMs, RAG, Agents, Guardrails ⭐
├── 06-amazon-q/                           # Aulas 26–32 · Assistente corporativo
├── 07-sagemaker/                          # Aula 33     · Plataforma de ML
├── 08-servicos-de-ia-na-aws/              # Aulas 34–47 · Catálogo de serviços de IA
├── 09-praticas-e-responsabilidades-de-ia/ # Aulas 48–52 · IA responsável e governança
├── 10-seguranca/                          # Aulas 53–54 · IAM e Identity Center
├── 11-o-exame/                            # Aula 55     · Estratégia de prova
├── 12-finalizando/                        # Aula 56     · Próximos passos
├── 13-bonus/                              # Aula 57     · Folha de cola final
├── README.md                              # Este arquivo
└── SCORE.md                               # 📊 Painel de desempenho
```

Cada pasta de seção contém:
- **`NN-titulo.md`** — um arquivo por aula
- **`exercicios.md`** — questões de múltipla escolha no estilo AIF-C01, com gabarito comentado

### Anatomia de uma aula

Todo arquivo de aula segue o mesmo template:

- **📌 Resumo** — a explicação didática do conceito
- **🎓 Pontos-chave para a prova** — o que memorizar
- **🔑 Termos importantes** — glossário do tópico
- **💡 Exemplo prático** — o conceito aplicado a um caso real
- **✅ Checklist de domínio** — autoavaliação

## 📖 Como estudar

1. **Assista** à aula do curso.
2. **Leia** o `.md` correspondente aqui — ele condensa o que cai na prova.
3. **Marque** o checklist de domínio ao final. Se não conseguir dar um caso de uso real, releia.
4. Ao terminar a seção, **resolva os exercícios** (veja abaixo).
5. **Peça a correção** e deixe o `SCORE.md` dizer o que revisar.

Ou peça ajuda ao tutor:

```
estudar bedrock
```

O Claude resume a seção e faz uma pergunta de fixação.

## 🧪 Como fazer os exercícios

1. Abra o `exercicios.md` da seção.
2. Preencha o bloco **"Minhas respostas"** no topo:
   ```markdown
   ## Minhas respostas
   > Responda aqui: 1-B, 2-C, 3-A, 4-D, 5-B
   ```
3. **Não olhe o gabarito antes.** Ele está no bloco `<details>` no final do arquivo — colapsado justamente para não estragar o teste.

## ✅ Como pedir a correção

```
corrigir seção 5
```

O Claude Code vai:
- ler suas respostas e compará-las com o gabarito;
- calcular acertos e porcentagem;
- explicar **por que** cada erro está errado;
- **atualizar o `SCORE.md`** com placar, status e histórico.

O status segue a legenda: 🔴 <60% · 🟡 60–79% · 🟢 ≥80%.

## 🤖 Como usar a Skill

A Skill `estudo-aws-aip` (em `.claude/skills/estudo-aws-aip/`) transforma o Claude Code num tutor da certificação. Ela é ativada automaticamente pelos comandos abaixo, ou explicitamente com `/estudo-aws-aip`.

| Comando | O que faz |
|---------|-----------|
| `estudar <tópico/seção>` | Resume o material e faz uma pergunta de fixação |
| `corrigir seção <N>` | Corrige os exercícios e atualiza o `SCORE.md` |
| `meu progresso` | Analisa o `SCORE.md` e sugere o que revisar |
| `simulado` | Monta um simulado de 20 questões misturando seções |

> A Skill fica em `.claude/` na **raiz do repositório** (e não dentro de `aws-ai-practitioner/`), porque é lá que o Claude Code descobre skills de projeto.

## 💰 Avisos de custo

Os laboratórios usam serviços **pagos**. Antes de começar:

- **Crie um orçamento no AWS Budgets** com alerta por e-mail (ex.: US$ 10).
- **O Amazon Bedrock não está no Free Tier** — cobra por token desde a primeira chamada.
- **Sempre remova os recursos** ao final de cada laboratório.

Os recursos que **cobram mesmo ociosos** — e que mais geram fatura surpresa:

| Recurso | Cobrança |
|---------|----------|
| Amazon Q Business | Assinatura por usuário/mês |
| Amazon Kendra | Por hora de índice provisionado |
| OpenSearch Serverless (Knowledge Bases) | Por OCU |
| Endpoints real-time do SageMaker | Por hora, enquanto existirem |

## 🔗 Referências oficiais

- [Página do exame AIF-C01](https://aws.amazon.com/certification/certified-ai-practitioner/)
- [Exam Guide (PDF)](https://d1.awsstatic.com/onedam/marketing-channels/website/aws/en_US/certification/approved/pdfs/docs-ai-practitioner/AWS-Certified-AI-Practitioner_Exam-Guide.pdf)
- [AWS Skill Builder](https://explore.skillbuilder.aws/)
- [AI Service Cards](https://aws.amazon.com/machine-learning/responsible-ai/resources/)

---

**Bons estudos!** Comece por `01-iniciando/01-boas-vindas.md`.
