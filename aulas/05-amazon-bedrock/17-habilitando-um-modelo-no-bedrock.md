# 17. Habilitando um Modelo no Bedrock

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Os Foundation Models do Bedrock **não vêm habilitados por padrão**. Antes de invocar qualquer modelo, você precisa solicitar acesso em **Bedrock → Model access**, selecionar os modelos desejados e submeter o pedido. Alguns modelos são liberados quase imediatamente; outros (especialmente de provedores terceiros) exigem que você preencha **informações de caso de uso** e aceite o **EULA do provedor**.

O acesso é concedido **por Região e por conta**. Habilitar Claude em `us-east-1` não o habilita em `sa-east-1` — é preciso repetir o processo em cada Região. Esse detalhe é fonte comum de erro em laboratório e de distratores na prova: uma chamada a um modelo não habilitado retorna **`AccessDeniedException`**.

Após a liberação, o modelo aparece com status **Access granted**. Você pode então testá-lo no **Playground** do console (Chat, Text ou Image), que é a forma mais rápida de experimentar prompts e ajustar parâmetros de inferência sem escrever código. O Playground também mostra a contagem de tokens e permite comparar configurações.

Há duas camadas de permissão que não devem ser confundidas. **Model access** é a habilitação do modelo na conta, feita no console do Bedrock. **Permissões IAM** definem quais identidades podem chamar a API (`bedrock:InvokeModel`, `bedrock:InvokeModelWithResponseStream`, `bedrock:ListFoundationModels`). Ter o modelo habilitado mas faltar a permissão IAM também resulta em acesso negado — e vice-versa. A prova gosta dessa distinção.

Vale lembrar dos **cross-Region inference profiles**, que permitem distribuir chamadas entre Regiões para aumentar a resiliência e o throughput — nesse caso o acesso ao modelo precisa estar habilitado nas Regiões envolvidas.

## 🎓 Pontos-chave para a prova

- Modelos **não vêm habilitados**; é preciso solicitar acesso em **Model access**.
- Acesso é concedido **por conta e por Região** — repita em cada Região.
- Modelo não habilitado → **`AccessDeniedException`** ao invocar.
- **Model access ≠ permissão IAM**: são camadas independentes e ambas necessárias.
- O **Playground** permite testar prompts e parâmetros sem escrever código.
- Alguns modelos exigem **detalhes de caso de uso** e aceite de **EULA**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Model access | Habilitação do FM na conta, por Região |
| Access granted | Status que indica modelo liberado para uso |
| EULA | Contrato de licença do provedor do modelo |
| Playground | Console interativo para testar modelos e parâmetros |
| `bedrock:InvokeModel` | Ação IAM que permite invocar um modelo |
| AccessDeniedException | Erro retornado quando falta acesso ao modelo ou permissão IAM |
| Inference profile | Configuração que permite inferência distribuída entre Regiões |

## 💡 Exemplo prático / caso de uso

Um desenvolvedor recebe `AccessDeniedException` ao chamar um modelo. O diagnóstico segue duas frentes: (1) o modelo está com **Access granted** *nesta Região*? (2) A role que executa o código tem a ação **`bedrock:InvokeModel`** para aquele `modelId` no ARN do recurso? Nove em cada dez erros de laboratório estão em uma dessas duas — frequentemente na Região errada.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
