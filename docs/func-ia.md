# **Funcionalidades IA** 🤖

## **Validação de Documentação e Identidade** 🪪🤳

A validação da documentação do usuário é realizada utilizando duas tecnologias avançadas:

1. **Reconhecimento Facial com DeepFace** 🧑‍⚖️  
   A biblioteca **DeepFace** é empregada para realizar o reconhecimento facial. Ela compara a selfie enviada pelo usuário com a foto contida na CNH, assegurando que ambas as imagens correspondem à mesma pessoa.

2. **Reconhecimento de Texto com Pytesseract** 📝  
   O **Pytesseract**, uma ferramenta baseada em IA para reconhecimento ótico de caracteres (OCR), é utilizado para extrair e validar o **CPF** presente na CNH. O sistema compara o CPF informado pelo usuário durante o cadastro com o CPF extraído da imagem do documento.

Se a validação do CPF e o reconhecimento facial forem bem-sucedidos, o processo de cadastro prossegue normalmente. Caso contrário, o usuário será informado sobre a falha na validação e instruído a corrigir os dados enviados.

## **Mapeamento de Entusiasmo** 📊🎮

O nível de entusiasmo do usuário em relação ao time **FURIA** é determinado através da análise de seus posts no Twitter (X). Para isso, um **scraping** é realizado nos últimos 20 tweets do usuário, nos quais uma inteligência artificial avalia o grau de engajamento com o time.

Com base nessa análise, a IA atribui um **nível de entusiasmo** ao usuário e gera uma breve descrição que resume seu nível de envolvimento com o time **FURIA**.
