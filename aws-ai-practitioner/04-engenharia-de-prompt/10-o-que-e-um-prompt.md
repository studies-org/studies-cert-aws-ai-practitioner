# 10. O Que é um Prompt

> Seção: Engenharia de Prompt · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Um **prompt** é a entrada em linguagem natural que você fornece a um modelo de IA Generativa para obter a saída desejada. **Prompt engineering** é a prática de projetar essa entrada para maximizar a qualidade, a relevância e a consistência da resposta — sem alterar os pesos do modelo. É a forma **mais barata e mais rápida** de melhorar resultados, e por isso é sempre a primeira alternativa a considerar antes de partir para RAG ou fine-tuning.

Para entender o que acontece por baixo, dois conceitos são obrigatórios. **Token** é a unidade em que o modelo processa texto — aproximadamente uma palavra curta ou um pedaço de palavra (regra prática em inglês: ~4 caracteres ≈ 1 token). **Você paga por token de entrada e de saída no Bedrock**, então o tamanho do prompt tem impacto direto no custo. A **janela de contexto (context window)** é o número máximo de tokens que o modelo consegue considerar de uma vez, somando entrada e saída — estourá-la causa truncamento ou erro.

Os **parâmetros de inferência** controlam o comportamento da geração e caem muito na prova. **Temperature** regula a aleatoriedade: valores baixos (0–0,3) produzem saídas determinísticas e focadas, ideais para extração de dados e respostas factuais; valores altos (0,8–1,0) aumentam a criatividade e a variação, úteis para brainstorming e escrita criativa. **Top-P (nucleus sampling)** limita a escolha ao menor conjunto de tokens cuja probabilidade acumulada atinge P. **Top-K** limita às K palavras mais prováveis. **Max tokens** (ou *maximum length*) define o tamanho máximo da resposta — e é o principal controle de custo da saída. **Stop sequences** encerram a geração ao encontrar um texto específico.

Um erro conceitual comum: **ajustar temperature não torna o modelo mais preciso nem elimina alucinação**. Temperature muda a distribuição de amostragem, não o conhecimento do modelo. Se a questão pedir "reduzir alucinação com informação factual da empresa", a resposta é **RAG**, não temperature.

## 🎓 Pontos-chave para a prova

- **Prompt engineering não altera os pesos** do modelo — é a opção de menor custo e menor esforço.
- **Token** é a unidade de cobrança e de processamento; **context window** é o limite de entrada + saída.
- **Temperature baixa** → determinístico e factual. **Temperature alta** → criativo e variado.
- **Top-P** = corte por probabilidade acumulada; **Top-K** = corte pelas K opções mais prováveis.
- **Max tokens** controla o tamanho (e o custo) da resposta; **stop sequences** encerram a geração.
- Temperature **não** corrige falta de conhecimento — para isso existe **RAG** ou **fine-tuning**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Prompt | Entrada em linguagem natural fornecida ao modelo |
| Prompt engineering | Prática de projetar prompts para melhorar a saída |
| Token | Unidade de texto processada e cobrada pelo modelo |
| Context window | Máximo de tokens que o modelo considera (entrada + saída) |
| Temperature | Controla a aleatoriedade da geração (0 = determinístico) |
| Top-P | Nucleus sampling — corte por probabilidade cumulativa |
| Top-K | Restringe a amostragem aos K tokens mais prováveis |
| Max tokens | Limite de tamanho da resposta gerada |
| Stop sequence | Texto que interrompe a geração ao ser produzido |
| Inferência | Ato de gerar uma resposta a partir do prompt |

## 💡 Exemplo prático / caso de uso

Um time cria um extrator que lê notas fiscais e devolve JSON estruturado. Como qualquer variação quebra o parser a jusante, configuram **temperature = 0**, **top-P = 1**, **max tokens = 500** e uma **stop sequence** em `}` para cortar texto extra. Já o time de marketing, gerando slogans, usa **temperature = 0,9** para obter dez variações distintas. Mesmo modelo, parâmetros opostos, porque os objetivos são opostos.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
