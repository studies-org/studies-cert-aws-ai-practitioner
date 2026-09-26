# 📊 SCORE — AWS Certified AI Practitioner (AIF-C01)

Painel de acompanhamento do desempenho nos exercícios de cada seção.

## Placar por seção

| Seção | Questões | Acertos | % | Status |
|-------|---------:|--------:|--:|:------:|
| 01 — Iniciando | 5 | 0 | 0% | ⬜ |
| 02 — A AWS | 7 | 0 | 0% | ⬜ |
| 03 — AI: Inteligência Artificial | 10 | 0 | 0% | ⬜ |
| 04 — Engenharia de Prompt | 8 | 0 | 0% | ⬜ |
| 05 — Amazon Bedrock | 10 | 0 | 0% | ⬜ |
| 06 — Amazon Q | 7 | 0 | 0% | ⬜ |
| 07 — SageMaker | 6 | 0 | 0% | ⬜ |
| 08 — Serviços de IA na AWS | 10 | 0 | 0% | ⬜ |
| 09 — Práticas e Responsabilidades de IA | 8 | 0 | 0% | ⬜ |
| 10 — Segurança | 5 | 0 | 0% | ⬜ |
| 11 — O Exame | 5 | 0 | 0% | ⬜ |
| 12 — Finalizando | 5 | 0 | 0% | ⬜ |
| 13 — Bônus (revisão geral) | 10 | 0 | 0% | ⬜ |
| **TOTAL GERAL** | **96** | **0** | **0%** | **⬜** |

> O total é a **média ponderada**: `soma dos acertos ÷ soma das questões respondidas`.
> Seções ainda não respondidas (⬜) ficam fora do cálculo do total.

## Legenda de status

| Status | Faixa | Significado |
|:------:|-------|-------------|
| ⬜ | — | Ainda não respondida |
| 🔴 | < 60% | Precisa de revisão completa da seção |
| 🟡 | 60–79% | Revisar os tópicos errados |
| 🟢 | ≥ 80% | Domínio adequado |

> Referência: a aprovação no exame real exige **700/1000**. Mire em **🟢 (≥80%)** em todas as seções antes de agendar.

## Histórico de tentativas

| Data | Seção | Acertos | % | Observação |
|------|-------|--------:|--:|------------|
| — | — | — | — | Nenhuma tentativa registrada ainda |

## Simulados

| Data | Questões | Acertos | % | Status |
|------|---------:|--------:|--:|:------:|
| — | — | — | — | ⬜ |

---

## Como atualizar este painel

1. Abra o `exercicios.md` da seção que você estudou.
2. Preencha o bloco **"Minhas respostas"** no topo do arquivo, por exemplo:
   ```
   > Responda aqui: 1-B, 2-C, 3-A, 4-D, 5-B
   ```
   **Não olhe o gabarito antes.** Ele está no bloco `<details>` no final do arquivo.
3. Peça ao Claude Code:
   ```
   corrigir seção 5
   ```
4. O Claude vai:
   - ler o `exercicios.md` da seção;
   - comparar suas respostas com o gabarito;
   - calcular acertos e porcentagem;
   - mostrar quais você errou e **por quê**;
   - **atualizar este `SCORE.md`** (placar, status, total ponderado e histórico).

Outros comandos úteis:

| Comando | O que faz |
|---------|-----------|
| `estudar bedrock` | Resume a seção e faz uma pergunta de fixação |
| `corrigir seção 5` | Corrige os exercícios e atualiza este arquivo |
| `meu progresso` | Lê este painel e sugere o que revisar |
| `simulado` | Monta um simulado de 20 questões misturando seções |
