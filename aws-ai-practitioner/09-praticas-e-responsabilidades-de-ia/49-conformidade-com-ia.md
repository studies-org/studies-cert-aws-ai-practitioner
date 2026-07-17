# 49. Conformidade com IA

> Seção: Práticas e Responsabilidades de IA · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**Conformidade (compliance)** é aderir às leis, normas e padrões aplicáveis. Sistemas de IA processam dados pessoais e tomam decisões que afetam pessoas, o que os coloca no radar de vários regimes regulatórios ao mesmo tempo.

Os **regulamentos** relevantes: **LGPD** (Brasil — Lei Geral de Proteção de Dados, com direitos de acesso, correção, eliminação e o **direito à revisão de decisões automatizadas**); **GDPR** (Europa — inclui *right to explanation* e *right to be forgotten*); **HIPAA** (saúde nos EUA); **PCI-DSS** (dados de cartão); **SOC 1/2/3** e **ISO 27001** (segurança da informação); **ISO 42001** (norma específica de **sistemas de gestão de IA**); e o **EU AI Act**, que classifica sistemas por **nível de risco** — inaceitável (proibido), alto risco (obrigações rigorosas), risco limitado (transparência) e risco mínimo.

As **ferramentas AWS de conformidade** que caem na prova: **AWS Artifact** — portal de **relatórios de conformidade** e acordos (SOC, ISO, PCI) sob demanda; **AWS Config** — avalia continuamente se os recursos estão em conformidade com regras definidas; **AWS Audit Manager** — automatiza a coleta de evidências para auditorias; **AWS CloudTrail** — registra todas as chamadas de API (a trilha de auditoria); **Amazon Macie** — descobre e classifica **PII** no S3 usando ML; **AWS Trusted Advisor** — recomendações de segurança e otimização; e **AWS Well-Architected Tool**, com um **lente de Machine Learning**.

O ponto conceitual mais importante é o **Modelo de Responsabilidade Compartilhada aplicado à conformidade**: a AWS é certificada e fornece os relatórios (via **Artifact**), mas **isso não torna sua aplicação automaticamente conforme**. Usar um serviço "HIPAA-eligible" não significa que sua solução seja HIPAA-compliant — você ainda precisa assinar o **BAA**, configurar criptografia, controlar acesso e auditar. **Você herda controles, não conformidade.**

Para IA especificamente, os requisitos recorrentes são: **rastreabilidade** da origem dos dados de treino, **documentação** do modelo (**Model Cards**), **explicabilidade** das decisões, **direito de revisão humana**, **retenção e eliminação** de dados, e **soberania de dados** (a Região onde os dados residem).

## 🎓 Pontos-chave para a prova

- **LGPD** (BR) e **GDPR** (UE) garantem direitos sobre dados e **revisão de decisões automatizadas**.
- **EU AI Act** classifica sistemas por **nível de risco**.
- **ISO 42001** é a norma de **sistemas de gestão de IA**.
- **AWS Artifact** = relatórios de conformidade; **Audit Manager** = evidências; **Config** = conformidade de recursos.
- **Amazon Macie** descobre **PII** no S3; **CloudTrail** fornece a trilha de auditoria.
- **Serviço "eligible" ≠ solução compliant** — você herda controles, não conformidade.
- Soberania de dados depende da **escolha da Região**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| LGPD | Lei Geral de Proteção de Dados (Brasil) |
| GDPR | Regulamento europeu de proteção de dados |
| HIPAA | Regulamento de dados de saúde nos EUA |
| ISO 42001 | Norma de sistemas de gestão de IA |
| EU AI Act | Regulamento europeu de IA baseado em níveis de risco |
| AWS Artifact | Portal de relatórios e acordos de conformidade |
| AWS Audit Manager | Automação da coleta de evidências de auditoria |
| Amazon Macie | Descoberta e classificação de dados sensíveis no S3 |
| BAA | Business Associate Addendum, exigido pela HIPAA |
| Soberania de dados | Exigência de que os dados residam em uma jurisdição |

## 💡 Exemplo prático / caso de uso

Uma healthtech quer usar IA sobre prontuários. Baixa os relatórios **SOC 2** e **HIPAA** no **AWS Artifact** para o time jurídico, assina o **BAA** com a AWS, usa apenas serviços **HIPAA-eligible**, criptografa tudo com **KMS**, usa o **Macie** para garantir que nenhum PHI foi parar num bucket errado, registra todo acesso via **CloudTrail** e mantém **revisão médica humana (A2I)** em qualquer sugestão diagnóstica. A certificação da AWS foi o **ponto de partida**, não a chegada — o restante do trabalho é do cliente.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
