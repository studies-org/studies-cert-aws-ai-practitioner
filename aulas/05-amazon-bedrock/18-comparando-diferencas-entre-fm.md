# 18. Comparando Diferenças entre FM

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Escolher o Foundation Model certo é uma decisão de **trade-offs**, e a AIF-C01 cobra os critérios. Os principais são: **modalidade** (texto, imagem, embeddings, multimodal), **capacidade/qualidade** de raciocínio, **latência**, **custo por token**, **tamanho da janela de contexto**, **idiomas suportados**, **licenciamento** e **customizabilidade** (nem todo modelo aceita fine-tuning).

O padrão que se repete entre famílias é o de **níveis**: um modelo pequeno e rápido, um intermediário equilibrado e um grande e caro com raciocínio superior. A Amazon usa os nomes **Nova Micro, Lite, Pro e Premier**; a Anthropic usa **Haiku, Sonnet e Opus**. A regra de decisão é a mesma em todas: **use o menor modelo que resolve a tarefa**. Classificar sentimento não precisa do modelo mais caro da família; análise jurídica complexa provavelmente precisa.

Os principais provedores no Bedrock e seus destaques: **Anthropic (Claude)** — raciocínio forte, contexto longo, multimodal; **Amazon (Nova)** — família própria com bom custo-benefício e integração nativa; **Amazon (Titan)** — texto, imagem e especialmente **Titan Embeddings** para RAG; **Meta (Llama)** — modelos de pesos abertos; **Mistral AI** — eficiência e baixo custo; **Cohere** — forte em embeddings e busca empresarial; **AI21 Labs (Jamba)** — contexto longo; **Stability AI (Stable Diffusion)** — geração de imagens.

O trade-off fundamental é: **modelos maiores = melhor raciocínio, maior latência, maior custo**. Modelos menores = mais rápidos e baratos, com qualidade suficiente para tarefas bem definidas. Não existe "melhor modelo" absoluto — existe o adequado ao requisito.

A comparação não deve ser feita no achismo. Ferramentas: o **Playground** para teste manual lado a lado, o **Model Evaluation** do Bedrock (aula 20) para avaliação sistemática com métricas ou juízes humanos, e o **Intelligent Prompt Routing**, que roteia cada requisição dinamicamente ao modelo mais econômico capaz de responder com qualidade.

## 🎓 Pontos-chave para a prova

- Critérios: **modalidade, qualidade, latência, custo, context window, idioma, licença, customizabilidade**.
- Regra de ouro: **use o menor modelo que atende ao requisito**.
- Trade-off: **maior = melhor raciocínio, mais lento, mais caro**.
- **Titan Embeddings / Cohere Embed** → vetores para RAG e busca semântica.
- **Stable Diffusion / Titan Image / Nova Canvas** → geração de imagens.
- **Intelligent Prompt Routing** otimiza custo escolhendo o modelo por requisição.
- Nem todo modelo suporta **fine-tuning** — verifique antes de planejar customização.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Modalidade | Tipo de dado que o modelo processa/gera |
| Context window | Máximo de tokens considerados por invocação |
| Latência | Tempo até a resposta ser produzida |
| Multimodal | Modelo que aceita múltiplos tipos de entrada |
| Modelo de embeddings | Converte texto/imagem em vetores para busca semântica |
| Intelligent Prompt Routing | Roteamento automático entre modelos para otimizar custo/qualidade |
| Customizabilidade | Se o modelo aceita fine-tuning ou continued pre-training |

## 💡 Exemplo prático / caso de uso

Uma empresa tem duas necessidades. (1) Um classificador de sentimento sobre 500 mil avaliações/dia: alto volume, tarefa simples, latência importa → **modelo pequeno e barato** (Nova Micro/Lite, Haiku, Mistral pequeno). (2) Um analista de contratos de 80 páginas que precisa cruzar cláusulas: raciocínio complexo, contexto longo, volume baixo → **modelo grande** (Claude Sonnet/Opus, Nova Pro). Usar o modelo grande no caso (1) multiplicaria o custo sem ganho de qualidade — esse é exatamente o erro que a prova testa.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
