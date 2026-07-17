# 13. Tipos de Prompt

> Seção: Engenharia de Prompt · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

As técnicas de prompting formam um vocabulário fixo e **muito cobrado** na prova. A escala mais básica é pelo número de exemplos fornecidos.

**Zero-shot**: nenhum exemplo, apenas a instrução — "Classifique o sentimento: 'Adorei o produto'". Funciona bem em tarefas comuns que o modelo já domina. **One-shot**: um único exemplo demonstrando o padrão. **Few-shot**: dois ou mais exemplos, ideal quando o formato de saída é específico ou a tarefa é de nicho. A regra prática: quanto mais incomum a tarefa ou mais rígido o formato, mais exemplos ajudam.

**Chain-of-Thought (CoT)**: pedir que o modelo explicite o raciocínio antes de concluir ("pense passo a passo"). Melhora tarefas aritméticas, lógicas e analíticas de várias etapas. Existe a variante **zero-shot CoT**, que é simplesmente acrescentar "vamos pensar passo a passo" sem dar exemplos.

Outras técnicas que aparecem: **Self-consistency** (gerar vários raciocínios e escolher a resposta majoritária), **Tree-of-Thought** (explorar múltiplos ramos de raciocínio em árvore), **Prompt chaining** (quebrar uma tarefa complexa em uma sequência de prompts, onde a saída de um alimenta o próximo), **ReAct** (*Reason + Act* — o modelo alterna raciocínio e uso de ferramentas, base conceitual dos **Bedrock Agents**) e **RAG** (injetar contexto recuperado de uma base de conhecimento).

Do lado adversarial, dois termos precisam ser distinguidos: **prompt injection** é inserir instruções maliciosas nos dados para desviar o comportamento do modelo; **jailbreaking** é contornar as salvaguardas para obter conteúdo proibido (muitas vezes via roleplay ou hipóteses). Ambos são mitigados por **Guardrails**, validação de entrada, delimitação de dados e princípio do menor privilégio nas ferramentas expostas ao modelo.

Por fim, a **hierarquia de decisão** que a prova adora: se o problema é **formato ou clareza** → prompt engineering; se é **falta de conhecimento factual/atualizado** → **RAG**; se é **estilo, tom ou domínio muito específico de forma persistente** → **fine-tuning**; se exige **ações em sistemas externos** → **Agents**.

## 🎓 Pontos-chave para a prova

- **Zero-shot** = 0 exemplos; **one-shot** = 1; **few-shot** = 2 ou mais.
- **Chain-of-Thought** = raciocínio passo a passo; melhora lógica e matemática.
- **Prompt chaining** = dividir a tarefa em prompts encadeados.
- **ReAct** = raciocinar + agir com ferramentas → base dos **Bedrock Agents**.
- **Prompt injection** ≠ **jailbreaking**: injeção usa dados como instrução; jailbreak burla salvaguardas.
- Decisão: formato → **prompt**; conhecimento → **RAG**; estilo/domínio → **fine-tuning**; ação → **Agents**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Zero-shot | Prompt sem exemplos |
| One-shot | Prompt com um exemplo |
| Few-shot | Prompt com dois ou mais exemplos |
| Chain-of-Thought | Raciocínio explícito passo a passo antes da resposta |
| Self-consistency | Amostrar vários raciocínios e votar na resposta mais frequente |
| Tree-of-Thought | Exploração ramificada de múltiplos caminhos de raciocínio |
| Prompt chaining | Encadear prompts, usando a saída de um como entrada do próximo |
| ReAct | Reasoning + Acting; alterna raciocínio e uso de ferramentas |
| Prompt injection | Injetar instruções maliciosas via dados de entrada |
| Jailbreaking | Contornar salvaguardas do modelo para obter conteúdo proibido |

## 💡 Exemplo prático / caso de uso

Um time tenta classificar chamados em 12 categorias internas com **zero-shot** e obtém 68% de acerto — o modelo não conhece a taxonomia da empresa. Passam para **few-shot**, incluindo dois exemplos de cada categoria, e sobem para 89%. Quando o volume cresce e o prompt fica caro demais, migram para **fine-tuning**, movendo os exemplos do prompt para os pesos do modelo — prompt menor, resposta mais rápida, custo por chamada menor. É a progressão natural que a prova espera que você reconheça.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
