# 34. Amazon Comprehend

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Comprehend** é o serviço gerenciado de **NLP (Processamento de Linguagem Natural)** da AWS. Ele **extrai insights de texto** sem que você precise treinar modelo algum: você envia o texto pela API e recebe a análise pronta.

As capacidades principais são: **Análise de sentimento** (positivo, negativo, neutro ou misto — e o *targeted sentiment*, que identifica o sentimento em relação a **entidades específicas** dentro do texto); **Detecção de entidades** (pessoas, lugares, organizações, datas, quantidades); **Extração de key phrases**; **Detecção de idioma**; **Modelagem de tópicos** (agrupa documentos por tema — uma aplicação **não supervisionada**); **Detecção de PII** (dados pessoais identificáveis, com opção de redação); e **classificação e reconhecimento de entidades customizados**, em que você treina o Comprehend com suas próprias categorias/entidades sem escrever código de ML.

Há uma variante especializada importante: o **Amazon Comprehend Medical**, que extrai informações de textos clínicos (medicamentos, dosagens, diagnósticos, procedimentos) e é compatível com **HIPAA**.

A distinção que a prova cobra: **Comprehend analisa e entende texto** (classifica, extrai, detecta). Ele **não gera** texto — para gerar, é Bedrock. E ele **não faz busca** — para busca empresarial, é Kendra. Comprehend também não traduz (Translate) nem transcreve áudio (Transcribe), embora seja comum encadeá-lo com esses serviços.

## 🎓 Pontos-chave para a prova

- Comprehend = **NLP gerenciado**: sentimento, entidades, key phrases, idioma, tópicos, **PII**.
- **Targeted sentiment** identifica o sentimento em relação a entidades específicas.
- **Custom classification** e **custom entity recognition** permitem categorias próprias **sem código de ML**.
- **Comprehend Medical** para textos clínicos, compatível com **HIPAA**.
- **Detecção/redação de PII** é uma função-chave para privacidade.
- Comprehend **analisa** texto; **não gera** (isso é Bedrock) e **não busca** (isso é Kendra).

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| NLP | Processamento de Linguagem Natural |
| Análise de sentimento | Classificação do tom em positivo/negativo/neutro/misto |
| Targeted sentiment | Sentimento em relação a uma entidade específica |
| Entity recognition | Identificação de entidades nomeadas no texto |
| Key phrase | Expressão-chave que resume o conteúdo |
| Topic modeling | Agrupamento não supervisionado de documentos por tema |
| PII | Personally Identifiable Information |
| Comprehend Medical | Variante para textos clínicos, compatível com HIPAA |

## 💡 Exemplo prático / caso de uso

Um e-commerce processa 50 mil avaliações por dia. O **Comprehend** faz análise de **sentimento** e extrai **key phrases** e **entidades** de cada uma. O resultado alimenta um dashboard que mostra que o sentimento sobre "entrega" despencou na última semana. Usando **targeted sentiment**, o time descobre que a avaliação "o produto é ótimo, mas a entrega foi péssima" é **positiva sobre o produto** e **negativa sobre a entrega** — nuance que uma classificação global do documento perderia.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
