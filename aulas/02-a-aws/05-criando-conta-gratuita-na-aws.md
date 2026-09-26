# 5. Criando Conta Gratuita na AWS

> Seção: A AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Criar uma conta AWS exige um **e-mail válido**, um **número de telefone** e um **cartão de crédito internacional** (usado apenas para verificação de identidade — há uma cobrança simbólica de cerca de US$ 1 que é estornada). Você também escolhe um plano de suporte: para estudo, selecione o **Basic Support**, que é gratuito.

O e-mail usado no cadastro se torna o **usuário root** da conta. O root é uma identidade especial: ele tem acesso irrestrito a tudo, incluindo ações que nenhuma outra identidade pode fazer (fechar a conta, alterar o plano de suporte, mudar o e-mail de faturamento). Por isso a **regra de ouro** da AWS é: **não use o root no dia a dia**.

As boas práticas imediatamente após criar a conta são: **ativar MFA (autenticação multifator) no root**, criar um usuário administrativo separado no **IAM Identity Center** (ou no IAM) para o uso cotidiano, **não criar access keys para o root**, e guardar as credenciais do root em local seguro. Essas práticas caem no Domínio 5 (Segurança e Governança) e reaparecem nas aulas 53 e 54.

Vale também configurar o idioma e a Região padrão do console. Lembre-se: a maioria dos serviços é **regional**, então recursos criados em `us-east-1` não aparecem se você estiver visualizando `sa-east-1`. Isso confunde muita gente em laboratório — "sumiu meu bucket" quase sempre é a Região errada no seletor. (O S3 tem namespace global de nomes, mas os buckets residem em uma Região específica.)

## 🎓 Pontos-chave para a prova

- O **usuário root** tem acesso irrestrito e deve ser usado apenas para tarefas exclusivas dele.
- **Ative MFA no root imediatamente** e não gere access keys para ele.
- Crie um usuário/identidade administrativa separada para o uso diário (princípio do menor privilégio).
- **Basic Support** é gratuito; Developer, Business e Enterprise são pagos.
- A maioria dos serviços é **regional** — confira o seletor de Região ao procurar recursos.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Usuário root | Identidade criada com a conta; acesso total e irrestrito |
| MFA | Multi-Factor Authentication — segundo fator além da senha |
| IAM Identity Center | Serviço recomendado para gerenciar identidades e acessos humanos |
| Basic Support | Plano de suporte gratuito, padrão de novas contas |
| Menor privilégio | Conceder apenas as permissões estritamente necessárias |
| Região padrão | Região selecionada no console; determina onde os recursos são criados |

## 💡 Exemplo prático / caso de uso

Você cria a conta, ativa MFA no root com um app autenticador, faz logout do root e passa a acessar tudo por um usuário `estudos-aip` com a policy `AdministratorAccess`. Se esse usuário for comprometido, você ainda pode entrar como root e revogar o acesso — o oposto (root comprometido) não teria saída equivalente.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
