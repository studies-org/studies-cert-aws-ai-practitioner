# 27. Como Funciona o Amazon Q

> Seção: Amazon Q · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Por baixo do capô, o **Amazon Q Business** é um **RAG gerenciado de ponta a ponta** com controle de acesso embutido. A arquitetura tem quatro peças: a **Application** (a instância do Q), o **Retriever/Index** (onde o conteúdo é indexado — nativo do Q ou o **Amazon Kendra**), as **Data sources** (os conectores) e a **Web experience** (a interface de chat entregue aos usuários).

O fluxo de ingestão: você conecta uma data source, define o **sync schedule** (sob demanda, horário ou diário), e o Q **rastreia os documentos e também as ACLs** de cada um. Esse segundo ponto é o pulo do gato: o índice guarda não só o conteúdo, mas **quem pode vê-lo**. No momento da consulta, o Q filtra os resultados pela identidade do usuário autenticado antes de montar o contexto para o modelo.

A autenticação acontece via **IAM Identity Center**, que pode federar com o provedor de identidade da empresa (Okta, Entra ID/Azure AD, Ping). O usuário faz login, o Q sabe quem ele é, e a busca é filtrada de acordo.

Existem **dois planos de assinatura** do Q Business: **Lite** e **Pro**, cobrados **por usuário/mês**. A implicação prática — e a armadilha do laboratório — é que **a cobrança é por assinatura, não por uso**: um usuário que nunca abre o chat continua sendo cobrado enquanto a assinatura existir. Por isso a aula 32 é inteiramente sobre remover o serviço.

Os **Plugins** estendem o Q para **executar ações** em sistemas externos (criar um ticket no Jira, abrir um caso no Salesforce, ServiceNow), de forma análoga aos Action Groups dos Agents. E os **Admin controls / Guardrails** do Q permitem restringir tópicos, bloquear palavras e decidir se o modelo pode responder usando **conhecimento geral** ou **apenas os documentos da empresa** — um controle importante para reduzir alucinação em contexto corporativo.

## 🎓 Pontos-chave para a prova

- Q Business = **RAG gerenciado** com **ACL-aware retrieval**: o índice armazena conteúdo **e permissões**.
- Autenticação via **IAM Identity Center**, federável com IdPs corporativos.
- Componentes: **Application, Retriever/Index, Data sources, Web experience**.
- **Sync** pode ser sob demanda ou agendado; sem sync não há conteúdo indexado.
- Cobrança por **assinatura de usuário (Lite/Pro)** — cobra mesmo ocioso.
- **Plugins** executam ações em sistemas externos (Jira, Salesforce, ServiceNow).
- **Admin controls** permitem limitar respostas apenas aos documentos da empresa.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Application | Instância do Amazon Q Business |
| Retriever / Index | Componente que indexa e recupera o conteúdo |
| Data source connector | Integração que ingere conteúdo de um sistema |
| ACL | Access Control List — permissões do documento na fonte original |
| Sync schedule | Frequência de sincronização da data source |
| Web experience | Interface de chat entregue aos usuários |
| Plugin | Extensão que permite ao Q executar ações externas |
| Lite / Pro | Planos de assinatura por usuário/mês |
| Admin controls | Políticas de tópicos, palavras e escopo das respostas |

## 💡 Exemplo prático / caso de uso

O TI conecta o Q Business ao SharePoint com sync diário. O índice guarda o documento "Plano de Remuneração 2026" junto com sua ACL: apenas o grupo `RH-Gestores`. Quando a diretora de RH pergunta sobre bandas salariais, o documento entra no contexto e ela recebe a resposta com citação. Quando um analista de outra área faz a mesma pergunta, o filtro por identidade **remove o documento antes da recuperação** — o modelo nunca o vê e responde que não encontrou informação. Nenhuma regra extra foi escrita: a permissão veio do SharePoint.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
