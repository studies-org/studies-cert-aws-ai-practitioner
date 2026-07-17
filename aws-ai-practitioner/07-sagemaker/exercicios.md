# Exercícios — 07. SageMaker

## Minhas respostas
> Responda aqui: 1-_, 2-_, 3-_, 4-_, 5-_, 6-_

## Questões

### 1. Uma empresa quer treinar um modelo de previsão de churn usando seus próprios dados e um algoritmo específico, com controle total sobre o processo. Qual serviço é o adequado?
- A) Amazon Bedrock
- B) Amazon SageMaker
- C) Amazon Q Business
- D) Amazon Comprehend

### 2. Qual componente do SageMaker detecta viés em datasets e modelos, além de fornecer explicabilidade?
- A) SageMaker Model Monitor
- B) SageMaker Clarify
- C) SageMaker Feature Store
- D) SageMaker Ground Truth

### 3. Um analista de negócio sem conhecimento de programação precisa criar um modelo preditivo. Qual ferramenta é a mais adequada?
- A) SageMaker Studio com notebooks Python
- B) SageMaker Canvas
- C) SageMaker Pipelines
- D) SageMaker Feature Store

### 4. Qual componente monitora data drift e model drift em modelos já em produção?
- A) SageMaker Clarify
- B) SageMaker Model Monitor
- C) SageMaker Autopilot
- D) SageMaker JumpStart

### 5. Qual afirmação sobre custo do SageMaker é correta?
- A) Endpoints de inferência real-time só cobram quando recebem requisições
- B) Endpoints de inferência real-time cobram por hora enquanto existirem, mesmo ociosos
- C) O SageMaker é totalmente gratuito no Free Tier permanente
- D) Apenas o treinamento gera custo; a inferência é gratuita

### 6. Uma equipe quer implantar rapidamente um modelo pré-treinado de código aberto sem construí-lo do zero. Qual recurso do SageMaker facilita isso?
- A) SageMaker Ground Truth
- B) SageMaker Data Wrangler
- C) SageMaker JumpStart
- D) SageMaker Model Cards

## Gabarito

<details>
<summary>Clique para ver o gabarito</summary>

1. **B** — **SageMaker** é a plataforma para **construir e treinar modelos próprios** com controle total. Bedrock serve para consumir/adaptar Foundation Models, o que não é o caso aqui — previsão de churn com dados tabulares é ML clássico, não IA Generativa.

2. **B** — **SageMaker Clarify** faz **detecção de viés** (em dados e em modelos) e **explicabilidade** via SHAP. Model Monitor cuida de drift em produção, e são funções frequentemente confundidas nas questões.

3. **B** — **SageMaker Canvas** é a interface **visual sem código**, desenhada exatamente para analistas de negócio construírem modelos sem escrever Python.

4. **B** — **Model Monitor** acompanha **data drift** (a distribuição das entradas muda) e **model drift** (a qualidade das previsões cai) em modelos implantados.

5. **B** — **Endpoints real-time cobram por hora enquanto existirem**, independentemente do tráfego. É a causa clássica de fatura surpresa — delete os endpoints ao final do laboratório. (A opção que escala a zero é o **Serverless inference**.)

6. **C** — **JumpStart** é o hub de **modelos pré-treinados e Foundation Models** prontos para deploy com poucos cliques, incluindo modelos de código aberto.

</details>
