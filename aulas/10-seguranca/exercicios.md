# Exercícios — 10. Segurança

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_

## Questões

### 1. Uma identidade tem uma policy com Allow para `bedrock:InvokeModel` e outra com Deny explícito para a mesma ação. Qual é o resultado?
- A) O Allow prevalece, pois foi anexado primeiro
- B) O Deny explícito prevalece e a ação é negada
- C) Ocorre um erro de conflito de policies
- D) A ação é permitida com aviso no CloudTrail

### 2. Qual é a forma recomendada de uma função Lambda acessar um bucket S3?
- A) Armazenar access keys de um IAM user nas variáveis de ambiente
- B) Assumir uma IAM role com credenciais temporárias e menor privilégio
- C) Usar as credenciais do usuário root
- D) Tornar o bucket público

### 3. Qual serviço é exigido pelo Amazon Q Business para autenticar usuários finais?
- A) IAM users com access keys
- B) IAM Identity Center
- C) AWS Directory Service exclusivamente
- D) Amazon Cognito

### 4. Qual é a melhor prática para atribuir permissões a 50 desenvolvedores com o mesmo nível de acesso?
- A) Anexar a policy individualmente a cada usuário
- B) Atribuir a permissão a um grupo e adicionar os usuários ao grupo
- C) Compartilhar um único IAM user entre todos
- D) Dar AdministratorAccess a todos para evitar bloqueios

### 5. Quais elementos compõem uma IAM policy?
- A) Region, AZ, Endpoint e Protocol
- B) Effect, Action, Resource e Condition
- C) Intent, Slot, Utterance e Fulfillment
- D) Agent, Ambiente, Ação e Recompensa

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — A lógica de avaliação do IAM é: **deny explícito > allow explícito > deny implícito**. Um `Deny` explícito **sempre vence**, independentemente de quantos Allows existam ou da ordem de anexação.

2. **B** — Serviços devem usar **IAM roles com credenciais temporárias** e menor privilégio. Access keys de longo prazo em variáveis de ambiente são um antipadrão clássico — elas vazam em repositórios e não rotacionam sozinhas.

3. **B** — O **IAM Identity Center** é obrigatório para o Q Business, porque o serviço precisa da identidade do usuário final para aplicar o filtro de permissões (ACL-aware retrieval) nos documentos indexados.

4. **B** — Permissões devem ser atribuídas a **grupos**. Isso torna a gestão escalável e auditável: mudou de time, muda de grupo. Anexar policies individualmente vira caos de manutenção, e `AdministratorAccess` para todos viola frontalmente o menor privilégio.

5. **B** — Uma policy IAM tem **Effect** (Allow/Deny), **Action** (a operação), **Resource** (o ARN alvo) e **Condition** (restrições contextuais). Policies baseadas em recurso também trazem **Principal**. A letra C descreve componentes do Amazon Lex e a D, de aprendizado por reforço.

</details>
