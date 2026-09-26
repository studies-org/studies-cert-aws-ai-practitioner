# 39. Amazon Forecast

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Forecast** é o serviço gerenciado de **previsão de séries temporais** (*time series forecasting*). Ele prevê valores futuros a partir de dados históricos com dimensão temporal: demanda de produtos, tráfego de site, necessidade de pessoal, consumo de energia, fluxo de caixa.

O diferencial em relação a uma planilha ou a uma regressão simples é que o Forecast incorpora automaticamente **sazonalidade**, **tendência** e **dados relacionados** — feriados, promoções, preço, clima. Ele aplica **AutoML** para testar vários algoritmos (ARIMA, Prophet, DeepAR+, CNN-QR, ETS, NPTS) e escolher o melhor para os seus dados.

Os conceitos do serviço: **Dataset group** (agrupa os datasets), **Target time series** (o histórico do que você quer prever), **Related time series** (variáveis que influenciam, como preço), **Item metadata** (atributos estáticos, como categoria do produto), **Predictor** (o modelo treinado) e **Forecast** (as previsões geradas). As previsões vêm em **quantis** (P10, P50, P90), o que permite decidir conforme o risco: usar P90 para estoque de item crítico (superestimar é melhor que faltar), P10 para item perecível (faltar é melhor que perder).

**Aviso importante e atual:** o Amazon Forecast está em **caminho de descontinuação** — a AWS deixou de aceitar novos clientes e recomenda a migração para as **capacidades de forecasting do SageMaker Canvas**. A prova ainda pode citar o Forecast como o serviço de séries temporais, então conheça o conceito; mas a recomendação para novas arquiteturas é **SageMaker Canvas**.

A fronteira: se a questão fala em **"prever valores futuros com base no histórico ao longo do tempo"**, é **séries temporais** (Forecast/Canvas). Se fala em prever uma categoria sem dimensão temporal, é classificação no SageMaker. Se fala em recomendar produtos, é **Personalize** — não Forecast.

## 🎓 Pontos-chave para a prova

- Forecast = **previsão de séries temporais** com AutoML e sazonalidade.
- Componentes: target time series, **related time series**, item metadata, predictor, forecast.
- Previsões em **quantis (P10/P50/P90)** para decidir conforme o risco.
- Casos: **demanda, estoque, capacidade, pessoal, finanças**.
- Serviço em **descontinuação** — a recomendação atual é **SageMaker Canvas** para forecasting.
- Previsão temporal → Forecast/Canvas. Recomendação de itens → **Personalize**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Série temporal | Sequência de observações ordenadas no tempo |
| Target time series | Histórico da variável a ser prevista |
| Related time series | Variável que influencia a previsão (preço, promoção) |
| Item metadata | Atributos estáticos do item |
| Predictor | Modelo de previsão treinado |
| Quantil (P10/P50/P90) | Nível de probabilidade da previsão |
| Sazonalidade | Padrão que se repete em intervalos regulares |
| AutoML | Seleção e ajuste automático de algoritmos |

## 💡 Exemplo prático / caso de uso

Uma rede de supermercados prevê a demanda de 30 mil SKUs por loja. O **target time series** é o histórico de vendas, o **related time series** inclui preço e promoções, e o **item metadata** traz a categoria. Para itens críticos que não podem faltar, a equipe usa o quantil **P90** (previsão conservadoramente alta, aceitando estoque extra); para perecíveis, usa **P10** (previsão baixa, aceitando ruptura para evitar desperdício). Essa escolha de quantil conforme o custo do erro é o raciocínio que a prova cobra.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
