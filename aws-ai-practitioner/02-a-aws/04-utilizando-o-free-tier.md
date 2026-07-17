# 4. Utilizando o Free Tier

> Seção: A AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **AWS Free Tier** é a camada gratuita que permite experimentar serviços sem custo dentro de limites definidos. Ele tem **três modalidades** e entender a diferença evita surpresas na fatura.

**Free Trials** (testes gratuitos): oferta de curta duração que começa quando você ativa o serviço — por exemplo, um período de avaliação do Amazon SageMaker ou do Amazon Q Business. **12 Months Free** (12 meses gratuitos): benefícios válidos por 12 meses a partir da criação da conta, como 750 horas/mês de EC2 `t2.micro`/`t3.micro` e 5 GB no S3 Standard. **Always Free** (sempre gratuito): limites permanentes que nunca expiram, como 1 milhão de requisições/mês no AWS Lambda e 25 GB no DynamoDB.

Um ponto que pega muita gente: **serviços de IA Generativa em geral NÃO estão no Free Tier**. O **Amazon Bedrock cobra por token** (entrada e saída) desde a primeira chamada. Serviços como **Amazon Comprehend, Translate, Polly, Transcribe, Rekognition e Textract** têm cotas gratuitas nos primeiros 12 meses, mas o Bedrock não segue esse padrão. Ou seja: fazer laboratório de Bedrock custa dinheiro — geralmente centavos, mas custa.

Para se proteger, use **AWS Budgets** para criar um orçamento com alerta por e-mail (ex.: avisar ao atingir US$ 5), acompanhe o **AWS Cost Explorer** para visualizar gastos por serviço, e **sempre remova recursos** após os laboratórios. O caso mais perigoso do curso é o **Amazon Q Business**, que cobra por assinatura de usuário mensal e continua cobrando mesmo ocioso — por isso existe uma aula inteira dedicada a removê-lo.

## 🎓 Pontos-chave para a prova

- Free Tier tem **3 tipos**: Free Trials, 12 Months Free e Always Free.
- **Bedrock não é Free Tier** — cobrança por token desde a primeira invocação.
- Serviços de IA "clássicos" (Comprehend, Polly, Translate, Rekognition, Textract) têm cota gratuita nos **primeiros 12 meses**.
- **AWS Budgets** cria alertas de custo; **Cost Explorer** analisa e visualiza o gasto.
- Recursos ociosos continuam cobrando (ex.: Amazon Q Business, endpoints do SageMaker).

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Free Trials | Teste gratuito de curta duração iniciado ao ativar o serviço |
| 12 Months Free | Benefícios gratuitos nos 12 meses após criar a conta |
| Always Free | Cotas gratuitas permanentes, sem expiração |
| AWS Budgets | Serviço de definição de orçamentos e alertas de custo |
| Cost Explorer | Ferramenta de visualização e análise de gastos |
| Billing Alarm | Alarme no CloudWatch disparado ao ultrapassar um valor de fatura |

## 💡 Exemplo prático / caso de uso

Antes de iniciar os laboratórios do Bedrock, você cria no **AWS Budgets** um orçamento mensal de custo de US$ 10 com alertas em 50%, 80% e 100%, notificando seu e-mail. Assim, se um endpoint de SageMaker ficar esquecido rodando 24/7, você recebe o aviso em vez de descobrir no fim do mês.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
