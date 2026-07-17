# 19. Customizando uma FM

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Quando prompt engineering não basta, o Bedrock oferece **customização**, que tem duas formas distintas — e a prova cobra a diferença.

**Fine-tuning**: você fornece um dataset **rotulado** de pares prompt→completion (formato JSONL no S3) e o modelo aprende a tarefa, o estilo ou o formato específico. É **supervisionado**. Use quando quiser que o modelo responda sempre em um tom, siga uma taxonomia interna ou domine um formato particular.

**Continued Pre-training** (pré-treinamento continuado): você fornece um grande volume de texto **não rotulado** do seu domínio (documentos, manuais, artigos) e o modelo absorve vocabulário e conhecimento setorial. É **auto-supervisionado** e exige muito mais dados que o fine-tuning. Use para domínios com linguagem própria — jurídico, médico, farmacêutico.

Em ambos os casos, o resultado é uma **cópia privada do modelo na sua conta**. O modelo base do provedor **não é alterado** e seus dados **não vazam** para outros clientes. Para servir esse modelo customizado em produção, você geralmente precisa comprar **Provisioned Throughput** — o que torna a customização significativamente mais cara que o On-Demand.

A **hierarquia de decisão** é o coração desta aula, e aparece em várias questões: comece por **prompt engineering** (mais barato e mais rápido); se falta **conhecimento factual ou atualizado**, use **RAG**; se precisa de **estilo, tom, formato ou domínio persistente**, considere **fine-tuning**; se o domínio tem linguagem inteiramente própria e você tem muito texto, **continued pre-training**; e treinar do zero é praticamente nunca a resposta — custo proibitivo.

Um contraste essencial: **RAG não altera o modelo, adiciona contexto em tempo de execução, e é atualizável instantaneamente** (basta reindexar os documentos). **Fine-tuning altera os pesos e cristaliza o conhecimento** — atualizar exige novo treino. Se a questão fala em "informações que mudam com frequência" ou "documentos internos atualizados diariamente", a resposta é **RAG**, nunca fine-tuning.

Há ainda um risco técnico a conhecer: o **catastrophic forgetting**, quando o fine-tuning excessivo degrada capacidades gerais do modelo em troca da especialização.

## 🎓 Pontos-chave para a prova

- **Fine-tuning** = dados **rotulados** (prompt/completion, JSONL no S3), supervisionado, ajusta estilo/tarefa.
- **Continued pre-training** = dados **não rotulados** em volume, auto-supervisionado, injeta conhecimento de domínio.
- Ambos criam uma **cópia privada**; o modelo base não muda.
- Modelo customizado normalmente exige **Provisioned Throughput** para inferência.
- Ordem de custo/esforço: **Prompt < RAG < Fine-tuning < Continued pre-training < Treinar do zero**.
- **Conhecimento dinâmico → RAG**. **Estilo/formato persistente → fine-tuning**.
- **Catastrophic forgetting**: risco de perder capacidades gerais ao especializar demais.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Fine-tuning | Ajuste supervisionado com dataset rotulado prompt→completion |
| Continued pre-training | Treino adicional auto-supervisionado com texto não rotulado do domínio |
| JSONL | Formato de dataset (um objeto JSON por linha) usado na customização |
| Cópia privada | Modelo customizado isolado na sua conta |
| Hiperparâmetro | Configuração de treino (epochs, learning rate, batch size) |
| Epoch | Uma passagem completa pelo dataset de treino |
| Catastrophic forgetting | Perda de capacidades gerais causada por especialização excessiva |
| Instruction tuning | Fine-tuning com pares instrução→resposta |

## 💡 Exemplo prático / caso de uso

Um escritório de advocacia tem duas dores. (1) O assistente precisa citar **jurisprudência atualizada semanalmente** → **RAG**, porque re-treinar toda semana seria absurdo e o RAG só exige reindexar os documentos. (2) O assistente precisa escrever **sempre no formato de parecer da casa**, com estrutura e tom próprios → **fine-tuning**, com algumas centenas de pareceres antigos como pares prompt→completion. As duas técnicas são **complementares**, não excludentes — a arquitetura final usa ambas.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
