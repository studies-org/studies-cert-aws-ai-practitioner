# 31. Testando a Aplicação Amazon Q

> Seção: Amazon Q · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

Com a Web experience publicada, é hora de validar. Acesse a URL, faça login com o usuário do **Identity Center** e faça perguntas cujas respostas você **sabe** que estão nos documentos indexados. O objetivo do teste não é ver se "funciona", mas verificar **de onde vêm as respostas**.

O elemento mais importante da interface é a **citação**. Cada resposta traz referências aos documentos e trechos usados. Sempre clique nelas. Uma resposta correta com citação errada é um sinal de que a **recuperação** está imprecisa — e isso vai quebrar em perguntas mais difíceis, mesmo que essa tenha acertado por sorte.

Os **problemas típicos** e seus diagnósticos: *"não encontrei informação"* → o sync não rodou, não completou, ou o documento não está no prefixo configurado; *resposta genérica sem citação* → o conhecimento geral do modelo está habilitado e ele respondeu de memória, não dos seus documentos; *resposta incompleta* → o chunking cortou a informação ao meio, ou a pergunta exige juntar muitos documentos; *usuário não vê um documento* → comportamento **esperado** se a ACL da fonte não o permite.

Teste também o **feedback** (polegar para cima/baixo), que alimenta a melhoria contínua, e as **conversas multi-turno** — pergunte algo e depois faça uma pergunta de acompanhamento com pronome ("e no ano anterior?") para verificar se o contexto está sendo mantido.

Do lado administrativo, o console traz **métricas de uso**: número de conversas, perguntas mais frequentes, documentos mais citados e taxa de feedback positivo. Isso ajuda a identificar lacunas na documentação — se muita gente pergunta algo que o Q não responde, o problema pode não ser o Q, mas a **ausência do documento**.

Por fim, teste o **isolamento por permissão** com dois usuários diferentes, se possível. É a garantia que justifica o serviço em ambiente corporativo, e vale confirmar na prática.

## 🎓 Pontos-chave para a prova

- **Citações** são a ferramenta primária de validação e auditoria das respostas.
- "Não encontrei" geralmente indica **problema de sync ou de escopo da data source**.
- Resposta sem citação indica uso de **conhecimento geral do modelo** (ajuste em Admin controls).
- Respostas **variam por usuário** conforme as ACLs herdadas — isso é o comportamento correto.
- **Feedback do usuário** e **métricas de uso** apoiam a melhoria contínua.
- Q suporta **conversas multi-turno** com manutenção de contexto.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Citação | Referência ao documento/trecho que fundamentou a resposta |
| Sync status | Estado da sincronização da data source |
| Conversa multi-turno | Diálogo em que o contexto anterior é preservado |
| Feedback | Avaliação do usuário sobre a qualidade da resposta |
| Métricas de uso | Estatísticas de conversas, perguntas e documentos citados |
| Isolamento por ACL | Filtragem dos resultados conforme a permissão do usuário |

## 💡 Exemplo prático / caso de uso

Você pergunta *"qual é a política de home office?"* e o Q responde citando `politica-rh.pdf`. Depois pergunta *"e para estagiários?"* — a resposta correta continua ancorada no mesmo documento, mostrando que o contexto multi-turno foi preservado. Em seguida você pergunta algo que **não está** em documento nenhum: se a resposta vier confiante e **sem citação**, o conhecimento geral do modelo está ligado e precisa ser desabilitado nos **Admin controls**. É exatamente esse teste negativo que revela a configuração errada — o teste positivo sozinho não revelaria.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
