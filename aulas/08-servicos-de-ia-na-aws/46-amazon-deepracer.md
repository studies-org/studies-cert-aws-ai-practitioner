# 46. Amazon DeepRacer

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **AWS DeepRacer** é um carro de corrida autônomo em escala **1/18** — e, mais importante, uma plataforma **educacional** para aprender **aprendizado por reforço (RL)** na prática, de forma gamificada. Existe o carro físico e o **simulador** na nuvem, onde a maior parte do aprendizado acontece.

O mapeamento com os conceitos de RL da aula 9 é direto: o **agente** é o carro; o **ambiente** é a pista (simulada ou real); o **estado** vem dos sensores (câmera frontal, e nos modelos avançados também LIDAR e câmera estéreo); as **ações** são combinações de velocidade e ângulo de direção (o **action space**, discreto ou contínuo); e a **recompensa** é definida por **você**.

A **função de recompensa** é o coração da experiência. Você escreve uma função Python que recebe um dicionário de parâmetros — `track_width`, `distance_from_center`, `all_wheels_on_track`, `speed`, `steering_angle`, `progress`, `steps`, `is_offtrack`, `waypoints` — e retorna um número. Recompensar a proximidade da linha central produz um carro cauteloso; recompensar velocidade e progresso produz um carro rápido mas instável. **A função de recompensa define o comportamento aprendido** — e é aí que está a lição pedagógica: você não programa a direção, você programa o **objetivo**, e o comportamento emerge do treino.

Você também configura **hiperparâmetros** (learning rate, batch size, número de epochs, entropia) e o **tempo de treino**. O algoritmo padrão é o **PPO (Proximal Policy Optimization)**, com suporte também a **SAC**.

Os modos de corrida: **Time Trial** (contra o relógio, pista vazia), **Object Avoidance** (com obstáculos estáticos) e **Head-to-Head** (contra outro carro). E existe a **DeepRacer League**, com competições virtuais e presenciais.

Para a prova, o essencial é: **DeepRacer = o serviço AWS de aprendizado por reforço**. Se a questão mencionar RL, recompensa, agente ou "aprender por tentativa e erro", DeepRacer é a associação esperada.

## 🎓 Pontos-chave para a prova

- DeepRacer = plataforma **educacional de aprendizado por reforço**; carro autônomo 1/18.
- Mapeamento: **agente = carro**, **ambiente = pista**, **ação = velocidade/direção**, **recompensa = sua função**.
- A **função de recompensa** em Python define o comportamento aprendido.
- **Action space** pode ser **discreto** ou **contínuo**.
- Algoritmo padrão: **PPO**; também suporta **SAC**.
- Modos: **Time Trial**, **Object Avoidance** e **Head-to-Head**.
- Treino no **simulador**, com opção de implantar no carro físico.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Função de recompensa | Código Python que define o que é bom ou ruim |
| Action space | Conjunto de ações possíveis (discreto ou contínuo) |
| Waypoint | Ponto de referência ao longo da pista |
| `all_wheels_on_track` | Parâmetro que indica se o carro está totalmente na pista |
| `distance_from_center` | Distância do carro em relação à linha central |
| PPO | Proximal Policy Optimization — algoritmo padrão de treino |
| Episódio | Uma tentativa completa do agente no ambiente |
| Simulador | Ambiente virtual de treino na nuvem |

## 💡 Exemplo prático / caso de uso

```python
def reward_function(params):
    track_width = params['track_width']
    distance_from_center = params['distance_from_center']
    all_wheels_on_track = params['all_wheels_on_track']

    if not all_wheels_on_track:
        return 1e-3                       # penalidade forte por sair da pista

    marker = 0.1 * track_width
    return 1.0 if distance_from_center <= marker else 0.1
```

Este modelo aprende a andar colado à linha central — seguro, porém lento. Adicionar `params['speed']` à recompensa produziria um carro mais rápido e mais propenso a sair da pista. **Nenhuma linha diz ao carro como dirigir**: ele descobre sozinho, ao longo de milhares de episódios, o que maximiza a recompensa que você escreveu.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
