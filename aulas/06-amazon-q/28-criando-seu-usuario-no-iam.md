# 28. Criando seu Usuário no IAM

> Seção: Amazon Q · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Antes de subir o Amazon Q Business, é preciso ter **usuários** para acessá-lo. Aqui aparece uma distinção que a prova cobra: **IAM users** versus **IAM Identity Center users**.

O **IAM tradicional** gerencia identidades e permissões dentro de uma conta. Um **IAM user** tem credenciais de longo prazo (senha para o console, access keys para a API) e recebe permissões via **policies**, diretamente ou através de **grupos**. É o modelo clássico — e hoje a AWS o considera **legado para identidades humanas**.

O **IAM Identity Center** (antigo AWS SSO) é o serviço **recomendado** para acesso humano. Ele centraliza usuários e grupos, permite federação com um provedor de identidade externo (Okta, Entra ID), oferece **login único (SSO)** para múltiplas contas e usa **credenciais temporárias** em vez de access keys permanentes. **O Amazon Q Business exige o IAM Identity Center** — ele não trabalha com IAM users comuns, justamente porque precisa da noção de identidade de usuário final para filtrar resultados por permissão.

Os conceitos de IAM que você deve dominar: **User** (identidade de pessoa), **Group** (coleção de usuários — permissões são atribuídas ao grupo, não um a um), **Role** (identidade assumível temporariamente, sem credenciais fixas — usada por serviços e por acesso federado) e **Policy** (documento JSON que define Effect, Action, Resource e Condition).

As boas práticas, que reaparecem no Domínio 5: **menor privilégio** (conceda só o necessário), **atribua permissões via grupos**, **use roles em vez de access keys** sempre que possível, **ative MFA**, e **nunca use o root** no dia a dia.

## 🎓 Pontos-chave para a prova

- **IAM Identity Center é o recomendado** para identidades humanas; IAM users são legado.
- **Amazon Q Business exige IAM Identity Center** para autenticar usuários finais.
- **Group** agrupa usuários; permissões devem ser atribuídas ao grupo.
- **Role** = identidade assumível com **credenciais temporárias**; preferível a access keys.
- **Policy** = JSON com **Effect, Action, Resource, Condition**.
- Boas práticas: **menor privilégio, MFA, não usar root, evitar credenciais de longo prazo**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| IAM User | Identidade com credenciais de longo prazo dentro da conta |
| IAM Group | Coleção de usuários que compartilham permissões |
| IAM Role | Identidade assumível temporariamente, sem credenciais fixas |
| IAM Policy | Documento JSON que concede ou nega permissões |
| IAM Identity Center | Serviço de gestão centralizada de identidades e SSO |
| Federação | Uso de um IdP externo para autenticar na AWS |
| Credencial temporária | Credencial de curta duração emitida ao assumir uma role |
| Menor privilégio | Conceder apenas as permissões estritamente necessárias |

## 💡 Exemplo prático / caso de uso

Para o laboratório do Q Business você habilita o **IAM Identity Center**, cria o usuário `aluno` e o grupo `q-users`, atribui o usuário ao grupo e define a senha. Esse usuário será o assinante do Q. Repare no contraste: a **aplicação Q** usa uma **service role** (uma *role*, não um usuário) para ler o bucket S3, enquanto o **acesso humano** vem do Identity Center. Serviço usa role; pessoa usa identidade federada — esse é o padrão que a prova espera.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
