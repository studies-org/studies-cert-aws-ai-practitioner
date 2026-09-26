# 14. O Que é o Amazon Bedrock

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Bedrock** é o serviço **totalmente gerenciado e serverless** da AWS para construir aplicações de IA Generativa. Ele oferece, através de uma **única API**, acesso a **Foundation Models (FMs)** de diversos provedores — Anthropic (Claude), Amazon (Nova, Titan), Meta (Llama), Mistral AI, Cohere, AI21 Labs e Stability AI — além dos recursos ao redor: customização, Guardrails, Agents, Knowledge Bases e avaliação de modelos.

O ponto central que a prova cobra é o **"serverless"**: você **não provisiona nem gerencia infraestrutura**. Não há instância para escolher, cluster para dimensionar nem GPU para configurar. Você chama a API, o modelo responde, você paga pelo consumo. Isso contrasta diretamente com o **SageMaker**, onde você controla instâncias, treina modelos próprios e gerencia endpoints.

A **privacidade dos dados** é o segundo ponto crítico. **Seus prompts e respostas não são usados para treinar os modelos base**, não são compartilhados com os provedores dos modelos e trafegam criptografados. Quando você customiza um modelo, é criada uma **cópia privada** do FM na sua conta — o modelo original do provedor não é alterado, e nenhum outro cliente tem acesso à sua versão. Essa garantia é o que torna o Bedrock aceitável para setores regulados, e aparece com frequência nas questões.

A **integração com o ecossistema AWS** completa o quadro: **IAM** para controle de acesso, **PrivateLink** para acesso privado sem passar pela internet, **KMS** para criptografia, **CloudWatch** para métricas e logs, **CloudTrail** para auditoria de chamadas de API e **VPC** para isolamento de rede.

As principais capacidades expostas pelo serviço são: invocação de modelos (`InvokeModel` e a API unificada **Converse**), **Knowledge Bases** (RAG gerenciado), **Agents** (execução de tarefas em múltiplos passos com ferramentas), **Guardrails** (políticas de segurança de conteúdo), **Model Evaluation** (avaliação automática ou com humanos), **Prompt Management/Flows** e customização via fine-tuning e continued pre-training.

## 🎓 Pontos-chave para a prova

- Bedrock é **serverless e totalmente gerenciado** — sem provisionar infraestrutura.
- **API única** para múltiplos provedores de FMs; trocar de modelo é mudar o `modelId`.
- **Seus dados não treinam os modelos base** e não são compartilhados com os provedores.
- Customização gera uma **cópia privada** do modelo na sua conta.
- Integra com **IAM, KMS, PrivateLink, VPC, CloudWatch e CloudTrail**.
- Bedrock = **usar/adaptar FMs**; SageMaker = **construir/treinar modelos próprios**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Foundation Model (FM) | Modelo pré-treinado em larga escala, adaptável a muitas tarefas |
| Serverless | Sem provisionamento ou gestão de servidores pelo cliente |
| InvokeModel | Operação de API para invocar um FM |
| Converse API | API unificada do Bedrock para conversas multi-turno entre modelos |
| Model ID | Identificador do modelo (ex.: `anthropic.claude-...`) |
| PrivateLink | Conectividade privada a serviços AWS sem trafegar pela internet |
| CloudTrail | Serviço de auditoria de chamadas de API |
| Cópia privada | Instância customizada do FM isolada na sua conta |

## 💡 Exemplo prático / caso de uso

Uma seguradora quer um assistente que responda dúvidas de apólices sem que qualquer dado do segurado saia do seu perímetro. Escolhe **Bedrock** por três razões: os dados **não treinam o modelo base**, o acesso é controlado por **IAM** e pode ser feito via **PrivateLink** dentro da VPC, e tudo é auditável pelo **CloudTrail**. Se depois quiser trocar de FM, basta apontar para outro `modelId` — sem reescrever a aplicação.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
