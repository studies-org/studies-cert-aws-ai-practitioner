# 9. Machine Learning Reforçada

> Seção: AI — Inteligência Artificial · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **aprendizado por reforço (Reinforcement Learning, RL)** é o terceiro paradigma. Aqui não há dataset rotulado nem busca por estrutura oculta: existe um **agente** que **age** dentro de um **ambiente**, recebe **recompensas** ou **punições** e aprende, por tentativa e erro, a **política** que maximiza a recompensa acumulada ao longo do tempo.

Os componentes que caem na prova são: **Agente** (quem decide), **Ambiente** (o mundo em que ele atua), **Estado** (a situação atual), **Ação** (o que o agente pode fazer), **Recompensa** (o sinal numérico de feedback) e **Política** (a estratégia que mapeia estado → ação). O treinamento é iterativo e envolve o dilema **exploration vs. exploitation**: explorar ações novas para descobrir algo melhor, ou explorar o que já se sabe que funciona.

Casos de uso típicos: robótica, jogos, veículos autônomos, otimização de rotas, gestão de portfólio e controle de sistemas (como resfriamento de datacenter). Na AWS, o serviço emblemático é o **AWS DeepRacer** — um carrinho autônomo em escala 1/18 onde você escreve a **função de recompensa** e o modelo aprende a completar a pista. É didaticamente RL puro, e por isso está no curso (aulas 46 e 47).

A conexão mais importante com o exame moderno é o **RLHF — Reinforcement Learning from Human Feedback**. É a técnica usada para **alinhar** grandes modelos de linguagem ao comportamento desejado: humanos comparam e ranqueiam respostas do modelo, esses rankings treinam um **reward model**, e o LLM é então ajustado por RL para maximizar a pontuação desse reward model. É assim que um modelo bruto se torna um assistente útil, honesto e inofensivo. **RLHF é um tema recorrente na AIF-C01** — sempre que a questão falar em "alinhar o modelo às preferências humanas", a resposta é RLHF.

## 🎓 Pontos-chave para a prova

- RL aprende por **tentativa e erro** com **recompensas**, sem dados rotulados.
- Componentes: **agente, ambiente, estado, ação, recompensa, política**.
- Dilema **exploration vs. exploitation**.
- **AWS DeepRacer** é o serviço AWS de aprendizado por reforço.
- **RLHF** alinha LLMs às preferências humanas usando um **reward model** treinado com rankings humanos.
- Casos de uso: robótica, jogos, veículos autônomos, otimização sequencial de decisões.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Agente | Entidade que toma decisões no ambiente |
| Ambiente | Contexto em que o agente atua |
| Estado | Representação da situação atual do ambiente |
| Recompensa (reward) | Sinal numérico de feedback por uma ação |
| Política (policy) | Estratégia que mapeia estados em ações |
| Função de recompensa | Código que define o que é bom ou ruim (você escreve no DeepRacer) |
| Exploration vs. Exploitation | Trade-off entre testar o novo e usar o que já funciona |
| RLHF | Reinforcement Learning from Human Feedback — alinhamento de LLMs |
| Reward model | Modelo que aprende a pontuar respostas conforme a preferência humana |

## 💡 Exemplo prático / caso de uso

No **AWS DeepRacer**, o agente é o carro, o ambiente é a pista, o estado vem das imagens da câmera, as ações são acelerar e virar, e a recompensa é definida por você — por exemplo, "+1 quando o carro está próximo da linha central, penalidade quando sai da pista". Nenhuma volta é rotulada como "correta"; o carro aprende sozinho, milhares de episódios depois. A mesma lógica, aplicada a rankings humanos de respostas de texto, é o **RLHF** que transforma um LLM cru em um assistente alinhado.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
