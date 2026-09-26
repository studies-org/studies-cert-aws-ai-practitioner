# 54. Criando Usuários e Grupos no IAM Identity Center

> Seção: Segurança · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **IAM Identity Center** (antigo AWS SSO) é o serviço **recomendado pela AWS para acesso humano**. Enquanto o IAM tradicional gerencia identidades **dentro de uma conta**, o Identity Center gerencia identidades **entre várias contas** de uma organização, com **login único (SSO)** e **credenciais temporárias**.

As **vantagens** sobre IAM users: um único login para todas as contas AWS; **sem access keys de longo prazo** (que vazam em repositórios Git e são a origem de tantos incidentes); **federação** com o provedor de identidade corporativo (Okta, Entra ID, Ping) — o funcionário usa a mesma credencial de sempre e, ao ser desligado, perde o acesso à AWS automaticamente; e **MFA centralizado**.

Os **conceitos**: **Identity source** (onde ficam as identidades — o diretório interno do Identity Center, o Active Directory ou um IdP externo via SAML/SCIM); **Users e Groups**; **Permission set** (uma coleção de policies que define o nível de acesso — na prática, um template de role provisionado nas contas); e **Account assignment** (a ligação usuário/grupo + permission set + conta).

O fluxo de criação: habilitar o Identity Center (que exige o **AWS Organizations**) → escolher a identity source → criar **grupos** (ex.: `Admins`, `Desenvolvedores`, `Q-Users`) → criar **usuários** e atribuí-los aos grupos → criar **permission sets** → fazer o **account assignment** → o usuário acessa o **portal AWS access** com sua URL própria e escolhe conta/papel.

A relação com esta trilha de estudos: o **Amazon Q Business exige o Identity Center** para autenticar usuários finais e aplicar o filtro de permissões por documento. Sem ele, o Q não sabe **quem** está perguntando — e todo o modelo de ACL-aware retrieval desaba.

A **melhor prática de permissões** se repete: atribua **permission sets a grupos**, nunca a usuários individuais. Quando alguém muda de time, você move a pessoa de grupo e pronto — em vez de auditar dezenas de permissões avulsas.

## 🎓 Pontos-chave para a prova

- **IAM Identity Center é o recomendado** para acesso humano; IAM users são legado.
- Oferece **SSO entre contas**, **credenciais temporárias** e **federação com IdP externo**.
- Requer **AWS Organizations**.
- **Permission set** = conjunto de policies provisionado como role nas contas.
- Atribua permission sets a **grupos**, não a usuários individuais.
- **Amazon Q Business exige o Identity Center** para autenticar usuários finais.
- Federação permite **revogar o acesso à AWS ao desligar** o funcionário no IdP.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| IAM Identity Center | Serviço de identidade centralizada e SSO (antigo AWS SSO) |
| Identity source | Origem das identidades (interna, AD ou IdP externo) |
| Permission set | Conjunto de permissões atribuível a grupos em contas |
| Account assignment | Ligação entre usuário/grupo, permission set e conta |
| SSO | Single Sign-On — login único |
| SAML / SCIM | Protocolos de federação e provisionamento de identidades |
| AWS Organizations | Serviço de gestão de múltiplas contas AWS |
| Portal AWS access | Portal onde o usuário escolhe conta e papel |

## 💡 Exemplo prático / caso de uso

Para o laboratório do Amazon Q Business, você habilita o **Identity Center**, cria o grupo `q-users`, adiciona o usuário `aluno` e o atribui à aplicação do Q. Quando ele faz login no portal e abre o chat, **o Q sabe exatamente quem ele é** e filtra os documentos pelas ACLs correspondentes. Em uma empresa real, esse grupo viria sincronizado do **Entra ID** via SCIM: entrou no grupo no AD, ganhou acesso ao Q; saiu da empresa, perdeu o acesso na mesma hora, sem ninguém precisar lembrar de revogar nada.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
