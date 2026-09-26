# 55. Dicas para Passar na Prova

> Seção: O Exame · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**Os dados do exame:** 65 questões (50 pontuadas + 15 experimentais), 90 minutos, nota de corte **700/1000**, custo de **US$ 100**, disponível em **Pesos Vue** (centro de testes) ou **OnVUE** (online proctored). Candidatos cujo idioma nativo não é o inglês podem solicitar **+30 minutos** de acomodação — peça **antes** de agendar.

**A estratégia de prova.** São ~83 segundos por questão. Faça duas passadas: na primeira, responda o que sabe e **marque para revisão** o que trava; na segunda, volte às marcadas. **Nunca deixe em branco** — não há penalidade por erro. Leia a **última linha primeiro**: ela costuma revelar o que realmente se pede ("qual é a solução **MAIS ECONÔMICA**?" muda tudo). Preste atenção nas palavras em maiúsculas: **MOST cost-effective**, **LEAST operational overhead**, **FASTEST** — elas escolhem entre alternativas que estão todas tecnicamente corretas.

**Os padrões de resposta que se repetem.** "Sem gerenciar infraestrutura" → **serverless/Bedrock**. "Menor esforço operacional" → **serviço gerenciado**, nunca "construir do zero". "Reduzir alucinação com dados da empresa" → **RAG/Knowledge Bases**. "Dados que mudam com frequência" → **RAG**, nunca fine-tuning. "Estilo/tom persistente" → **fine-tuning**. "Executar ações em sistemas" → **Agents**. "Bloquear conteúdo impróprio" → **Guardrails**. "Detectar viés/explicar" → **Clarify**. "Drift em produção" → **Model Monitor**. "Revisão humana" → **A2I**. "Documento/formulário" → **Textract**. "Imagem/cena" → **Rekognition**. "Recomendação" → **Personalize**. "Série temporal" → **Forecast/Canvas**. "Busca empresarial" → **Kendra**.

**Os erros clássicos:** confundir **Transcribe** (fala→texto) com **Polly** (texto→fala); confundir **Textract** (documentos) com **Rekognition** (imagens); escolher **fine-tuning** onde a resposta é **RAG**; achar que **temperature** corrige alucinação; e esquecer que **Bedrock ≠ Free Tier**.

**O plano final:** revise as seções 🔴 e 🟡 do seu `SCORE.md`, refaça os exercícios errados, faça pelo menos um **simulado** completo cronometrado, releia o **Exam Guide oficial** e as **AI Service Cards**. Durma bem — 90 minutos de leitura atenta cansam mais do que parece.

## 🎓 Pontos-chave para a prova

- **65 questões / 90 min / 700 pontos / US$ 100**; +30 min por acomodação de idioma (solicite antes).
- **Nunca deixe em branco**; marque para revisão e volte depois.
- Palavras-chave **MOST/LEAST/BEST** decidem entre alternativas todas corretas.
- "Menor esforço operacional" → **serviço gerenciado**, não construir do zero.
- Domine os pares confundíveis: **Transcribe/Polly**, **Textract/Rekognition**, **RAG/fine-tuning**.
- Foque nos domínios 2 e 3 (**52% da prova**): GenAI e aplicações de FMs.
- Elimine primeiro as alternativas absurdas; sobram duas — decida pela palavra-chave.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Nota de corte | 700 em escala de 100 a 1000 |
| OnVUE | Modalidade de prova online com supervisão remota |
| ESL accommodation | +30 minutos para não nativos em inglês (solicitar antes) |
| Marcar para revisão | Recurso para sinalizar questões e voltar depois |
| Questão de múltipla resposta | Exige selecionar 2 ou mais alternativas corretas |
| Exam Guide | Documento oficial com domínios e escopo |
| Distrator | Alternativa incorreta, porém plausível |

## 💡 Exemplo prático / caso de uso

> *"Uma empresa quer um chatbot que responda com base em 10 mil documentos internos atualizados semanalmente, com **o MENOR esforço operacional** possível."*

Leitura: "documentos internos" → RAG; "atualizados semanalmente" → **descarta fine-tuning**; "menor esforço operacional" → **descarta construir o pipeline manualmente** com Lambda + OpenSearch. Resposta: **Bedrock Knowledge Bases** (ou **Amazon Q Business**, se o cenário enfatizar usuários finais corporativos e permissões). Repare que a decisão veio de **três palavras-chave**, não de conhecimento profundo — é assim que a prova funciona.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
