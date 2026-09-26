# 24. Criando um RAG e KB

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Esta é a aula prática: montar uma **Knowledge Base** do zero. O roteiro tem seis passos.

**1. Preparar os dados.** Crie um bucket **S3** e faça upload dos documentos (PDF, TXT, MD, DOCX, HTML, CSV). Organize por prefixo, porque a Knowledge Base sincroniza a partir de um caminho. Além do S3, as Knowledge Bases suportam outras fontes como **web crawler**, **Confluence**, **Salesforce** e **SharePoint**.

**2. Criar a Knowledge Base.** No console do Bedrock → Knowledge Bases → Create. Você define o nome e uma **IAM role** de serviço (o console pode criá-la), que precisa de permissão de leitura no S3 e de acesso ao modelo de embeddings e ao vector store.

**3. Configurar a data source e o chunking.** Aponte o S3 e escolha a estratégia: **fixed-size** (defina tokens por chunk e a sobreposição), **hierarchical**, **semantic** ou **none**. Um ponto de partida razoável é fixed-size com ~300 tokens e 20% de overlap — a sobreposição evita cortar uma frase importante exatamente na fronteira entre dois chunks.

**4. Escolher o modelo de embeddings e o vector store.** Selecione, por exemplo, **Titan Text Embeddings**. Para o vector store, a opção mais simples é deixar o Bedrock **criar automaticamente** um índice no **OpenSearch Serverless**; alternativamente, aponte para Aurora pgvector, Pinecone ou Redis já existentes.

**5. Sincronizar.** Execute o **Sync** da data source. É aqui que o chunking, a geração de embeddings e a indexação acontecem. **Nada funciona antes do primeiro sync** — e este é o erro mais comum do laboratório. Sempre que os documentos mudarem, rode o sync de novo.

**6. Testar.** Use o painel de teste da Knowledge Base, selecione um FM de geração e faça perguntas. Verifique as **citações** retornadas — elas mostram qual chunk fundamentou a resposta e são a melhor ferramenta de depuração: se a citação está errada, o problema é de **recuperação** (chunking/embeddings), não de geração.

**Atenção ao custo:** o **OpenSearch Serverless cobra por OCU e não fica barato ocioso**. Ao terminar o laboratório, **delete a Knowledge Base e a coleção do OpenSearch**. Este é, junto com o Amazon Q Business, o recurso mais perigoso do curso para a fatura.

## 🎓 Pontos-chave para a prova

- Fluxo: **S3 → Knowledge Base → chunking → embeddings → vector store → sync → consulta**.
- **O sync é obrigatório** — sem ele, a base está vazia.
- Fontes suportadas incluem **S3, web crawler, Confluence, Salesforce e SharePoint**.
- A **IAM role** da KB precisa de acesso ao S3, ao modelo de embeddings e ao vector store.
- **Citações** indicam qual chunk fundamentou a resposta (útil para auditoria e debug).
- **OpenSearch Serverless gera custo contínuo** — remova após o laboratório.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Data source | Origem dos documentos da Knowledge Base |
| Sync (ingestion job) | Processo que faz chunking, embedding e indexação |
| Overlap | Sobreposição entre chunks vizinhos |
| OCU | OpenSearch Compute Unit — unidade de cobrança do OpenSearch Serverless |
| Índice vetorial | Estrutura que armazena e busca embeddings |
| Citação | Referência ao chunk/documento usado na resposta |
| Service role | IAM role assumida pela Knowledge Base para acessar recursos |

## 💡 Exemplo prático / caso de uso

Você sobe 10 PDFs de manuais para `s3://kb-lab-aip/manuais/`, cria a KB com **Titan Embeddings** e OpenSearch Serverless, faz o **sync** e pergunta *"como faço o reset de fábrica do modelo X?"*. A resposta cita `manual-x.pdf`, chunk 14. Se ela viesse do manual errado, o ajuste seria no **chunking** ou nos filtros de metadados — não no prompt. Ao encerrar, delete a KB **e** a coleção do OpenSearch: a KB sozinha não remove a infraestrutura vetorial que continua cobrando.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
