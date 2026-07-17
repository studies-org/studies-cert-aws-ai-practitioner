# 20. Avaliando um Modelo FM

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Bedrock Model Evaluation** permite comparar modelos de forma sistemática, em vez de decidir "no olho". Existem **dois tipos de job**: **Automatic evaluation** e **Human evaluation**.

Na **avaliação automática**, você escolhe uma tarefa (geração de texto geral, sumarização, question answering, classificação), usa um **dataset embutido** da AWS ou um **dataset próprio** (JSONL no S3), e o serviço calcula métricas objetivas: **accuracy**, **robustness** e **toxicity**. É rápido e barato, mas limitado ao que se consegue medir automaticamente. O Bedrock também suporta avaliação com **LLM-as-a-judge**, em que outro modelo pontua as respostas.

Na **avaliação humana**, revisores — sua própria equipe (*bring your own work team*) ou uma equipe gerenciada pela AWS — avaliam as respostas segundo critérios subjetivos que você define: relevância, estilo, aderência à marca, utilidade. É mais lento e mais caro, mas é a única forma de medir qualidades que nenhuma métrica automática captura. **Se a questão fala em critérios subjetivos, tom, estilo ou "alinhamento com a marca", a resposta é human evaluation.**

As **métricas clássicas de NLP** também caem: **ROUGE** (usado em **sumarização**, mede sobreposição de n-gramas com um resumo de referência — *recall-oriented*), **BLEU** (usado em **tradução**, mede precisão de n-gramas), **BERTScore** (usa embeddings para comparar semanticamente, não literalmente) e **Perplexity** (quão "surpreso" o modelo fica com o texto; menor é melhor). O par **ROUGE=sumarização / BLEU=tradução** é praticamente garantido em alguma questão.

Além das métricas de qualidade, avalie também as **métricas de negócio**: custo por inferência, latência (p50/p99), taxa de aprovação humana, e o impacto no indicador que motivou o projeto. Um modelo com métrica ligeiramente melhor mas 5× mais caro raramente é a escolha certa.

## 🎓 Pontos-chave para a prova

- Model Evaluation tem **automatic** e **human**; métricas automáticas incluem **accuracy, robustness e toxicity**.
- **Human evaluation** → critérios **subjetivos** (estilo, tom, marca, utilidade).
- **ROUGE → sumarização**; **BLEU → tradução**; **BERTScore → similaridade semântica**; **Perplexity → menor é melhor**.
- Datasets podem ser **built-in da AWS** ou **próprios (JSONL no S3)**.
- **LLM-as-a-judge** é uma opção intermediária entre automático e humano.
- Avalie também **custo, latência e impacto de negócio**, não só qualidade.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Automatic evaluation | Avaliação com métricas calculadas pelo serviço |
| Human evaluation | Avaliação por revisores humanos com critérios definidos |
| ROUGE | Métrica de sumarização baseada em sobreposição de n-gramas |
| BLEU | Métrica de tradução baseada em precisão de n-gramas |
| BERTScore | Métrica de similaridade semântica via embeddings |
| Perplexity | Medida de incerteza do modelo sobre um texto |
| Toxicity | Métrica de conteúdo ofensivo na saída |
| Robustness | Estabilidade da saída frente a variações da entrada |
| LLM-as-a-judge | Uso de um modelo para avaliar respostas de outro |

## 💡 Exemplo prático / caso de uso

Uma empresa avalia três modelos para resumir chamados de suporte. Roda primeiro um **automatic evaluation** com métrica **ROUGE** contra resumos de referência escritos por analistas — isso elimina o modelo claramente pior. Os dois finalistas empatam nas métricas, então roda um **human evaluation** com a equipe de CX julgando clareza e tom. O vencedor tem ROUGE ligeiramente menor, mas os humanos preferem seus resumos — exatamente o caso em que a métrica automática não captura o que importa.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
