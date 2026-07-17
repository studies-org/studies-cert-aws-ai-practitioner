# 32. Removendo o Amazon Q Business

> Seção: Amazon Q · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Esta aula existe por um motivo bem concreto: **o Amazon Q Business cobra por assinatura de usuário/mês e continua cobrando mesmo sem uso nenhum**. Deixar o laboratório de pé "para ver depois" gera fatura todo mês. Diferente de serviços por consumo, aqui não existe "custo zero se eu não usar".

A **ordem de remoção** importa, porque há dependências entre os recursos:

**1. Remover as subscriptions.** Vá em Users and groups e **remova as assinaturas** dos usuários. Este é o passo que efetivamente **estanca a cobrança principal** — faça-o primeiro.

**2. Deletar a Application.** Isso remove junto a Web experience, o retriever/índice e os conectores de data source associados. Confirme a exclusão.

**3. Limpar os recursos relacionados.** Delete o **bucket S3** do laboratório (esvazie antes — não é possível deletar bucket com objetos). Se você criou um índice **Kendra** separado, delete-o também: **Kendra é caro e cobra por hora de índice provisionado**, sendo um dos piores esquecimentos possíveis. Remova as **IAM roles** e políticas criadas para o laboratório.

**4. Decidir sobre o IAM Identity Center.** Você pode manter o usuário para outros laboratórios — o Identity Center em si **não gera custo**. Só remova se não for reutilizar.

**5. Verificar.** Confira no **Cost Explorer** nos dias seguintes se ainda há lançamentos para Amazon Q ou Kendra. Se você configurou o **AWS Budgets** (aula 4), o alerta serve como rede de segurança.

A regra geral que vale para todo o curso: **serviços com capacidade provisionada continuam cobrando ociosos**. Os três campeões nesse quesito são **Amazon Q Business** (assinatura), **Amazon Kendra** (índice por hora), **OpenSearch Serverless** (OCUs da Knowledge Base) — e, quando você chegar lá, os **endpoints do SageMaker**.

## 🎓 Pontos-chave para a prova

- Q Business cobra **por assinatura de usuário/mês**, independentemente do uso.
- Ordem: **remover subscriptions → deletar Application → limpar S3/Kendra/roles**.
- **Kendra** e **OpenSearch Serverless** cobram por capacidade provisionada, mesmo ociosos.
- **Endpoints do SageMaker** também cobram por hora enquanto existirem.
- Sempre valide a limpeza no **Cost Explorer** e proteja-se com **AWS Budgets**.
- Buckets S3 precisam ser **esvaziados antes de excluídos**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Subscription | Assinatura de usuário que gera cobrança mensal |
| Application | Recurso raiz do Q Business; sua exclusão remove os componentes filhos |
| Capacidade provisionada | Recurso reservado que cobra independentemente do uso |
| Cost Explorer | Ferramenta de análise dos gastos por serviço e período |
| AWS Budgets | Orçamentos e alertas de custo |
| Orphaned resource | Recurso esquecido que continua gerando custo |

## 💡 Exemplo prático / caso de uso

Um estudante conclui o laboratório, deleta a aplicação do Q e considera o assunto encerrado. Semanas depois recebe uma fatura inesperada: **o índice do Kendra** que ele criou separadamente continuou provisionado, cobrando por hora, 24/7. A lição — e é uma das mais práticas do curso — é que **deletar o recurso principal nem sempre remove a infraestrutura subjacente**. Sempre feche o ciclo verificando o **Cost Explorer**.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
