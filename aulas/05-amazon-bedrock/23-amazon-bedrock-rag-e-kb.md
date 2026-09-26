# 23. Amazon Bedrock RAG e KB

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**RAG (Retrieval-Augmented Generation)** é a técnica de **recuperar** informação relevante de uma base de conhecimento e **injetá-la no contexto** do prompt, para que o modelo responda com base em fatos reais em vez da memória do treino. É a resposta canônica da prova para **reduzir alucinação** e para **dar ao modelo acesso a dados privados e atualizados** — sem alterar seus pesos.

O funcionamento tem duas fases. **Ingestão (offline)**: os documentos no **S3** são divididos em pedaços (**chunking**), cada pedaço é convertido em vetor por um **modelo de embeddings** (ex.: Titan Embeddings, Cohere Embed) e armazenado em um **banco vetorial**. **Consulta (online)**: a pergunta do usuário também vira embedding, o sistema faz **busca por similaridade** (vizinhos mais próximos) no banco vetorial, recupera os trechos mais relevantes e os injeta no prompt junto da pergunta. O modelo então responde **fundamentado** naqueles trechos — e pode **citar as fontes**.

As **Knowledge Bases for Amazon Bedrock** entregam esse pipeline **gerenciado**: você aponta a fonte de dados, escolhe o modelo de embeddings e o banco vetorial, e o serviço cuida de chunking, embedding, indexação e sincronização. As opções de **vector store** que caem na prova: **Amazon OpenSearch Serverless** (padrão), **Amazon Aurora PostgreSQL com pgvector**, **Amazon Neptune Analytics** (para GraphRAG), **Amazon Kendra** e opções de terceiros como **Pinecone**, **Redis Enterprise Cloud** e **MongoDB Atlas**. As APIs principais são **`Retrieve`** (só recupera os trechos) e **`RetrieveAndGenerate`** (recupera e já gera a resposta).

O **chunking** tem estratégias: **fixed-size** (tamanho fixo com sobreposição), **hierarchical** (pai/filho), **semantic** (corta por unidade de significado) ou **none** (o documento inteiro é um chunk). Chunks pequenos dão precisão mas podem perder contexto; chunks grandes preservam contexto mas trazem ruído.

O contraste que a prova exige: **RAG vs. fine-tuning**. RAG **não altera o modelo**, é **atualizável na hora** (basta reindexar), permite **citar fontes** e **respeita permissões por documento**. Fine-tuning **altera os pesos**, cristaliza o conhecimento e exige novo treino a cada atualização. Conhecimento que muda → **RAG**. Estilo/formato persistente → **fine-tuning**.

## 🎓 Pontos-chave para a prova

- **RAG = recuperar + injetar no contexto**; principal mitigação de **alucinação**.
- Fases: **ingestão** (chunk → embedding → vector store) e **consulta** (busca por similaridade → contexto → geração).
- **Knowledge Bases** é o RAG **gerenciado** do Bedrock.
- Vector stores: **OpenSearch Serverless**, **Aurora pgvector**, **Neptune Analytics**, **Kendra**, **Pinecone**, **Redis**, **MongoDB Atlas**.
- APIs: **`Retrieve`** e **`RetrieveAndGenerate`**.
- RAG permite **citar fontes** e **atualizar sem re-treinar**; fine-tuning não.
- **Embeddings** são o que torna a busca **semântica** (por significado, não por palavra-chave).

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| RAG | Retrieval-Augmented Generation |
| Knowledge Base | Pipeline de RAG gerenciado do Bedrock |
| Chunking | Divisão dos documentos em pedaços indexáveis |
| Embedding | Vetor que representa o significado de um texto |
| Vector store | Banco otimizado para busca por similaridade vetorial |
| Busca semântica | Busca por significado, via proximidade entre vetores |
| Similaridade de cosseno | Métrica comum de proximidade entre embeddings |
| RetrieveAndGenerate | API que recupera trechos e gera a resposta |
| Grounding | Fundamentação da resposta nos trechos recuperados |
| Citação de fonte | Referência ao documento de origem da informação |

## 💡 Exemplo prático / caso de uso

O RH tem 400 PDFs de políticas internas. Sem RAG, o FM inventa respostas — nunca viu esses documentos. Com uma **Knowledge Base**: os PDFs vão para o **S3**, o Bedrock faz chunking e gera embeddings com o **Titan Embeddings**, indexando no **OpenSearch Serverless**. Quando um funcionário pergunta *"quantos dias de licença-paternidade eu tenho?"*, a pergunta vira vetor, os 3 chunks mais próximos são recuperados da política de benefícios e injetados no prompt. O modelo responde **com base no texto real** e **cita o PDF de origem**. Quando o RH altera a política, basta **sincronizar a base** — nenhum re-treino envolvido.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
