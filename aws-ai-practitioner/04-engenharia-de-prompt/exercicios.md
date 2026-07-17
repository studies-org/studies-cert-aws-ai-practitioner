# Exercícios — 04. Engenharia de Prompt

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_, 6-_, 7-_, 8-_

## Questões

### 1. Uma equipe precisa que um modelo extraia campos de contratos e devolva sempre o mesmo JSON. Qual configuração é mais adequada?
- A) Temperature 0,9 para aumentar a criatividade
- B) Temperature próxima de 0 para maximizar o determinismo
- C) Top-K = 100 para ampliar as opções
- D) Remover o max tokens para não truncar

### 2. O que caracteriza um prompt few-shot?
- A) Um prompt sem nenhum exemplo, apenas a instrução
- B) Um prompt com exatamente um exemplo
- C) Um prompt com dois ou mais exemplos demonstrando o padrão desejado
- D) Um prompt que pede raciocínio passo a passo

### 3. Um chatbot inventa detalhes sobre a política interna de reembolso da empresa. Qual é a solução mais adequada?
- A) Reduzir a temperature para 0
- B) Implementar RAG com uma Knowledge Base contendo os documentos oficiais
- C) Aumentar o max tokens
- D) Trocar de zero-shot para one-shot

### 4. Qual técnica é a base conceitual dos Amazon Bedrock Agents?
- A) Chain-of-Thought puro
- B) ReAct (Reasoning + Acting)
- C) Self-consistency
- D) Zero-shot classification

### 5. Qual é a diferença entre prompt injection e jailbreaking?
- A) São exatamente o mesmo ataque com nomes diferentes
- B) Injection insere instruções maliciosas via dados de entrada; jailbreaking busca contornar as salvaguardas do modelo
- C) Injection só ocorre em imagens; jailbreaking só em texto
- D) Jailbreaking é uma técnica legítima de otimização de prompt

### 6. Quais são componentes de um prompt bem estruturado? (Escolha a melhor opção)
- A) Instrução, contexto, dados de entrada, exemplos e indicador de saída
- B) Encoder, decoder, atenção e embeddings
- C) Agente, ambiente, ação e recompensa
- D) Treino, validação e teste

### 7. Uma tarefa envolve raciocínio matemático em várias etapas e o modelo erra com frequência. Qual técnica ajuda mais?
- A) Aumentar a temperature para 1,0
- B) Chain-of-Thought, pedindo raciocínio passo a passo
- C) Reduzir o max tokens para forçar objetividade
- D) Usar zero-shot sem contexto

### 8. Qual afirmação sobre prompt engineering versus fine-tuning é correta?
- A) Prompt engineering altera os pesos do modelo; fine-tuning não
- B) Prompt engineering não altera os pesos e é a opção de menor custo e esforço
- C) Fine-tuning é sempre mais barato que prompt engineering
- D) Ambos exigem retreinar o modelo do zero

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — **Temperature próxima de 0** torna a geração determinística, o que é essencial quando a saída alimenta um parser. Temperature alta introduz variação e quebra o contrato de formato.

2. **C** — **Few-shot = dois ou mais exemplos**. Zero-shot não tem exemplos, one-shot tem exatamente um, e raciocínio passo a passo é Chain-of-Thought.

3. **B** — Alucinação por **falta de conhecimento factual** se resolve com **RAG**, injetando os documentos reais no contexto. Temperature 0 apenas torna a resposta errada mais consistente — não a torna correta.

4. **B** — **ReAct** alterna raciocínio e chamada de ferramentas, exatamente o loop que os **Bedrock Agents** implementam para consultar APIs e executar ações.

5. **B** — **Prompt injection** explora a fronteira entre instrução e dados, fazendo o modelo obedecer a texto vindo do usuário. **Jailbreaking** tenta burlar as salvaguardas (roleplay, hipóteses) para extrair conteúdo proibido. Ambos são mitigados por Guardrails e delimitação de dados.

6. **A** — Os cinco componentes são **instrução, contexto, dados de entrada, exemplos e indicador de saída**. B descreve a arquitetura Transformer, C descreve RL e D descreve a divisão de dados.

7. **B** — **Chain-of-Thought** melhora significativamente tarefas de múltiplas etapas ao permitir que o modelo externalize o raciocínio intermediário antes de concluir.

8. **B** — **Prompt engineering não toca nos pesos** e é a alternativa mais rápida e barata. Fine-tuning ajusta os pesos, exige dataset e infraestrutura, e custa muito mais.

</details>
