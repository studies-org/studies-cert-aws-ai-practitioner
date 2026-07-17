# 29. Criando a Bucket no S3

> Seção: Amazon Q · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon S3 (Simple Storage Service)** é o serviço de **armazenamento de objetos** da AWS, e é a fonte de dados mais usada em soluções de IA: datasets de treino, documentos para RAG, entrada e saída de batch inference, artefatos de modelo. Praticamente toda arquitetura de IA na AWS tem um bucket no meio.

Um **bucket** é o contêiner dos objetos. O **nome é globalmente único** em toda a AWS (não existem dois buckets com o mesmo nome no mundo), mas o bucket **reside em uma Região específica**. Cada **objeto** tem uma **key** (o caminho, ex.: `docs/politica.pdf`), o conteúdo e **metadados**. O S3 é projetado para **11 noves de durabilidade** (99,999999999%).

As configurações que importam para IA e para a prova: **Block Public Access** vem **ativado por padrão** e deve continuar assim — buckets públicos são a causa clássica de vazamento de dados. **Criptografia em repouso** é aplicada por padrão (**SSE-S3**); para controle próprio de chaves e auditoria, use **SSE-KMS**. **Versionamento** protege contra sobrescrita e exclusão acidental. **Bucket policies** e **IAM policies** controlam o acesso. **CloudTrail data events** auditam acesso a objetos.

Para o laboratório do Q Business, o bucket guarda os documentos que serão indexados. A **service role** do Q precisa de permissão `s3:GetObject` e `s3:ListBucket` sobre esse bucket — e apenas sobre ele (menor privilégio). O bucket deve estar na **mesma Região** da aplicação Q.

Uma nota de custo e boa prática: as **storage classes** (Standard, Intelligent-Tiering, Glacier) otimizam custo por padrão de acesso, e o **lifecycle policy** move objetos automaticamente entre elas. Para IA, dados de treino frios podem ir para Glacier; documentos de RAG ativos ficam em Standard.

## 🎓 Pontos-chave para a prova

- S3 = **armazenamento de objetos**; base de datasets, RAG, batch e artefatos de modelo.
- Nome do bucket é **globalmente único**; o bucket **reside em uma Região**.
- **Block Public Access ativado por padrão** — mantenha assim.
- Criptografia em repouso **por padrão (SSE-S3)**; use **SSE-KMS** para chaves gerenciadas e auditáveis.
- **Versionamento** protege contra sobrescrita/exclusão acidental.
- Serviços acessam o S3 via **IAM role**, com **menor privilégio**.
- Durabilidade de **11 noves**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Bucket | Contêiner de objetos, com nome globalmente único |
| Object | Unidade armazenada: conteúdo + key + metadados |
| Key | Caminho/identificador do objeto dentro do bucket |
| Block Public Access | Configuração que impede exposição pública, ativa por padrão |
| SSE-S3 | Criptografia em repouso com chaves gerenciadas pelo S3 |
| SSE-KMS | Criptografia em repouso com chaves gerenciadas no AWS KMS |
| Versionamento | Retenção de versões anteriores de um objeto |
| Storage class | Nível de armazenamento otimizado por padrão de acesso |
| Lifecycle policy | Regra de transição/expiração automática de objetos |

## 💡 Exemplo prático / caso de uso

Você cria o bucket `q-lab-docs-<seu-nome>` em `us-east-1`, mantém o **Block Public Access ligado**, deixa a criptografia SSE-S3 padrão e sobe alguns PDFs em `docs/`. Ao criar a aplicação do Q, aponta a data source para `s3://q-lab-docs-<seu-nome>/docs/`. A service role gerada recebe `s3:GetObject` **apenas naquele prefixo** — se ela tivesse `s3:*` em `*`, seria uma violação de menor privilégio, e é exatamente esse tipo de detalhe que a prova usa como distrator.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
