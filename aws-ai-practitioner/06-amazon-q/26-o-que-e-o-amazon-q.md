# 26. O Que é o Amazon Q

> Seção: Amazon Q · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Q** é o assistente de IA Generativa da AWS. A diferença essencial em relação ao Bedrock: o Bedrock é uma **plataforma para você construir** aplicações de IA; o Amazon Q é uma **aplicação pronta** que você configura e usa. Se a questão fala em "construir uma solução customizada com FMs", a resposta é Bedrock; se fala em "solução pronta para os funcionários conversarem com os dados da empresa", é Amazon Q.

A família tem várias variantes, e a prova cobra a distinção. **Amazon Q Business**: assistente para funcionários, que se conecta a fontes de dados corporativas (mais de 40 conectores: S3, SharePoint, Salesforce, Confluence, Jira, Slack, Gmail, Zendesk) e responde perguntas sobre esses dados, **respeitando as permissões de cada usuário**. **Amazon Q Developer** (antigo CodeWhisperer): assistente de código na IDE — gera, explica, refatora e testa código, faz upgrades de versão de linguagem e ajuda a diagnosticar recursos AWS. **Amazon Q in QuickSight**: perguntas em linguagem natural sobre dashboards e dados de BI. **Amazon Q in Connect**: apoio a agentes de call center em tempo real. **Amazon Q Apps**: permite que um usuário crie um pequeno app de IA descrevendo o que quer em linguagem natural.

A característica mais cobrada do Amazon Q Business é o **respeito às permissões existentes**. Ele não é um buraco negro que expõe tudo a todos: se um funcionário não tem acesso a um documento no SharePoint, o Q **não usará esse documento** para responder a ele. Essa integração com o **IAM Identity Center** e com os provedores de identidade corporativos é o que torna o serviço aceitável em empresas.

Assim como o Bedrock, o Amazon Q **não usa seu conteúdo para treinar os modelos base**, e responde com **citações das fontes**, permitindo verificar de onde veio cada afirmação.

## 🎓 Pontos-chave para a prova

- **Bedrock = plataforma para construir**; **Amazon Q = aplicação pronta**.
- **Q Business** → funcionários + dados corporativos, via **40+ conectores**.
- **Q Developer** → assistente de código na IDE (sucessor do CodeWhisperer).
- **Q in QuickSight** → BI em linguagem natural; **Q in Connect** → suporte a atendentes.
- **Q Business respeita as permissões do usuário** nas fontes de dados (via IAM Identity Center).
- Q **cita fontes** e **não treina os modelos base** com seu conteúdo.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Amazon Q Business | Assistente corporativo conectado a dados da empresa |
| Amazon Q Developer | Assistente de desenvolvimento de código e operações AWS |
| Amazon Q Apps | Criação de mini-aplicações de IA por descrição em linguagem natural |
| Conector (data source) | Integração pronta com um sistema corporativo |
| IAM Identity Center | Serviço de identidade usado para autenticar usuários do Q |
| Permissão herdada | Respeito às ACLs originais da fonte de dados |
| Citação | Referência à fonte usada na resposta |

## 💡 Exemplo prático / caso de uso

Uma empresa tem documentação espalhada por SharePoint, Confluence e Jira. Em vez de construir um RAG do zero com Bedrock (embeddings, vector store, sincronização, controle de acesso por documento), configura o **Amazon Q Business** com os três conectores. Um analista pergunta *"qual é o SLA do produto X?"* e recebe a resposta com link para o documento no Confluence. Um estagiário faz a mesma pergunta e recebe menos informação — porque ele não tem acesso àquele espaço. **A permissão foi herdada da fonte, sem configuração adicional.**

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
