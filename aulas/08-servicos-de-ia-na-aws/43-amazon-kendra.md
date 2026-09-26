# 43. Amazon Kendra

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Kendra** é o serviço de **busca empresarial inteligente**. A diferença em relação a uma busca tradicional por palavra-chave é que o Kendra faz **busca semântica**: ele entende a **intenção** da pergunta em linguagem natural e devolve a **resposta**, não apenas uma lista de links.

Os **tipos de consulta** que ele resolve: **Factoid** ("quem é o gerente do projeto X?" → resposta curta e direta), **Descriptive** ("como configuro a VPN?" → trecho explicativo) e **Keyword** (busca tradicional). Ele retorna **Answer** (a resposta extraída), **Document excerpt** (o trecho relevante) e **Document link**.

Os recursos: mais de 40 **conectores** (S3, SharePoint, Salesforce, Confluence, ServiceNow, RDS, web crawler); **ACL-aware search**, filtrando resultados pela permissão do usuário; **FAQs** carregadas explicitamente; **relevance tuning** (dar mais peso a documentos recentes ou a determinadas fontes); **incremental learning** com feedback de cliques; e **filtros por metadados/facetas**.

O Kendra tem **duas edições**: **Developer** (para PoC) e **Enterprise** (produção, com alta disponibilidade). Ambas cobram por **hora de índice provisionado** — e é aqui que mora o perigo. **Kendra é um dos serviços mais caros do curso e cobra 24/7 mesmo sem nenhuma consulta.** Nunca deixe um índice de laboratório ligado.

As fronteiras que a prova cobra: **Kendra × OpenSearch**: Kendra é busca **semântica gerenciada** com NLP pronta; OpenSearch é um motor de busca/análise de propósito geral, mais flexível e barato, mas exige mais construção. **Kendra × Amazon Q Business**: o Q é a **camada conversacional generativa** que pode usar o Kendra como retriever — Kendra **busca e responde**, o Q **conversa e sintetiza**. **Kendra × Bedrock Knowledge Bases**: ambos fazem recuperação para RAG; a KB é a via nativa e mais econômica do Bedrock, enquanto o Kendra brilha quando você já precisa de busca empresarial com muitos conectores e ACLs.

## 🎓 Pontos-chave para a prova

- Kendra = **busca empresarial semântica**, com resposta em linguagem natural.
- Retorna **Answer, excerpt e link**; resolve consultas factoid, descriptive e keyword.
- **40+ conectores** e **ACL-aware search** (respeita permissões do usuário).
- **Relevance tuning**, **FAQs** e **incremental learning** por feedback.
- Edições **Developer** e **Enterprise**; **cobra por hora de índice, mesmo ocioso**.
- Pode ser o **retriever** do Amazon Q Business e de soluções de RAG.
- Busca → Kendra. Análise de texto → Comprehend. Geração → Bedrock.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Busca semântica | Busca por significado e intenção, não por palavra-chave |
| Factoid query | Pergunta com resposta curta e objetiva |
| Answer / Excerpt | Resposta extraída e trecho relevante do documento |
| ACL-aware search | Filtragem de resultados pela permissão do usuário |
| Relevance tuning | Ajuste do peso de campos e fontes na relevância |
| Incremental learning | Melhoria contínua com base no feedback dos usuários |
| Developer / Enterprise Edition | Edições do Kendra, cobradas por hora de índice |

## 💡 Exemplo prático / caso de uso

Uma empresa com 500 mil documentos espalhados em S3, SharePoint e Confluence tem um problema real: ninguém acha nada. Com o **Kendra**, um funcionário pergunta *"qual é a política de reembolso de viagem internacional?"* e recebe a **resposta extraída** do documento certo, com link e trecho — e apenas dos documentos que ele tem permissão de ver. Uma busca por palavra-chave devolveria 200 documentos contendo "reembolso" e deixaria o trabalho para o humano. Encerrado o piloto, o índice **deve ser deletado**: ele cobra por hora, indiferente ao uso.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
