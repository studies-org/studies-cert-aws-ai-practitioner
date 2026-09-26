# 3. O Que é a Amazon AWS

> Seção: A AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

A **Amazon Web Services (AWS)** é a plataforma de computação em nuvem da Amazon, lançada em 2006 e hoje líder global de mercado. Em vez de comprar e manter servidores físicos, você aluga capacidade computacional sob demanda e paga apenas pelo que consome (*pay-as-you-go*). Isso transforma um custo de capital (CapEx) em custo operacional (OpEx).

As vantagens clássicas da nuvem — que a AWS chama de *value proposition* — são: **agilidade** (provisionar um servidor em minutos, não meses), **elasticidade** (escalar para cima e para baixo conforme a demanda), **economia de escala** (a AWS compra hardware em volume e repassa o preço), **alcance global** (implantar em outro continente com poucos cliques) e **foco no negócio** (parar de gerenciar datacenter e cuidar do que diferencia sua empresa).

A infraestrutura é organizada geograficamente. Uma **Região** (ex.: `us-east-1`, `sa-east-1`) é uma área geográfica isolada. Cada Região contém múltiplas **Zonas de Disponibilidade (AZs)** — datacenters fisicamente separados, com energia e rede independentes, ligados por links de baixa latência. Além disso existem **Edge Locations** (pontos de presença do CloudFront, mais de 400 no mundo) usados para cache e entrega de conteúdo próximo do usuário.

Para o exame AIF-C01, o ponto crítico sobre Regiões é que **nem todo serviço de IA está disponível em todas as Regiões**, e **nem todo Foundation Model do Bedrock está em todas as Regiões**. Isso frequentemente aparece como distrator ou como parte de um cenário de latência/soberania de dados.

Outro conceito essencial é o **Modelo de Responsabilidade Compartilhada** (*Shared Responsibility Model*): a AWS é responsável pela segurança **DA** nuvem (hardware, rede física, hipervisor, infraestrutura dos serviços gerenciados); o cliente é responsável pela segurança **NA** nuvem (seus dados, configuração de IAM, criptografia, controle de acesso). Em serviços de IA isso significa: a AWS protege o Bedrock; você protege seus prompts, seus dados de fine-tuning e quem pode invocar o modelo.

## 🎓 Pontos-chave para a prova

- **Região** = área geográfica; **AZ** = datacenter isolado dentro da Região; **Edge Location** = PoP de cache/CDN.
- Disponibilidade de serviços e de **Foundation Models varia por Região** — verifique antes de arquitetar.
- **Responsabilidade Compartilhada**: AWS = segurança **da** nuvem; cliente = segurança **na** nuvem.
- Modelo de cobrança **pay-as-you-go**, sem compromisso de longo prazo obrigatório.
- Escolha de Região é guiada por: latência, custo, conformidade/soberania de dados e disponibilidade do serviço.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Região (Region) | Área geográfica isolada com múltiplas AZs (ex.: `sa-east-1` = São Paulo) |
| Zona de Disponibilidade (AZ) | Um ou mais datacenters isolados dentro de uma Região |
| Edge Location | Ponto de presença global para cache/entrega (CloudFront) |
| Shared Responsibility Model | Divisão de responsabilidade de segurança entre AWS e cliente |
| Elasticidade | Capacidade de aumentar/reduzir recursos conforme a demanda |
| CapEx → OpEx | Troca de investimento em hardware por despesa operacional variável |

## 💡 Exemplo prático / caso de uso

Um banco brasileiro precisa usar IA Generativa mantendo os dados no país por exigência regulatória. Ele avalia a Região `sa-east-1` (São Paulo) e descobre que o modelo desejado ainda não está disponível lá. As opções são: usar um modelo alternativo disponível em `sa-east-1`, ou usar `us-east-1` e obter aprovação jurídica para transferência internacional. Essa decisão — **disponibilidade regional versus conformidade** — é exatamente o tipo de trade-off cobrado na prova.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
