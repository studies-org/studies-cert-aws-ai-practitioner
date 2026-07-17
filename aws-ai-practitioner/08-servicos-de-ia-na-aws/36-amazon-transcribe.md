# 36. Amazon Transcribe

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Transcribe** converte **fala em texto** (*Automatic Speech Recognition* — ASR). A direção importa e é fonte de confusão: **Transcribe = áudio → texto**; **Polly = texto → áudio**. Memorize esse par invertido, porque a prova o explora.

Os recursos cobrados: **Speaker diarization** (*speaker identification*) — identifica **quem falou o quê**, essencial em reuniões e ligações; **Custom vocabulary** — melhora o reconhecimento de termos específicos (nomes de produtos, siglas, jargão médico); **Custom Language Models** — adapta o modelo ao seu domínio com texto de treino; **Automatic language identification**; **Channel identification** — separa canais de áudio (por exemplo, atendente e cliente em gravações estéreo); **PII redaction** — identifica e remove dados sensíveis da transcrição (e até do áudio); **Toxicity detection**; e **timestamps** por palavra.

Existem modos **batch** (arquivo no S3) e **streaming** (tempo real, para legendagem ao vivo e assistentes). E há variantes especializadas: **Transcribe Medical** (terminologia clínica, compatível com HIPAA) e **Transcribe Call Analytics** (voltado a call centers, com sentimento, interrupções, tempo de fala e resumo da chamada).

O Transcribe é a **porta de entrada** dos pipelines de voz. Depois de transcrever, você pode encadear: **Comprehend** para sentimento, **Translate** para outros idiomas, **Bedrock** para resumir a reunião, **Kendra** para tornar as gravações pesquisáveis.

## 🎓 Pontos-chave para a prova

- Transcribe = **fala → texto (ASR)**. Polly = **texto → fala**. Não inverta.
- **Speaker diarization** identifica os diferentes interlocutores.
- **Custom vocabulary** melhora o reconhecimento de termos e siglas específicos.
- **PII redaction** remove dados sensíveis da transcrição.
- Modos **batch** e **streaming** (tempo real).
- Variantes: **Transcribe Medical** (HIPAA) e **Call Analytics** (call center).
- Pipeline típico: **Transcribe → Comprehend/Translate/Bedrock**.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| ASR | Automatic Speech Recognition — reconhecimento automático de fala |
| Speaker diarization | Identificação de qual interlocutor falou cada trecho |
| Custom vocabulary | Lista de termos que melhora a precisão do reconhecimento |
| Custom Language Model | Modelo adaptado ao domínio com texto de treino |
| Channel identification | Separação de canais de áudio distintos |
| PII redaction | Remoção de dados pessoais da transcrição |
| Streaming transcription | Transcrição em tempo real |
| Transcribe Medical | Variante clínica compatível com HIPAA |

## 💡 Exemplo prático / caso de uso

Um call center grava 8 mil ligações por dia. O **Transcribe Call Analytics** transcreve com **diarização** (separa atendente e cliente), aplica **redação de PII** (remove número de cartão dito em voz alta) e gera métricas de sentimento e interrupção. As transcrições vão para o **Bedrock**, que resume cada chamada e sugere ações, e para o **Kendra**, tornando o histórico pesquisável. Nada disso exigiu treinar um modelo de fala.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
