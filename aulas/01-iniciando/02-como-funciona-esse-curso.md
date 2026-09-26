# 2. Como Funciona Esse Curso

> Seção: Iniciando · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O curso é organizado em blocos que espelham os **domínios oficiais do exame**. Primeiro vêm os fundamentos (o que é a AWS, o que é IA/ML), depois engenharia de prompt, então o coração do exame — **Amazon Bedrock** —, seguido de Amazon Q, SageMaker, o catálogo de serviços de IA gerenciados, IA responsável e, por fim, segurança e dicas de prova.

Os cinco domínios oficiais e seus pesos são: **Domínio 1 — Fundamentos de IA e ML (20%)**, **Domínio 2 — Fundamentos de IA Generativa (24%)**, **Domínio 3 — Aplicações de Foundation Models (28%)**, **Domínio 4 — Diretrizes de IA Responsável (14%)** e **Domínio 5 — Segurança, Conformidade e Governança de soluções de IA (14%)**. Repare que os domínios 2 e 3 somam **52%** — mais da metade da prova gira em torno de IA Generativa e Foundation Models, o que explica o peso dado ao Bedrock.

O método recomendado para usar este repositório é o ciclo **assistir → ler → exercitar → corrigir → revisar**. Assista à aula do curso, leia o `.md` correspondente aqui (que condensa o que cai na prova), e ao terminar a seção resolva o `exercicios.md`. Peça ao Claude Code para corrigir e o `SCORE.md` é atualizado automaticamente.

Prática em conta real é fortemente recomendada, mesmo sendo uma prova conceitual. Habilitar um modelo no Bedrock, criar um Guardrail, subir uma Knowledge Base — cada uma dessas ações fixa mais do que dez releituras. Use o **Free Tier** e sempre remova os recursos ao final para evitar cobranças.

## 🎓 Pontos-chave para a prova

- **Domínio 1 — Fundamentos de IA/ML: 20%**
- **Domínio 2 — Fundamentos de IA Generativa: 24%**
- **Domínio 3 — Aplicações de Foundation Models: 28%** (maior peso)
- **Domínio 4 — Diretrizes de IA Responsável: 14%**
- **Domínio 5 — Segurança, Conformidade e Governança: 14%**
- Bedrock + prompt engineering + RAG concentram a maior densidade de questões.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Exam Guide | Documento oficial da AWS com domínios, pesos e escopo do exame |
| Domínio 3 | "Applications of Foundation Models" — maior peso (28%) |
| Free Tier | Camada gratuita da AWS usada para os laboratórios do curso |
| Ciclo de estudo | Assistir → ler → exercitar → corrigir → revisar |
| Spaced repetition | Revisar em intervalos crescentes; aplicado via seções 🔴/🟡 do SCORE |

## 💡 Exemplo prático / caso de uso

Você termina a Seção 05 (Bedrock). Abre `05-amazon-bedrock/exercicios.md`, preenche o bloco "Minhas respostas" e pede: *"corrigir seção 5"*. A Skill lê o gabarito, calcula que você acertou 8/10 (80% → 🟢) e grava isso no `SCORE.md`. Depois você pede *"meu progresso"* e ela aponta que a Seção 03 está 🔴 e deve ser revisada antes do simulado.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
