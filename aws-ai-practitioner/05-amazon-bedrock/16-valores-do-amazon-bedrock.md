# 16. Valores do Amazon Bedrock

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O Bedrock tem **modos de cobrança** distintos, e escolher o certo para cada cenário é uma questão recorrente na prova.

**On-Demand**: você paga **por token de entrada e por token de saída**, sem compromisso. Tokens de saída costumam custar mais que os de entrada. É o modo padrão, ideal para cargas variáveis, provas de conceito e volumes baixos ou imprevisíveis. Para modelos de imagem, a cobrança é por imagem gerada; para embeddings, por token de entrada.

**Provisioned Throughput**: você compra **unidades de modelo (model units)** que garantem capacidade e vazão, com compromisso de **1 mês ou 6 meses** (o compromisso mais longo tem desconto maior). É indicado para cargas **altas, constantes e previsíveis**, quando você precisa de throughput garantido — e é **obrigatório** para servir a maioria dos **modelos customizados** (fine-tuned).

**Batch inference**: processa grandes volumes de forma assíncrona a partir de arquivos no S3, com **desconto de cerca de 50%** em relação ao On-Demand. É a escolha quando o processamento **não é sensível à latência** — classificar um milhão de avaliações durante a noite, por exemplo.

Além disso existem: **Model customization**, cobrado pelo tempo de treino, pelo armazenamento do modelo customizado e depois pela inferência (via Provisioned Throughput); e a **Marketplace/serverless de modelos terceiros**, com preços do próprio provedor.

As alavancas para **reduzir custo** são as mais cobradas: escolher um **modelo menor** quando ele resolve a tarefa (um modelo pequeno pode custar uma ordem de grandeza menos que o maior da família); **encurtar prompts** e limitar `max tokens`; usar **batch** para trabalho assíncrono; aplicar **prompt caching** para reaproveitar contexto repetido; e usar **Intelligent Prompt Routing** para direcionar automaticamente cada requisição ao modelo mais econômico capaz de atendê-la. Rastrear tudo isso é papel do **Cost Explorer**, do **AWS Budgets** e das **tags de alocação de custo**.

## 🎓 Pontos-chave para a prova

- **On-Demand**: por token, sem compromisso — cargas variáveis e PoCs.
- **Provisioned Throughput**: model units com compromisso de **1 ou 6 meses** — carga alta e previsível; **necessário para modelos customizados**.
- **Batch**: assíncrono via S3, **~50% mais barato** — quando latência não importa.
- Tokens de **saída** normalmente custam mais que os de **entrada**.
- Reduzir custo: modelo menor, prompt curto, `max tokens` menor, batch, prompt caching, routing.
- **Bedrock não está no Free Tier** — cobra desde a primeira chamada.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| On-Demand | Cobrança por token consumido, sem compromisso |
| Provisioned Throughput | Capacidade reservada em model units com compromisso de prazo |
| Model Unit (MU) | Unidade de capacidade de throughput de um modelo |
| Batch inference | Inferência assíncrona em lote via S3, com desconto |
| Prompt caching | Reuso de porções repetidas do prompt para reduzir custo e latência |
| Intelligent Prompt Routing | Roteamento automático da requisição ao modelo mais adequado/econômico |
| Cost allocation tags | Tags que permitem atribuir custos a times/projetos |

## 💡 Exemplo prático / caso de uso

Uma empresa tem duas cargas. A primeira é um chatbot de atendimento com picos imprevisíveis → **On-Demand**, pagando só pelo que usa. A segunda é a classificação noturna de 2 milhões de tickets acumulados → **Batch inference**, cortando cerca de metade do custo, já que ninguém espera a resposta em tempo real. Quando o chatbot amadurece e passa a ter tráfego alto e constante 24/7 com um modelo fine-tuned, a empresa migra para **Provisioned Throughput** com compromisso de 6 meses.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
