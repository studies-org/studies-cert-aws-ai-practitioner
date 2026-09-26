# 21. O Bedrock Guardrail

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**Amazon Bedrock Guardrails** é o mecanismo de **salvaguardas** que aplica políticas de segurança de conteúdo tanto na **entrada** (prompt do usuário) quanto na **saída** (resposta do modelo). É o serviço que a prova espera como resposta sempre que o cenário envolver "impedir conteúdo inadequado", "bloquear tópicos", "proteger PII" ou "reduzir alucinação com verificação contextual".

As **políticas configuráveis** são: **Content filters** — filtram categorias nocivas (ódio, insultos, sexual, violência, misconduta e **prompt attacks**), com força ajustável em níveis (none/low/medium/high). **Denied topics** — você define tópicos proibidos em linguagem natural (ex.: "aconselhamento de investimento") e o Guardrail os bloqueia. **Word filters** — bloqueia palavras específicas e palavrões. **Sensitive information filters** — detecta **PII** (CPF, e-mail, telefone, cartão) e permite **bloquear** ou **mascarar** (`{NOME}`), inclusive via **regex** customizado. **Contextual grounding check** — mede se a resposta está **fundamentada** na fonte fornecida (grounding) e se é **relevante** à pergunta, bloqueando abaixo de um limiar — é a política anti-alucinação. **Automated Reasoning checks** — validação lógica formal contra regras declaradas, para domínios que exigem exatidão.

Duas características arquiteturais importam. Primeiro, **um Guardrail é independente do modelo**: você o cria uma vez e o aplica a qualquer FM, a Agents e a Knowledge Bases — a política não é reescrita ao trocar de modelo. Segundo, existe a API **`ApplyGuardrail`**, que permite avaliar um texto **sem invocar um FM** — útil para validar conteúdo vindo de modelos fora do Bedrock ou de outras fontes.

Guardrails também suportam **versionamento** (rascunho + versões publicadas) e emitem métricas/logs para **CloudWatch**, permitindo auditar quantas intervenções ocorreram e por qual política.

Um limite conceitual que a prova cobra: Guardrails atua sobre **conteúdo**, não sobre **autorização**. Quem pode chamar o modelo continua sendo definido por **IAM**. Guardrails não substitui controle de acesso.

## 🎓 Pontos-chave para a prova

- Guardrails filtra **entrada e saída**; políticas: content filters, denied topics, word filters, PII, contextual grounding, automated reasoning.
- **Contextual grounding check** é a política para **reduzir alucinação**.
- **Sensitive information filters** podem **bloquear ou mascarar** PII.
- **Prompt attacks** (injection/jailbreak) são cobertos pelos content filters.
- Um Guardrail é **reutilizável entre modelos**, Agents e Knowledge Bases.
- **`ApplyGuardrail`** avalia texto **sem invocar um FM**.
- Guardrails ≠ IAM: conteúdo vs. autorização.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Guardrail | Conjunto de políticas de segurança de conteúdo aplicado a FMs |
| Content filter | Filtro por categoria nociva com força ajustável |
| Denied topic | Tópico proibido definido em linguagem natural |
| Sensitive information filter | Detecção de PII com ação de bloquear ou mascarar |
| Contextual grounding check | Verifica fundamentação e relevância da resposta; anti-alucinação |
| Automated Reasoning check | Validação lógica formal contra regras declaradas |
| ApplyGuardrail | API que avalia texto sem invocar um modelo |
| Blocked message | Mensagem customizada exibida quando o conteúdo é bloqueado |

## 💡 Exemplo prático / caso de uso

Um banco lança um assistente de dúvidas de conta. O Guardrail configurado: **denied topic** "recomendação de investimento" (risco regulatório), **content filters** em `HIGH` para todas as categorias e para prompt attacks, **PII filter** mascarando CPF e número de cartão nos logs, e **contextual grounding check** com limiar alto para que o assistente só responda o que estiver realmente nos documentos da Knowledge Base. Se o usuário perguntar "em qual ação devo investir?", o Guardrail bloqueia e devolve a mensagem customizada — o modelo sequer é consultado.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
