# 44. Amazon Mechanical Turk

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Mechanical Turk (MTurk)** é um **marketplace de crowdsourcing**: uma força de trabalho humana global e sob demanda para tarefas que computadores fazem mal e pessoas fazem bem. O nome vem do "Turco Mecânico" do século XVIII — um autômato jogador de xadrez que, na verdade, escondia uma pessoa dentro. A metáfora é precisa: é **inteligência artificial artificial**.

O vocabulário do serviço: **Requester** (você, que publica o trabalho), **Worker** (a pessoa que executa), **HIT — Human Intelligence Task** (a unidade de trabalho: "rotule esta imagem"), **Assignment** (a execução de um HIT por um worker específico), **Reward** (o pagamento por HIT) e **Qualification** (requisitos que filtram quem pode executar — idioma, taxa de aprovação, testes).

Os casos de uso típicos em IA são: **rotulagem de dados de treino** (a matéria-prima do aprendizado supervisionado), moderação de conteúdo, transcrição de áudio difícil, pesquisas, validação de dados e **avaliação humana de saídas de modelos**.

A relação com outros serviços é o que a prova cobra. O **SageMaker Ground Truth** pode usar o MTurk como **força de trabalho pública** — as alternativas são a *private workforce* (sua própria equipe, para dados confidenciais) e a *vendor workforce* (fornecedores aprovados). O **Amazon A2I** também pode usar MTurk para os fluxos de revisão humana. Ou seja: o MTurk é frequentemente a **camada de mão de obra** por trás desses serviços, não algo que você usa isolado.

Um ponto de **IA responsável** e de segurança: como os workers são o **público geral**, **nunca envie dados confidenciais, PII ou material sensível ao MTurk**. Para esses casos, use a *private workforce*. Além disso, há considerações éticas legítimas sobre remuneração justa e condições de trabalho no crowdsourcing — tema que dialoga diretamente com a seção 09.

## 🎓 Pontos-chave para a prova

- MTurk = **crowdsourcing de tarefas humanas** sob demanda.
- **HIT** é a unidade de trabalho; **Workers** executam, **Requesters** publicam.
- **Qualifications** filtram quem pode executar a tarefa.
- Usado para **rotular dados de treino**, moderar conteúdo e avaliar saídas de modelo.
- É a **força de trabalho pública** do **SageMaker Ground Truth** e do **Amazon A2I**.
- **Nunca envie dados confidenciais** — use a **private workforce** nesses casos.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Crowdsourcing | Distribuição de tarefas a uma multidão de trabalhadores |
| HIT | Human Intelligence Task — unidade de trabalho |
| Requester | Quem publica as tarefas |
| Worker | Quem executa as tarefas |
| Assignment | Execução de um HIT por um worker |
| Qualification | Critério que restringe quem pode executar o HIT |
| Public workforce | Força de trabalho aberta (MTurk) |
| Private workforce | Sua própria equipe, para dados sensíveis |

## 💡 Exemplo prático / caso de uso

Uma startup precisa de 100 mil imagens rotuladas para treinar um classificador. Publica **HITs** no **MTurk** ("esta foto contém um gato?"), com **qualification** exigindo taxa de aprovação acima de 95%, e usa **consenso de 3 workers** por imagem para reduzir erro. Custo: centavos por rótulo, entregue em dias. Já um hospital que precisa rotular imagens médicas **não pode** usar MTurk — os dados são protegidos por regulação. Ele usa o **Ground Truth com private workforce**, composta por seus próprios radiologistas.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
