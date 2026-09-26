# 45. Amazon Augmented AI

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Augmented AI (A2I)** implementa **human-in-the-loop**: fluxos em que **pessoas revisam as previsões de um modelo de ML**. É a resposta canônica da prova sempre que o cenário envolver "revisão humana", "decisões de alto risco", "baixa confiança do modelo" ou "auditoria de qualidade".

A ideia central é que **nem toda previsão precisa de revisão** — só as que importam. O A2I permite definir **condições de ativação**: quando o **confidence score** fica abaixo de um limiar (ex.: <90%), quando a decisão tem alto impacto, ou por **amostragem aleatória** (ex.: revisar 5% de tudo para auditoria contínua, mesmo com alta confiança).

Os componentes: **Human Review Workflow (flow definition)** — define quando acionar humanos, quem revisa e onde gravar o resultado; **Worker task template** — a interface que o revisor vê; **Human loop** — uma instância concreta de revisão; e **Workforce** — quem revisa: **private** (sua equipe, obrigatória para dados sensíveis), **vendor** (fornecedores aprovados) ou **public** (**MTurk**).

O A2I tem **integração nativa** com o **Amazon Textract** (revisão de extração de formulários) e o **Amazon Rekognition** (moderação de conteúdo), e suporta **modelos customizados** do SageMaker ou qualquer modelo próprio via API.

O valor do A2I vai além de corrigir erros pontuais: as decisões humanas viram **dados rotulados de alta qualidade**, que podem realimentar o treino e melhorar o modelo continuamente — fechando o ciclo entre operação e melhoria.

Este serviço é a ponte com a seção 09: **human-in-the-loop é um pilar de IA responsável**. Sistemas de alto risco — crédito, saúde, contratação, identificação de pessoas — não devem decidir sozinhos. O A2I é como isso se materializa em arquitetura na AWS.

## 🎓 Pontos-chave para a prova

- A2I = **human-in-the-loop**: revisão humana de previsões de ML.
- Aciona por **baixo confidence score**, **alto impacto** ou **amostragem aleatória**.
- Componentes: **flow definition, worker task template, human loop, workforce**.
- Workforce: **private** (dados sensíveis), **vendor** ou **public (MTurk)**.
- Integração nativa com **Textract** e **Rekognition**; suporta modelos customizados.
- Revisões viram **dados rotulados** para melhoria contínua.
- É a materialização de **IA responsável** em decisões de alto risco.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Human-in-the-loop | Inclusão de revisão humana no fluxo de decisão do modelo |
| Human Review Workflow | Definição de quando, quem e como revisar |
| Human loop | Instância concreta de uma revisão |
| Worker task template | Interface apresentada ao revisor |
| Confidence threshold | Limiar de confiança que dispara a revisão |
| Random sampling | Revisão de uma amostra aleatória para auditoria |
| Private workforce | Equipe interna, exigida para dados sensíveis |

## 💡 Exemplo prático / caso de uso

Um banco automatiza a abertura de contas com **Textract** extraindo dados de documentos. Configura o **A2I** para que qualquer campo com **confiança abaixo de 95%** vá para revisão de um analista, e adiciona **amostragem aleatória de 2%** dos casos de alta confiança como auditoria contínua — para detectar se o modelo começou a errar com confiança alta, que é o pior tipo de falha. Como são dados pessoais, a workforce é **private** (funcionários do banco), jamais MTurk. As correções dos analistas viram dataset para refinar o modelo.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
