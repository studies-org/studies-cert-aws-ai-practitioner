# Exercícios — 06. Amazon Q

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_, 6-_, 7-_

## Questões

### 1. Qual é a diferença fundamental entre Amazon Bedrock e Amazon Q Business?
- A) Bedrock é uma aplicação pronta; Q Business é uma plataforma de desenvolvimento
- B) Bedrock é uma plataforma para construir soluções com FMs; Q Business é uma aplicação pronta de assistente corporativo
- C) São o mesmo serviço com interfaces diferentes
- D) Bedrock só funciona com modelos Amazon; Q Business com modelos de terceiros

### 2. Um funcionário pergunta ao Amazon Q Business sobre um documento ao qual ele não tem acesso no SharePoint. O que acontece?
- A) O Q responde normalmente, pois indexou o documento
- B) O Q filtra o documento com base nas ACLs herdadas e não o usa para responder a esse usuário
- C) O Q responde e registra uma violação de segurança
- D) O Q exige aprovação do administrador em tempo real

### 3. Qual serviço de identidade é exigido pelo Amazon Q Business para autenticar usuários finais?
- A) IAM users com access keys
- B) IAM Identity Center
- C) Amazon Cognito user pools
- D) Usuário root da conta

### 4. Um desenvolvedor quer um assistente que gere e explique código dentro da IDE. Qual variante do Amazon Q é a correta?
- A) Amazon Q Business
- B) Amazon Q Developer
- C) Amazon Q in QuickSight
- D) Amazon Q in Connect

### 5. Após concluir o laboratório, qual é o primeiro passo para estancar a cobrança do Q Business?
- A) Desligar a Web experience
- B) Remover as subscriptions dos usuários
- C) Esvaziar o bucket S3
- D) Deletar o usuário no IAM Identity Center

### 6. O Amazon Q Business responde a uma pergunta corporativa de forma confiante, mas sem apresentar nenhuma citação. Qual é a causa mais provável?
- A) O sync da data source falhou completamente
- B) O modelo respondeu usando conhecimento geral, que está habilitado nos Admin controls
- C) O usuário não tem permissão para ver citações
- D) O retriever Kendra não suporta citações

### 7. Quais recursos continuam gerando custo mesmo quando ociosos? (Escolha a melhor opção)
- A) Buckets S3 vazios e IAM roles
- B) Amazon Q Business subscriptions, índices Kendra e OCUs do OpenSearch Serverless
- C) Prompts salvos no Prompt Management
- D) Modelos habilitados em Model access

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — **Bedrock é plataforma** (você constrói: escolhe FMs, monta RAG, cria agentes). **Q Business é aplicação pronta** (você configura conectores e entrega o chat aos funcionários). Essa distinção "construir vs. consumir" decide várias questões do exame.

2. **B** — O Q Business faz **ACL-aware retrieval**: o índice armazena o conteúdo **e as permissões** da fonte original. Documentos fora do alcance do usuário são filtrados **antes** da recuperação, então o modelo sequer os vê.

3. **B** — O **IAM Identity Center** é obrigatório. O Q precisa da identidade do usuário final para filtrar resultados por permissão, algo que IAM users com access keys não modelam adequadamente.

4. **B** — **Amazon Q Developer** (sucessor do CodeWhisperer) é o assistente de código na IDE. Q Business é para dados corporativos, Q in QuickSight para BI e Q in Connect para call center.

5. **B** — A cobrança principal é a **assinatura por usuário/mês**, então **remover as subscriptions** é o que a interrompe. Depois se deleta a Application e os recursos relacionados (S3, Kendra, roles).

6. **B** — Resposta sem citação significa que ela **não veio dos documentos indexados**. Nos **Admin controls** é possível restringir o Q a responder apenas com base no conteúdo da empresa — configuração recomendada para reduzir alucinação em contexto corporativo.

7. **B** — Todos os três são **capacidade provisionada**: a assinatura do Q cobra por usuário/mês, o **Kendra** cobra por hora de índice e o **OpenSearch Serverless** cobra por OCU. Buckets S3 vazios e IAM roles não geram custo relevante, e habilitar um modelo no Bedrock não cobra nada por si só.

</details>
