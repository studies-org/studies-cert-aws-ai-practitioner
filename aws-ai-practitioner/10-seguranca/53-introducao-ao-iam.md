# 53. Introdução ao IAM

> Seção: Segurança · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **AWS IAM (Identity and Access Management)** controla **quem** pode fazer **o quê** em **quais recursos**. É um serviço **global** (não regional) e **gratuito**. Toda arquitetura de IA na AWS depende dele: quem pode invocar um modelo no Bedrock, qual role a Knowledge Base usa para ler o S3, o que um Agent pode executar.

Os **componentes**: **User** (identidade de pessoa ou aplicação, com credenciais de longo prazo); **Group** (coleção de usuários — as permissões vão para o grupo, não para cada pessoa); **Role** (identidade **assumível temporariamente**, sem credenciais fixas, usada por serviços AWS, aplicações em EC2/Lambda e acesso federado); e **Policy** (documento JSON que concede ou nega).

A **estrutura de uma policy** cai na prova: **Effect** (`Allow` ou `Deny`), **Action** (`bedrock:InvokeModel`), **Resource** (o ARN alvo), **Condition** (restrições contextuais, como IP de origem ou exigência de MFA) e **Principal** (em policies baseadas em recurso).

A **lógica de avaliação** é a regra de ouro: **deny explícito > allow explícito > deny implícito (padrão)**. Ou seja, tudo é negado por padrão; um `Allow` libera; e um `Deny` explícito **sempre vence**, mesmo havendo um Allow em outra policy. Essa precedência é questão garantida em algum momento.

Há dois tipos de policy: **identity-based** (anexada a user/group/role) e **resource-based** (anexada ao recurso, como uma bucket policy, e que define o `Principal`).

As **boas práticas** — que são o Domínio 5 em forma condensada: **menor privilégio**; **usar roles em vez de access keys**; **MFA** habilitado; **não usar o root**; **atribuir permissões via grupos**; **rotacionar credenciais**; e usar **IAM Access Analyzer** para encontrar acessos externos indesejados e refinar permissões com base no uso real.

Aplicado a IA: a policy de um cientista de dados pode permitir `bedrock:InvokeModel` apenas em modelos específicos; a **service role** de uma Knowledge Base recebe `s3:GetObject` apenas no prefixo dos documentos; e um **Agent** recebe apenas as ações que precisa executar — nada além.

## 🎓 Pontos-chave para a prova

- IAM é **global** e **gratuito**; controla quem faz o quê em quais recursos.
- **User / Group / Role / Policy** — role usa **credenciais temporárias** e é a opção preferida.
- Policy = **Effect, Action, Resource, Condition** (+ Principal em resource-based).
- **Deny explícito > Allow explícito > Deny implícito** (tudo negado por padrão).
- Boas práticas: **menor privilégio, MFA, roles em vez de keys, não usar root, grupos**.
- **IAM Access Analyzer** identifica acesso externo e ajuda a refinar permissões.
- Serviços de IA acessam recursos via **service roles**, não com credenciais de usuário.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| IAM | Identity and Access Management |
| Role | Identidade assumível com credenciais temporárias |
| Policy | Documento JSON que define permissões |
| ARN | Amazon Resource Name — identificador único do recurso |
| Effect | `Allow` ou `Deny` |
| Condition | Restrição contextual da permissão |
| Identity-based policy | Policy anexada a usuário, grupo ou role |
| Resource-based policy | Policy anexada ao recurso, com Principal explícito |
| Access Analyzer | Ferramenta que detecta acesso externo e refina permissões |
| Menor privilégio | Conceder apenas o estritamente necessário |

## 💡 Exemplo prático / caso de uso

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": ["bedrock:InvokeModel"],
    "Resource": "arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-*"
  }]
}
```

Essa policy permite invocar **apenas** os modelos Claude, **apenas** em `us-east-1` — não `bedrock:*` em `*`. Se outra policy anexada à mesma identidade tiver um **Deny explícito** para `bedrock:InvokeModel`, o Deny vence e a chamada falha, independentemente deste Allow.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
