# 47. Amazon DeepRacer Dashboard

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **console do DeepRacer** é onde você treina, avalia e itera os modelos — e onde os conceitos de RL ficam visíveis em gráficos. Vale entender o que cada painel mostra, porque é a melhor intuição prática sobre treino de modelos que o curso oferece.

O fluxo é: **Create model** (escolhe a pista, o action space, a função de recompensa, os hiperparâmetros e o tempo de treino) → **Train** (o simulador roda episódios e o gráfico de recompensa evolui em tempo real) → **Evaluate** (roda voltas de teste sem treinar, medindo tempo e taxa de conclusão) → **Iterate** (ajusta e re-treina, possivelmente **clonando** o modelo para continuar de onde parou) → **Submit** (envia para a DeepRacer League ou implanta no carro físico).

O **gráfico de treino** tem três séries e ler isso é o aprendizado central: a **recompensa média por episódio** (deve **subir** e depois estabilizar), o **percentual de conclusão no treino** e o **percentual de conclusão na avaliação**. Uma curva que sobe e estabiliza indica **convergência**. Uma curva errática indica função de recompensa ruim ou hiperparâmetros inadequados. E uma curva que sobe no **treino** mas não melhora na **avaliação** é o velho conhecido **overfitting** — o modelo decorou aquela pista específica em vez de aprender a dirigir. O antídoto é o mesmo de sempre: **avaliar em uma pista diferente** da usada no treino.

A **avaliação** mostra tempo por volta, taxa de conclusão e o traçado percorrido. Aqui você vê se o carro é rápido, se é consistente e onde ele sai da pista — e o traçado costuma revelar exatamente qual termo da função de recompensa está mal calibrado.

Os **logs** vão para o **CloudWatch**, com detalhes por passo (posição, recompensa recebida, ação tomada), úteis para depurar a função de recompensa quando o comportamento surpreende.

O paralelo com ML "de verdade" é o que a prova valoriza: **treinar → avaliar em dados não vistos → detectar overfitting → iterar**. É o mesmo ciclo do SageMaker, só que com um carrinho na tela — o que o torna muito mais fácil de internalizar.

## 🎓 Pontos-chave para a prova

- Fluxo: **Create → Train → Evaluate → Iterate → Submit/Deploy**.
- **Recompensa média crescente e estável** = convergência do treino.
- **Treino bom + avaliação ruim = overfitting** (o modelo decorou a pista).
- Avalie **em pista diferente** para medir generalização.
- **Clonar** um modelo permite continuar o treino a partir dele.
- Logs detalhados vão para o **CloudWatch**.
- O ciclo espelha o de qualquer projeto de ML: treinar, avaliar, iterar.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Reward graph | Gráfico da recompensa média por episódio |
| Convergência | Estabilização do aprendizado em um bom desempenho |
| Evaluation | Voltas de teste sem treino, medindo desempenho real |
| Completion rate | Percentual de voltas concluídas |
| Clonar modelo | Continuar o treino a partir de um modelo existente |
| Overfitting (RL) | Modelo especializado numa pista, ruim em outras |
| Iteração | Ciclo de ajustar recompensa/hiperparâmetros e re-treinar |

## 💡 Exemplo prático / caso de uso

Você treina por 60 minutos e o gráfico mostra a recompensa subindo até estabilizar: bom sinal. A avaliação **na mesma pista** dá 100% de conclusão em 9,8s. Empolgado, você avalia em **outra pista** e a taxa despenca para 20% — **overfitting** clássico: o modelo memorizou aquelas curvas específicas em vez de aprender o princípio "fique na pista". A correção é generalizar a função de recompensa (privilegiar `all_wheels_on_track` e `progress` em vez de waypoints específicos) e treinar em pistas variadas. Se isso soa exatamente como o diagnóstico da aula 6, é porque é: mesmo conceito, roupagem diferente.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
