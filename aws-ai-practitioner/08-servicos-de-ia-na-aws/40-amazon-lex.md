# 40. Amazon Lex

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Lex** é o serviço para construir **interfaces conversacionais** — chatbots e bots de voz — usando a mesma tecnologia da Alexa. Ele combina **reconhecimento de fala (ASR)** e **compreensão de linguagem natural (NLU)** para entender a intenção do usuário e conduzir o diálogo.

Os conceitos estruturais são o coração da aula e caem na prova: **Intent** (a intenção do usuário — `ReservarHotel`, `ConsultarSaldo`); **Utterance** (as frases de exemplo que expressam aquela intenção — "quero reservar um quarto", "preciso de hotel"); **Slot** (os parâmetros necessários para atender a intenção — cidade, data, número de hóspedes); **Slot type** (o tipo do parâmetro, embutido ou customizado); **Prompt** (a pergunta que o bot faz para preencher um slot vazio); e **Fulfillment** (a ação executada quando todos os slots estão preenchidos, tipicamente uma função **Lambda**).

O fluxo: o usuário diz "quero reservar um hotel" → Lex identifica a **intent** `ReservarHotel` → percebe que faltam os **slots** `cidade` e `data` → faz os **prompts** correspondentes → com tudo preenchido, chama o **Lambda** de **fulfillment** que executa a reserva de fato.

As integrações típicas: **Amazon Connect** (URA de call center), **Lambda** (lógica de negócio), **Polly** (resposta em voz), **Kendra** (responder perguntas abertas a partir de documentos, via `AMAZON.KendraSearchIntent`), além de Slack, Facebook Messenger e Twilio.

A fronteira com o **Bedrock** merece atenção. Lex é **baseado em intents**: excelente para diálogos **estruturados e transacionais**, com fluxo previsível e integração com sistemas — reservar, consultar, cancelar. Um chatbot com **Bedrock** é **generativo e aberto**: conversa livremente sobre qualquer coisa, mas é menos determinístico. Se a questão fala em fluxo transacional com slots e integração de URA → **Lex**. Se fala em conversa aberta com conhecimento próprio → **Bedrock/Q**. Vale notar que versões recentes do Lex já incorporam recursos generativos para gerar utterances e resumir conversas.

## 🎓 Pontos-chave para a prova

- Lex = **chatbots e bots de voz**; combina **ASR + NLU**; é a tecnologia da Alexa.
- Estrutura: **Intent → Utterances → Slots → Prompts → Fulfillment (Lambda)**.
- Integra nativamente com **Amazon Connect**, Lambda, Polly e Kendra.
- **Lex = diálogo estruturado/transacional**; **Bedrock = conversa generativa aberta**.
- `AMAZON.KendraSearchIntent` permite responder perguntas abertas via documentos.
- Suporta versões e aliases para promover bots a produção.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Intent | Objetivo que o usuário quer alcançar |
| Utterance | Frase de exemplo que expressa uma intent |
| Slot | Parâmetro necessário para atender a intent |
| Slot type | Tipo de dado do slot (embutido ou customizado) |
| Prompt | Pergunta feita pelo bot para preencher um slot |
| Fulfillment | Execução da ação quando todos os slots estão completos |
| NLU | Natural Language Understanding |
| Amazon Connect | Serviço de call center que integra com o Lex |

## 💡 Exemplo prático / caso de uso

Um banco cria a URA `AtendimentoBanco` no **Amazon Connect** com um bot **Lex**. O cliente liga e diz: *"quero saber o saldo da minha conta"*. O Lex identifica a intent `ConsultarSaldo`, percebe que falta o slot `tipoConta` e pergunta "corrente ou poupança?". Com o slot preenchido, o **Lambda** de fulfillment consulta o core bancário e devolve o valor, que o **Polly** fala de volta. Fluxo determinístico, auditável e integrado — exatamente onde o Lex vence um chatbot generativo aberto.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
