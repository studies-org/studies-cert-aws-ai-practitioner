# 35. Amazon Translate

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Translate** é o serviço de **tradução automática neural** (*Neural Machine Translation*) da AWS. Ele traduz texto entre dezenas de idiomas com qualidade contextual, superando a tradução palavra a palavra dos sistemas antigos.

Os recursos que caem na prova: **detecção automática do idioma de origem** (você pode informar `auto` e o Translate identifica); **tradução em tempo real** (síncrona, para chats e interfaces) e **batch translation** (assíncrona, para grandes volumes no S3); **Custom Terminology**, que garante que termos específicos — nomes de produtos, marcas, jargão técnico — sejam traduzidos exatamente como você define; **Active Custom Translation (ACT)**, que adapta o modelo ao seu domínio usando exemplos paralelos; e a **redação de profanidade**.

O Translate é frequentemente usado em **pipelines encadeados** com outros serviços de IA — e é assim que a prova costuma apresentá-lo. Áudio em espanhol → **Transcribe** → **Translate** → **Polly** = dublagem automatizada. Avaliações em vários idiomas → **Translate** → **Comprehend** = análise de sentimento multilíngue centralizada.

A fronteira conceitual: **Translate traduz**. Se a questão pede tradução direta e de baixo custo, a resposta é Translate — e não um LLM no Bedrock. Um FM também traduz, mas o Translate é mais barato, mais rápido e determinístico para essa tarefa específica. A escolha de um serviço de IA gerenciado sobre um FM genérico, quando a tarefa é bem definida, é um raciocínio que a prova valoriza.

## 🎓 Pontos-chave para a prova

- Translate = **tradução automática neural**, com **detecção automática do idioma**.
- **Custom Terminology** força a tradução exata de termos específicos (marcas, jargão).
- **Active Custom Translation** adapta a tradução ao domínio com exemplos paralelos.
- Modos **real-time** e **batch** (via S3).
- Pipeline clássico: **Transcribe → Translate → Polly**.
- Para tradução pura, Translate é **mais barato e adequado** que um FM do Bedrock.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Neural Machine Translation | Tradução automática baseada em redes neurais |
| Source/Target language | Idioma de origem e de destino |
| Auto-detection | Identificação automática do idioma de origem |
| Custom Terminology | Dicionário que força traduções específicas de termos |
| Active Custom Translation | Adaptação ao domínio com exemplos paralelos |
| Batch translation | Tradução assíncrona de grandes volumes via S3 |

## 💡 Exemplo prático / caso de uso

Uma SaaS brasileira expande para a América Latina e os EUA. Usa **batch translation** para traduzir 12 mil artigos da base de conhecimento e configura **Custom Terminology** para que o nome do produto e termos como "carteira digital" nunca sejam traduzidos de forma inconsistente. No chat de suporte, usa **tradução em tempo real** com detecção automática: o cliente escreve em espanhol, o atendente lê em português, e a resposta volta traduzida.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
