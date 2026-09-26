# 41. Amazon Personalize

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Personalize** é o serviço gerenciado de **recomendação personalizada em tempo real**, construído sobre a mesma tecnologia usada pela Amazon.com. Ele entrega o clássico "recomendado para você" sem que você precise construir um sistema de recomendação do zero.

Ele consome **três tipos de dataset**: **Interactions** (o histórico de eventos — visualizações, cliques, compras, avaliações — o **único obrigatório**), **Users** (atributos dos usuários) e **Items** (atributos dos itens: categoria, preço, gênero). Quanto mais rico o contexto, melhor a recomendação.

As **receitas (recipes)** definem o tipo de recomendação: **User-Personalization** (recomendações personalizadas por usuário — a mais usada), **Personalized-Ranking** (reordena uma lista de candidatos conforme o gosto do usuário), **Related-Items / SIMS** ("quem viu isso também viu"), **Trending-Now** e **Personalized-Actions**. Os artefatos são o **Solution** (a configuração de treino), a **Solution version** (o modelo treinado) e a **Campaign** (o endpoint de inferência em tempo real) — ou os **Recommenders** no modo de domínio (E-commerce, Media).

Dois recursos merecem destaque. O **Event tracker** permite enviar eventos **em tempo real**, atualizando as recomendações conforme o usuário navega na sessão atual — sem precisar re-treinar. E as **Business rules / filters** permitem excluir itens (não recomendar o que já foi comprado, esconder produtos fora de estoque) e **promover** categorias.

O Personalize resolve nativamente o **cold start** — o problema de recomendar para um usuário novo ou um item recém-lançado, que não têm histórico — usando os metadados de item e o comportamento agregado.

A fronteira: **recomendar itens a pessoas → Personalize**. **Prever valores futuros no tempo → Forecast/SageMaker Canvas**. **Busca por documentos → Kendra**. São três serviços que a prova frequentemente coloca juntos como distratores.

## 🎓 Pontos-chave para a prova

- Personalize = **recomendação em tempo real**, mesma tecnologia da Amazon.com.
- Datasets: **Interactions (obrigatório)**, Users e Items.
- Receitas: **User-Personalization**, **Personalized-Ranking**, **Related-Items (SIMS)**, Trending-Now.
- **Campaign** = endpoint de inferência; **Event tracker** = eventos em tempo real na sessão.
- **Filters/business rules** excluem ou promovem itens.
- Trata **cold start** de usuários e itens novos.
- Recomendação → Personalize. Série temporal → Forecast. Busca → Kendra.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Interactions dataset | Histórico de eventos usuário-item (obrigatório) |
| Recipe | Algoritmo/tipo de recomendação escolhido |
| Solution / Solution version | Configuração de treino e modelo treinado |
| Campaign | Endpoint que serve recomendações em tempo real |
| Event tracker | Mecanismo de ingestão de eventos em tempo real |
| Filter | Regra de negócio que exclui ou promove itens |
| Cold start | Recomendar para usuário/item sem histórico |
| SIMS | Receita de itens similares ("quem viu isso também viu") |

## 💡 Exemplo prático / caso de uso

Um streaming envia ao **Personalize** o histórico de visualizações (**Interactions**), o perfil dos assinantes (**Users**) e os metadados dos títulos (**Items**). Treina uma solution com a receita **User-Personalization** e publica uma **Campaign**. A home passa a ser personalizada por usuário. Um **filter** garante que nada já assistido até o fim seja recomendado de novo. Quando um assinante novo entra e assiste dois documentários, o **event tracker** ajusta a home **na mesma sessão** — sem re-treino, resolvendo o cold start na prática.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
