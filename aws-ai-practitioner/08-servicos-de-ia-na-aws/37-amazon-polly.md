# 37. Amazon Polly

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Polly** converte **texto em fala** (*Text-to-Speech* — TTS), com vozes naturais em dezenas de idiomas e variantes regionais (incluindo português do Brasil — Camila, Vitória, Ricardo).

Os **tipos de voz** que a prova diferencia: **Standard** (concatenativa, mais antiga e barata), **Neural (NTTS)** (redes neurais, muito mais natural — o padrão recomendado), **Long-Form** (otimizada para textos longos, como artigos e audiolivros) e **Generative** (a mais expressiva e conversacional).

Os recursos principais: **SSML (Speech Synthesis Markup Language)** — marcação XML que controla pausas, ênfase, velocidade, tom e pronúncia (`<break>`, `<emphasis>`, `<prosody>`); **Lexicons** — dicionários de pronúncia customizada, para siglas e nomes próprios ("AWS" lido como "A-W-S", não "aus"); **Speech marks** — metadados de tempo por palavra e fonema, usados para sincronizar legendas ou lipsync de avatares; **Newscaster e Conversational styles**; e **Brand Voice**, uma voz exclusiva customizada para a marca.

Polly suporta síntese **em tempo real** (`SynthesizeSpeech`) e **assíncrona** (`StartSpeechSynthesisTask`, para textos longos, com saída em S3). Os formatos de saída incluem MP3, OGG, PCM e JSON (para speech marks).

Casos de uso: acessibilidade (leitura de conteúdo para deficientes visuais), URA e assistentes de voz, e-learning, notícias em áudio, audiolivros. E o par que a prova adora: **Polly + Lex** para bots de voz, e **Transcribe → Translate → Polly** para dublagem automática.

## 🎓 Pontos-chave para a prova

- Polly = **texto → fala (TTS)**; Transcribe = fala → texto. Direções opostas.
- Vozes: **Standard, Neural (NTTS), Long-Form e Generative** — Neural é o padrão natural.
- **SSML** controla pausas, ênfase, velocidade e pronúncia.
- **Lexicons** definem pronúncia customizada de siglas e nomes.
- **Speech marks** sincronizam áudio com legendas/animação.
- Síntese **em tempo real** ou **assíncrona** (saída em S3).
- Casos: acessibilidade, URA, e-learning, dublagem.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| TTS | Text-to-Speech — síntese de fala a partir de texto |
| NTTS (Neural) | Vozes neurais, mais naturais que as Standard |
| SSML | Linguagem de marcação para controlar a síntese de fala |
| Lexicon | Dicionário de pronúncia customizada |
| Speech marks | Metadados de tempo por palavra/fonema |
| Brand Voice | Voz exclusiva customizada para uma marca |
| Long-Form voice | Voz otimizada para conteúdo extenso |

## 💡 Exemplo prático / caso de uso

Um portal de notícias oferece a versão em áudio de cada matéria. Usa **Polly Neural** com estilo **Newscaster**, aplica um **lexicon** para que siglas como "IBGE" e "PIB" sejam pronunciadas corretamente, e usa **SSML** para inserir pausas entre parágrafos. Como os artigos são longos, a síntese é **assíncrona**, com o MP3 gravado no **S3** e servido via CloudFront. As **speech marks** permitem destacar cada palavra no texto conforme o áudio avança — ganho direto de acessibilidade.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
