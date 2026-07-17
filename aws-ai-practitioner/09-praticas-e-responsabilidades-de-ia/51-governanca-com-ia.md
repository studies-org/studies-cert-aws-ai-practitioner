# 51. Governança com IA

> Seção: Práticas e Responsabilidades de IA · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

**Governança de IA** é o conjunto de **políticas, papéis e processos** que garante que a IA seja usada de forma responsável, controlada e alinhada aos objetivos e ao apetite de risco da organização. Se IA responsável é o "o quê", governança é o "como garantir que aconteça sempre, e não só quando alguém lembra".

Os **componentes** de um programa de governança: **políticas** (o que é permitido, proibido e sob quais condições); **papéis e responsabilidades** (quem aprova o quê — frequentemente um comitê de IA multidisciplinar com jurídico, segurança, negócio e dados); **inventário de casos de uso** (quais sistemas de IA existem — não se governa o que não se conhece); **classificação de risco** (nem todo caso merece o mesmo rigor: um assistente interno de FAQ ≠ um modelo de concessão de crédito); **processo de aprovação**; **monitoramento contínuo**; e **auditoria**.

A **governança de dados** é a base, e a prova a cobra: **data lineage** (a origem e a trajetória do dado), **data provenance** (a proveniência e a legitimidade da fonte), **qualidade** (completude, consistência, atualidade), **classificação** (público, interno, confidencial, restrito), **retenção e eliminação**, e **consentimento** (os titulares autorizaram este uso?). Um modelo treinado em dados obtidos sem base legal é um passivo, por melhor que seja sua acurácia.

Os **frameworks** citados: **AWS Well-Architected Framework** (com **Machine Learning Lens**), **NIST AI Risk Management Framework**, **ISO 42001** e o **AWS Cloud Adoption Framework for AI/ML (CAF-AI)**.

As **ferramentas AWS**: **SageMaker Model Registry** (versionamento e aprovação), **Model Cards** (documentação), **SageMaker Pipelines** (reprodutibilidade), **AWS Config** (conformidade de recursos), **CloudTrail** (auditoria), **Organizations + SCPs** (políticas entre contas — por exemplo, negar o uso de serviços de IA em contas não aprovadas), **IAM** (controle de acesso) e **tags** (rastreamento de custo e propriedade).

O ciclo que fecha o conceito: **identificar → avaliar risco → mitigar → monitorar → auditar → melhorar**. É contínuo, não um projeto com data de término.

## 🎓 Pontos-chave para a prova

- Governança = **políticas + papéis + processos** para uso responsável e controlado da IA.
- **Inventário de casos de uso** e **classificação de risco** são pontos de partida.
- Governança de dados: **lineage, provenance, qualidade, classificação, retenção, consentimento**.
- Frameworks: **Well-Architected (ML Lens)**, **NIST AI RMF**, **ISO 42001**, **CAF-AI**.
- **Model Registry + Model Cards + Pipelines** dão versionamento, documentação e reprodutibilidade.
- **Organizations/SCPs** aplicam políticas entre contas; **CloudTrail** audita.
- Ciclo contínuo: **identificar → avaliar → mitigar → monitorar → auditar**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Governança de IA | Estrutura de políticas e processos para uso responsável da IA |
| Data lineage | Rastreamento da origem e das transformações do dado |
| Data provenance | Proveniência e legitimidade da fonte do dado |
| Classificação de dados | Categorização por sensibilidade |
| Model Registry | Catálogo versionado de modelos com aprovação |
| SCP | Service Control Policy — política de permissões entre contas |
| NIST AI RMF | Framework de gestão de risco de IA do NIST |
| ML Lens | Extensão do Well-Architected específica para ML |
| Comitê de IA | Grupo multidisciplinar que aprova e supervisiona casos de uso |

## 💡 Exemplo prático / caso de uso

Uma empresa cria seu programa de governança de IA. Monta um **comitê** com jurídico, segurança e negócio; levanta o **inventário** e descobre 14 iniciativas de IA, três das quais ninguém sabia que existiam; **classifica o risco** (o chatbot de FAQ é baixo, o modelo de crédito é alto); define que casos de **alto risco** exigem **Clarify**, **Model Card** aprovado e **A2I** obrigatório; usa **SCPs** para impedir que contas de desenvolvimento chamem serviços de IA com dados de produção; e audita trimestralmente via **CloudTrail** e **Audit Manager**. O achado mais valioso do processo foi o inventário — governar começa por saber o que existe.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
