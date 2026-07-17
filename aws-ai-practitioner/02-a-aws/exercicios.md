# Exercícios — 02. A AWS

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_, 6-_, 7-_

## Questões

### 1. Qual é a diferença entre uma Região e uma Zona de Disponibilidade?
- A) Região é um datacenter; AZ é um conjunto de Regiões
- B) Região é uma área geográfica que contém múltiplas AZs isoladas fisicamente
- C) São sinônimos, usados de forma intercambiável
- D) AZ é um ponto de cache de conteúdo global

### 2. Segundo o Modelo de Responsabilidade Compartilhada, quem é responsável por definir quem pode invocar um Foundation Model no Amazon Bedrock?
- A) A AWS, pois o Bedrock é totalmente gerenciado
- B) O cliente, via políticas de IAM
- C) O fornecedor do modelo (ex.: Anthropic, Meta)
- D) Ninguém — o acesso é público por padrão

### 3. Uma empresa quer testar o Amazon Bedrock sem gerar custos usando o Free Tier. O que acontece?
- A) O Bedrock está no Always Free, com 1 milhão de tokens/mês gratuitos
- B) O Bedrock está incluso nos 12 meses gratuitos
- C) O Bedrock não faz parte do Free Tier e cobra por token desde a primeira chamada
- D) O Bedrock é gratuito, mas o modelo cobra à parte

### 4. Qual das ações a seguir só pode ser executada pelo usuário root?
- A) Criar um bucket S3
- B) Habilitar um Foundation Model no Bedrock
- C) Fechar a conta AWS
- D) Criar um usuário no IAM

### 5. Quais são as três modalidades do AWS Free Tier?
- A) Trial, Standard e Premium
- B) Free Trials, 12 Months Free e Always Free
- C) Basic, Developer e Business
- D) Spot, Reserved e On-Demand

### 6. Um arquiteto precisa implantar uma solução de IA Generativa e descobre que o modelo desejado não existe na Região exigida por conformidade. Qual é a implicação correta?
- A) Nenhuma — os modelos do Bedrock são globais e replicados automaticamente
- B) A disponibilidade de Foundation Models varia por Região e precisa ser verificada na arquitetura
- C) Basta habilitar o modelo em qualquer Região que ele passa a responder em todas
- D) Modelos só existem em `us-east-1`, sem exceção

### 7. Qual serviço permite criar um alerta por e-mail quando o gasto mensal atingir US$ 5?
- A) AWS Budgets
- B) AWS Config
- C) Amazon Inspector
- D) AWS Artifact

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — Uma **Região** é uma área geográfica isolada (ex.: `sa-east-1`) que contém **múltiplas AZs**, cada uma com um ou mais datacenters de energia e rede independentes. Edge Locations (letra D) são os PoPs do CloudFront.

2. **B** — Controle de acesso é responsabilidade **do cliente** ("segurança **na** nuvem"). A AWS garante a segurança da infraestrutura do Bedrock ("segurança **da** nuvem"), mas quem pode chamar `InvokeModel` é definido por políticas IAM que você escreve.

3. **C** — O **Amazon Bedrock não está no Free Tier**. A cobrança é por token de entrada e saída (ou por throughput provisionado) desde a primeira invocação. Serviços de IA clássicos como Comprehend e Polly é que têm cota gratuita nos 12 meses.

4. **C** — **Fechar a conta** é uma ação exclusiva do root, assim como alterar o plano de suporte e mudar o e-mail de faturamento. As demais ações podem ser delegadas via IAM.

5. **B** — **Free Trials** (curta duração ao ativar o serviço), **12 Months Free** (12 meses após criar a conta) e **Always Free** (permanente). A letra C lista planos de suporte; a D lista modelos de compra do EC2.

6. **B** — A **disponibilidade de modelos é regional**. É preciso escolher entre um modelo alternativo disponível na Região exigida ou reavaliar o requisito de conformidade. Não há replicação automática entre Regiões.

7. **A** — **AWS Budgets** define orçamentos e dispara alertas. Cost Explorer visualiza gastos (mas não é a ferramenta primária de alerta), Config audita configurações, Inspector faz varredura de vulnerabilidades e Artifact fornece relatórios de conformidade.

</details>
