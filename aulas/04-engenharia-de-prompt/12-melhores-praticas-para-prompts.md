# 12. Melhores Práticas para Prompts

> Seção: Engenharia de Prompt · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

A primeira regra é **ser específico e direto**. Prompts vagos produzem respostas vagas. "Fale sobre vendas" é ruim; "resuma em 3 bullets as três principais causas da queda de vendas no relatório abaixo, citando os números" é bom. Ambiguidade no pedido vira variabilidade na resposta.

A segunda é **dizer o que fazer, não o que não fazer**. Instruções negativas ("não seja prolixo", "não use jargão") funcionam pior que positivas ("responda em no máximo 100 palavras usando linguagem simples"). Modelos seguem melhor um alvo concreto do que uma proibição abstrata.

A terceira é **usar delimitadores e estrutura**. Separe instrução, contexto e dados com marcadores claros — tags XML, `###`, aspas triplas. Isso reduz confusão do modelo e mitiga prompt injection. A quarta é **fornecer exemplos** (few-shot) sempre que o formato importar: dois ou três exemplos bem escolhidos valem mais que dez parágrafos descrevendo o formato.

A quinta é **dar espaço para o modelo pensar**. Pedir o raciocínio antes da conclusão ("pense passo a passo e só então responda") melhora sensivelmente tarefas de lógica, matemática e análise. Isso é o **Chain-of-Thought**, detalhado na próxima aula.

A sexta é **iterar e avaliar**. Prompt engineering é empírico: teste variações, compare saídas, use o **Prompt Management** e o **Prompt Flows** do Bedrock para versionar e reutilizar prompts em produção — em vez de espalhar strings soltas pelo código.

Por fim, as práticas de **segurança e custo**. Nunca confie cegamente em conteúdo de terceiros dentro do prompt; combine com **Guardrails** para bloquear conteúdo indesejado. E lembre-se de que prompts longos custam mais e consomem janela de contexto — enxugue instruções repetidas, e prefira RAG a colar documentos inteiros no prompt.

## 🎓 Pontos-chave para a prova

- Seja **específico**; instrua **positivamente** (o que fazer, não o que evitar).
- Use **delimitadores** para separar instrução de dados.
- **Few-shot** é a maneira mais eficiente de fixar formato e estilo.
- Peça **raciocínio passo a passo** em tarefas de lógica (Chain-of-Thought).
- **Itere e avalie**; use **Prompt Management/Prompt Flows** do Bedrock para versionar.
- Prompts longos = **mais custo e mais consumo da context window**.
- Prompt engineering é a alternativa de **menor custo** frente a RAG e fine-tuning.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Especificidade | Grau de detalhe e clareza da instrução |
| Instrução positiva | Dizer o que fazer em vez de o que não fazer |
| Delimitador | Marcador que isola blocos do prompt |
| Few-shot | Incluir exemplos no prompt |
| Chain-of-Thought | Solicitar raciocínio passo a passo antes da resposta |
| Prompt Management | Recurso do Bedrock para criar, versionar e testar prompts |
| Prompt Flows | Recurso do Bedrock para orquestrar prompts e serviços em fluxos |
| Iteração | Ciclo de testar, medir e refinar o prompt |

## 💡 Exemplo prático / caso de uso

**Antes:** "Analise esse feedback e não seja genérico."

**Depois:**
```
Você é um analista de CX. Leia o feedback delimitado e produza:
1. Sentimento (POSITIVO | NEUTRO | NEGATIVO)
2. Tema principal em até 5 palavras
3. Uma ação recomendada

Responda em JSON. Máximo de 80 palavras.

<feedback>
{texto_do_cliente}
</feedback>
```

O segundo prompt é específico, positivo, delimitado e define o formato de saída — as quatro práticas em um só bloco.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
