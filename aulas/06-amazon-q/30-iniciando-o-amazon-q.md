# 30. Iniciando o Amazon Q

> Seção: Amazon Q · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Com o usuário no **IAM Identity Center** e os documentos no **S3**, o passo seguinte é criar a **Application** do Amazon Q Business. O roteiro:

**1. Criar a Application.** Console do Amazon Q Business → Create application. Defina o nome, o método de acesso (**IAM Identity Center**) e a **service role** (o console pode criá-la), que dará ao Q permissão de ler o bucket e escrever logs.

**2. Configurar o Retriever.** Escolha entre o **índice nativo do Q** (padrão, mais simples) ou o **Amazon Kendra** (se você já tem um índice Kendra ou precisa dos recursos avançados dele). Defina o número de **index units**, que dimensiona a capacidade — e o custo.

**3. Conectar a Data Source.** Adicione o conector **Amazon S3**, aponte o bucket/prefixo, informe a IAM role e defina o **sync schedule**. Rode o sync e acompanhe até o status ficar completo. Como no Bedrock KB, **sem sync não há conteúdo indexado**.

**4. Atribuir usuários (subscriptions).** Adicione o usuário criado no Identity Center à aplicação e escolha o plano: **Lite** ou **Pro**. **É neste momento que a cobrança por assinatura começa** — cada usuário atribuído gera custo mensal, use ele o serviço ou não.

**5. Configurar Admin controls.** Aqui você define se o Q pode usar **conhecimento geral do modelo** ou responder **apenas com base nos documentos indexados**. Para casos corporativos que exigem precisão, restrinja aos documentos — é a configuração que reduz alucinação. Também é onde ficam os blocked words e os tópicos restritos.

**6. Publicar a Web experience.** O Q gera uma **URL de chat** hospedada. O usuário acessa, faz login pelo Identity Center e começa a conversar. Você pode customizar título, mensagem de boas-vindas e prompts sugeridos.

Da primeira sincronização à primeira resposta útil costumam se passar alguns minutos — o tempo do sync depende do volume de documentos.

## 🎓 Pontos-chave para a prova

- Ordem: **Application → Retriever → Data source + sync → Subscriptions → Admin controls → Web experience**.
- Acesso de usuários via **IAM Identity Center**; acesso a recursos via **service role**.
- Retriever pode ser **nativo do Q** ou **Amazon Kendra**.
- **A cobrança começa ao atribuir assinaturas** (Lite/Pro), não ao usar.
- **Admin controls** decidem se o Q usa conhecimento geral ou só os documentos da empresa.
- A **Web experience** é a interface de chat pronta, sem desenvolvimento de front-end.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Application | Instância do Q Business que agrega índice, fontes e usuários |
| Retriever | Componente de recuperação (índice nativo ou Kendra) |
| Index unit | Unidade de capacidade do índice; afeta custo |
| Subscription | Atribuição de plano (Lite/Pro) a um usuário — gera cobrança |
| Admin controls | Configurações de escopo e restrições de resposta |
| Web experience | URL de chat hospedada pelo Q |
| Service role | Role usada pela aplicação para acessar S3 e demais recursos |

## 💡 Exemplo prático / caso de uso

Você cria a aplicação `q-lab`, usa o retriever nativo, conecta o bucket `q-lab-docs-<seu-nome>`, roda o sync e atribui seu usuário no plano **Lite**. Nos Admin controls, desliga o conhecimento geral do modelo — assim o assistente responde **exclusivamente** com base nos PDFs indexados e admite não saber quando a informação não está lá. Isso é preferível a um assistente que "preenche as lacunas" inventando: em contexto corporativo, "não encontrei" é uma resposta melhor que uma alucinação confiante.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
