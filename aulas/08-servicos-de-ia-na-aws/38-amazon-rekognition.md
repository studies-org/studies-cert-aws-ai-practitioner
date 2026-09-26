# 38. Amazon Rekognition

> Seção: Serviços de IA na AWS · Certificação: AWS Certified AI Practitioner (AIF-C01)

## 📌 Resumo

O **Amazon Rekognition** é o serviço de **visão computacional** da AWS: análise de **imagens e vídeos** sem treinar modelo. Ele é o "Comprehend das imagens".

As capacidades: **Detecção de objetos, cenas e atividades** (labels); **Análise facial** (atributos como emoção aparente, óculos, faixa etária estimada); **Comparação e busca facial** (`CompareFaces`, e **Face Collections** para busca 1:N); **Reconhecimento de celebridades**; **Detecção de texto em imagens** (texto curto, como placas e legendas — não confundir com Textract); **Moderação de conteúdo** (identifica conteúdo impróprio, sugestivo ou violento); **Detecção de PPE** (equipamentos de proteção individual — capacete, luva, colete); **Face Liveness** (verifica se há uma pessoa real e presente diante da câmera, contra fotos e deepfakes); **Custom Labels** (treine o reconhecimento de objetos específicos da sua empresa com poucas imagens); e **Video segment detection**.

As fronteiras que a prova testa são três. **Rekognition × Textract**: Rekognition detecta **texto curto em cena** (uma placa numa foto); **Textract extrai documentos estruturados** (formulários, tabelas, faturas). Se a questão fala em documento, formulário ou tabela, é **Textract**. **Rekognition × modelos de imagem do Bedrock**: Rekognition **analisa** imagens; Stable Diffusion/Titan Image **geram** imagens. **Rekognition × SageMaker**: se o caso exige um modelo de visão totalmente customizado, é SageMaker; se as categorias são poucas e específicas, **Custom Labels** resolve com muito menos esforço.

Ponto de **IA responsável** que aparece na prova: o reconhecimento facial é uma tecnologia de **alto risco**, sujeita a questões de viés (historicamente com taxas de erro maiores para determinados grupos demográficos) e de privacidade. A AWS recomenda **human-in-the-loop** (via **Amazon A2I**) e limiares de confiança elevados em qualquer decisão consequente — especialmente em aplicações de segurança pública.

## 🎓 Pontos-chave para a prova

- Rekognition = **visão computacional** para imagens e vídeos; **analisa**, não gera.
- Capacidades: labels, análise/comparação facial, celebridades, **moderação de conteúdo**, **PPE**, **Face Liveness**, **Custom Labels**.
- **Rekognition** detecta texto em cena; **Textract** extrai texto de **documentos** (formulários/tabelas).
- **Custom Labels** treina categorias próprias com poucas imagens, sem código de ML.
- Reconhecimento facial é **alto risco**: viés e privacidade → use **A2I** e limiares altos.

## 🔑 Termos importantes

| Termo | Definição |
|-------|-----------|
| Label detection | Identificação de objetos, cenas e atividades |
| Face Collection | Conjunto indexado de faces para busca 1:N |
| CompareFaces | Comparação 1:1 entre duas faces |
| Content moderation | Detecção de conteúdo impróprio |
| PPE detection | Detecção de equipamentos de proteção individual |
| Face Liveness | Verificação de presença real da pessoa diante da câmera |
| Custom Labels | Treinamento de categorias visuais próprias |
| Confidence score | Grau de confiança da detecção |

## 💡 Exemplo prático / caso de uso

Uma rede social usa **Rekognition Content Moderation** para triar imagens enviadas por usuários. Conteúdo com alta confiança de violação é bloqueado automaticamente; os casos na **zona cinzenta** vão para revisão humana via **Amazon A2I**. Uma construtora usa **PPE detection** nas câmeras do canteiro para alertar quando alguém entra sem capacete. E uma fábrica usa **Custom Labels**, treinado com 200 fotos, para identificar um defeito específico de solda que nenhum modelo genérico reconheceria.

## ✅ Checklist de domínio

- [ ] Entendi o conceito principal
- [ ] Sei diferenciar de conceitos parecidos
- [ ] Consigo dar um caso de uso real
