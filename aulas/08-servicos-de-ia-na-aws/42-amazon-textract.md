# 42. Amazon Textract

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Textract** extrai **texto, dados estruturados e relações** de documentos digitalizados. Ele vai muito além do OCR tradicional: um OCR comum devolve uma sopa de caracteres; o Textract entende que aquele texto é um **campo de formulário**, uma **célula de tabela** ou uma **assinatura**.

As capacidades são organizadas em APIs: **Detect Document Text** (OCR simples — texto e linhas); **Analyze Document** com as features **FORMS** (pares chave-valor: "Nome: João" vira `{Nome: João}`), **TABLES** (preserva a estrutura de linhas e colunas), **SIGNATURES** (detecta assinaturas) e **LAYOUT** (identifica títulos, parágrafos e listas — muito útil para preparar documentos para **RAG**); **Analyze Expense** (recibos e faturas, com campos de negócio já reconhecidos); **Analyze ID** (documentos de identidade); e **Queries**, que permite simplesmente **perguntar** ao documento ("qual é o valor total?") sem configurar template algum.

O modo de operação é **síncrono** (documento único, poucas páginas) ou **assíncrono** (multipágina, PDFs grandes no S3, com notificação via SNS). A saída inclui **confidence score** por elemento, o que habilita fluxos de revisão: itens abaixo de um limiar vão para revisão humana via **Amazon A2I** — integração nativa e frequentemente cobrada.

A fronteira mais cobrada de toda a seção 08: **Textract × Rekognition**. **Textract = documentos** (formulários, tabelas, faturas, contratos). **Rekognition = imagens e cenas** (objetos, faces, texto curto em placas). Se a palavra "documento", "formulário", "fatura" ou "tabela" aparece na questão, a resposta é **Textract**.

O pipeline canônico de **IDP (Intelligent Document Processing)** é: **S3 → Textract** (extrai) → **Comprehend** (classifica/detecta PII) → **A2I** (revisão humana nos casos de baixa confiança) → banco de dados. E, cada vez mais: **Textract → Bedrock**, usando o LAYOUT para produzir chunks limpos para uma Knowledge Base.

## 🎓 Pontos-chave para a prova

- Textract = extração de **texto, formulários (FORMS), tabelas (TABLES), assinaturas e layout** de documentos.
- **Analyze Expense** (faturas/recibos) e **Analyze ID** (documentos de identidade) são APIs especializadas.
- **Queries** permite perguntar diretamente ao documento, sem template.
- Modos **síncrono** e **assíncrono** (multipágina via S3 + SNS).
- **Confidence scores** habilitam **human-in-the-loop com Amazon A2I**.
- **Textract = documentos**; **Rekognition = imagens/cenas**. Não troque.
- Pipeline IDP: **Textract → Comprehend → A2I**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| OCR | Optical Character Recognition — reconhecimento de caracteres |
| FORMS | Feature que extrai pares chave-valor de formulários |
| TABLES | Feature que preserva a estrutura tabular |
| LAYOUT | Feature que identifica títulos, parágrafos e listas |
| Analyze Expense | API para faturas e recibos |
| Analyze ID | API para documentos de identidade |
| Queries | Perguntas em linguagem natural sobre o documento |
| Confidence score | Grau de confiança da extração |
| IDP | Intelligent Document Processing |

## 💡 Exemplo prático / caso de uso

Uma seguradora recebe 5 mil formulários de sinistro em PDF por dia. O **Textract** com **FORMS** e **TABLES** extrai os campos e a tabela de itens danificados; **Queries** responde "qual é o valor reclamado?" sem template; o **Comprehend** detecta e reda o **PII**; e itens com **confidence** abaixo de 90% vão para revisão humana via **A2I**. O que era digitação manual vira um pipeline automatizado com controle de qualidade — e o gargalo humano fica só onde o modelo está incerto.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
