# 25. Machine Learning com Inferência

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**Inferência** é o ato de usar um modelo já treinado para produzir uma saída. É a fase que **roda continuamente em produção** e, por isso, é onde mora a maior parte do custo ao longo do tempo — o treino acontece uma vez, a inferência acontece milhões de vezes.

Os **tipos de inferência** que a prova cobra: **Real-time (síncrona)** — resposta imediata, baixa latência, para chatbots e APIs interativas; **Streaming** — a resposta chega token a token (`InvokeModelWithResponseStream`), melhorando a **latência percebida** sem mudar o tempo total; **Batch (assíncrona)** — grandes volumes via S3, com desconto de ~50%, para quando latência não importa; e, no SageMaker, também **Asynchronous inference** (payloads grandes, fila) e **Serverless inference** (tráfego intermitente, escala a zero).

Os **parâmetros de inferência** (temperature, top-P, top-K, max tokens, stop sequences) foram vistos na aula 10 e são configurados em cada invocação — eles afetam a saída sem tocar no modelo.

O **Provisioned Throughput** do Bedrock reserva capacidade em **model units**, garantindo vazão previsível e sendo requisito para servir a maioria dos **modelos customizados**. Já as otimizações de custo/latência mais cobradas são o **prompt caching** (reutiliza o processamento de porções repetidas do prompt — ideal quando um system prompt longo ou um documento se repete em muitas chamadas) e o **Intelligent Prompt Routing** (roteia cada requisição ao modelo mais econômico que dê conta).

O trio de trade-offs a memorizar: **latência, custo e qualidade**. Modelo maior → melhor qualidade, pior latência, maior custo. Batch → menor custo, latência alta. Streaming → melhor experiência percebida. Provisioned → latência previsível, custo fixo.

Por fim, **monitoramento**: o **CloudWatch** coleta métricas de invocação, latência e contagem de tokens; o **CloudTrail** registra as chamadas de API para auditoria; e o **model invocation logging** do Bedrock pode gravar prompts e respostas em S3 ou CloudWatch Logs — recurso valioso para governança, e que exige cuidado com **PII** nos logs.

## 🎓 Pontos-chave para a prova

- **Inferência** = usar o modelo treinado; é onde está o custo recorrente.
- **Real-time** (baixa latência) · **Streaming** (melhora latência percebida) · **Batch** (~50% mais barato, assíncrono).
- **Provisioned Throughput** = capacidade reservada em model units; exigido para modelos customizados.
- **Prompt caching** reduz custo/latência quando há contexto repetido entre chamadas.
- **Intelligent Prompt Routing** escolhe dinamicamente o modelo mais econômico adequado.
- Monitoramento: **CloudWatch** (métricas/logs), **CloudTrail** (auditoria de API), **model invocation logging** (prompts e respostas).

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Inferência | Uso do modelo treinado para gerar previsões/respostas |
| Real-time inference | Inferência síncrona de baixa latência |
| Streaming | Entrega incremental da resposta, token a token |
| Batch inference | Processamento assíncrono em lote, com desconto |
| Latência percebida | Tempo até o usuário ver o início da resposta |
| Model unit | Unidade de capacidade do Provisioned Throughput |
| Prompt caching | Reuso do processamento de partes repetidas do prompt |
| Model invocation logging | Registro de prompts e respostas em S3/CloudWatch |
| Cold start | Latência inicial ao acionar capacidade ociosa |

## 💡 Exemplo prático / caso de uso

Um assistente jurídico injeta o mesmo contrato de 30 páginas em dezenas de perguntas seguidas. Sem otimização, cada pergunta reprocessa (e paga por) todos os tokens do contrato. Ativando **prompt caching**, o contexto repetido é reaproveitado — custo e latência caem drasticamente. Como o usuário está esperando na tela, a resposta usa **streaming**, então ele vê o texto surgindo imediatamente em vez de encarar um spinner por 8 segundos. Já o relatório mensal que resume 100 mil contratos roda em **batch**, de madrugada, por metade do preço.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
