# 15. Como Funciona o Bedrock e FM

> Seção: Amazon Bedrock · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Um **Foundation Model (FM)** é um modelo de deep learning treinado em um volume gigantesco de dados não rotulados, de forma **auto-supervisionada**, resultando em um modelo de propósito geral que pode ser **adaptado** a muitas tarefas. O "foundation" vem daí: ele é a fundação sobre a qual você constrói, em vez de treinar um modelo específico do zero para cada problema.

A arquitetura por trás da maioria dos FMs de texto é o **Transformer**, introduzido no artigo *"Attention Is All You Need"* (2017). O mecanismo central é a **self-attention**, que permite ao modelo pesar a importância relativa de cada token em relação a todos os outros — é o que resolve dependências de longo alcance ("o **cachorro** que estava no parque **latiu**"). Um **LLM (Large Language Model)** é um FM de texto: ele é, na essência, um preditor do próximo token, aplicado repetidamente.

O ciclo de vida de um FM tem três estágios que a prova gosta de distinguir. **Pre-training**: treino massivo e caríssimo em dados gerais (feito pelo provedor, custa milhões). **Fine-tuning**: ajuste com um dataset menor e específico. **Alinhamento (RLHF)**: ajuste do comportamento às preferências humanas.

Os FMs se dividem por **modalidade**: modelos de **texto** (Claude, Llama, Mistral, Amazon Nova), de **embeddings** (Titan Embeddings, Cohere Embed — convertem texto em vetores para busca semântica e RAG), de **imagem** (Stable Diffusion, Titan Image Generator, Amazon Nova Canvas) e **multimodais** (aceitam texto + imagem, como Claude e Amazon Nova). Saber que **embeddings são a base do RAG** é essencial.

A limitação mais cobrada é a **alucinação**: o modelo gera conteúdo plausível mas factualmente incorreto, com total confiança. A causa é que ele otimiza plausibilidade estatística, não veracidade. Outras limitações: **knowledge cutoff** (não sabe de eventos após a data de treino), **falta de acesso a dados privados**, **não determinismo** e **viés herdado dos dados de treino**. As mitigações canônicas são **RAG** (dá acesso a fatos), **Guardrails** (filtra saídas), **citações de fontes** e **human-in-the-loop**.

## 🎓 Pontos-chave para a prova

- FM = pré-treinado em larga escala, **auto-supervisionado**, adaptável a várias tarefas.
- Arquitetura dominante = **Transformer**; mecanismo = **self-attention**.
- Estágios: **pre-training → fine-tuning → alinhamento (RLHF)**.
- **Embeddings** convertem texto em vetores e são a base do **RAG** e da busca semântica.
- **Alucinação** = saída plausível porém incorreta; mitigue com **RAG**, Guardrails e revisão humana.
- **Knowledge cutoff**: o FM desconhece eventos posteriores ao seu treino.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Foundation Model | Modelo de propósito geral pré-treinado em larga escala |
| Transformer | Arquitetura de rede neural baseada em atenção |
| Self-attention | Mecanismo que pondera a relevância entre todos os tokens |
| LLM | Large Language Model — FM especializado em texto |
| Pre-training | Treino inicial massivo em dados gerais |
| Embedding | Representação vetorial que captura significado semântico |
| Multimodal | Modelo que aceita mais de um tipo de entrada (ex.: texto + imagem) |
| Alucinação | Geração de conteúdo plausível mas factualmente incorreto |
| Knowledge cutoff | Data limite do conhecimento adquirido no treino |
| Auto-supervisionado | Treino que gera os próprios rótulos a partir dos dados |

## 💡 Exemplo prático / caso de uso

Um usuário pergunta ao FM "qual foi o faturamento da minha empresa no último trimestre?". O modelo **inventa um número plausível** — ele nunca viu esse dado, mas seu objetivo é produzir texto verossímil. A correção não é ajustar temperature: é **RAG**, conectando o modelo ao relatório financeiro real via **Knowledge Base**, para que ele responda com base em um trecho recuperado e possa **citar a fonte**.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
