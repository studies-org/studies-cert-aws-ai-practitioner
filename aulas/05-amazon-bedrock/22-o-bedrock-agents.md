# 22. O Bedrock Agents

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**Amazon Bedrock Agents** permite que um Foundation Model **execute tarefas de múltiplas etapas** interagindo com sistemas externos. A diferença fundamental em relação a um chatbot: um chatbot **responde**; um agente **age** — consulta APIs, atualiza pedidos, abre chamados, faz cálculos.

O agente funciona por **orquestração**: recebe o pedido do usuário, **decompõe** em passos (*chain of thought*), decide **qual ferramenta chamar**, executa, observa o resultado e repete até concluir. Esse ciclo raciocinar→agir→observar é o padrão **ReAct**.

Os **componentes** que a prova cobra são: **Foundation Model** (o cérebro que raciocina); **Instructions** (o prompt que define o papel e o escopo do agente); **Action Groups** (as ferramentas que ele pode usar, definidas por um **schema OpenAPI** ou por *function definitions*, e implementadas tipicamente por uma **função Lambda**); **Knowledge Bases** (fontes de consulta via RAG); **Prompt templates** (customização das etapas internas de orquestração); e **memória**, que permite reter contexto entre sessões.

O fluxo típico: usuário pergunta → agente raciocina → agente identifica que precisa do status de um pedido → chama o Action Group `getOrderStatus` → o **Lambda** consulta o **DynamoDB** → o resultado volta ao agente → o agente formula a resposta em linguagem natural. Se faltar informação, o agente pode **pedir esclarecimento** ao usuário antes de agir.

Na **segurança**, dois pontos são críticos e caem na prova. Primeiro, o agente executa ações com uma **IAM role** — aplique **menor privilégio**: um agente de consulta não deve ter permissão de escrita. Segundo, **Agents suportam Guardrails**, o que é essencial já que um agente com ferramentas tem superfície de ataque maior (um prompt injection bem-sucedido pode virar uma ação real no sistema).

Para produção, existe o conceito de **alias e versão**: você desenvolve no rascunho (`DRAFT`), publica uma **versão** imutável e aponta um **alias** para ela — o mesmo padrão de promoção usado em Lambda.

## 🎓 Pontos-chave para a prova

- Agents **executam tarefas de múltiplos passos** e chamam sistemas externos — vão além de responder.
- Padrão de raciocínio: **ReAct** (raciocinar → agir → observar).
- **Action Groups** definem as ferramentas via **OpenAPI schema** + **Lambda**.
- Agents integram **Knowledge Bases** (RAG) e **Guardrails**.
- Ações executam sob uma **IAM role** — aplique **menor privilégio**.
- **Versões e aliases** promovem o agente de desenvolvimento para produção.
- Se a questão pede "consultar API e executar ação", a resposta é **Agents**, não RAG puro.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Agent | FM orquestrado para executar tarefas em múltiplos passos |
| Action Group | Conjunto de ações/ferramentas disponíveis ao agente |
| OpenAPI schema | Especificação que descreve as APIs que o agente pode chamar |
| Lambda | Função serverless que implementa a ação do Action Group |
| Orquestração | Processo de decompor a tarefa e decidir os passos |
| ReAct | Padrão de alternância entre raciocínio e ação |
| Memória do agente | Retenção de contexto entre sessões |
| Alias / Versão | Mecanismo de promoção controlada do agente |

## 💡 Exemplo prático / caso de uso

Um e-commerce cria o agente "Assistente de Pedidos". O usuário diz: *"meu pedido 4471 não chegou, quero reembolso"*. O agente (1) consulta a **Knowledge Base** para a política de reembolso, (2) chama o Action Group `getOrder(4471)` via Lambda→DynamoDB e vê que está atrasado 12 dias, (3) verifica que a política autoriza reembolso automático acima de 10 dias, (4) chama `createRefund(4471)` e (5) responde confirmando. Um chatbot comum só explicaria a política; o agente **resolve**. Note que `createRefund` é uma ação **destrutiva** — daí a importância da role restrita e dos Guardrails contra injection.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
