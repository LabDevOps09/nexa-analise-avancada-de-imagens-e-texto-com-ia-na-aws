# Validação de CNH com AWS Textract

## **Descrição**
Este projeto extrai e valida dados de imagens de CNHs (Carteiras Nacionais de Habilitação) usando o AWS Textract. O objetivo é garantir que campos obrigatórios, como nome, data de nascimento e número de registro, estejam presentes e formatados corretamente.

---

## **Tecnologias Utilizadas**
- Python 3.13
- boto3
- boto3-stubs com Textract
- JMESPath

---

## **Configuração Inicial**
1. **Configurar dependências:**

   Instale as bibliotecas necessárias:
   ```bash
   pip install boto3 boto3-stubs[jmespath]
   ```

2. **Configurar credenciais AWS:**
   Certifique-se de ter uma conta AWS com permissões para o serviço Textract e configure as credenciais com o comando:
   ```bash
   aws configure
   ```

---

## **Uso do Projeto**
1. **Estrutura do Diretório:**
   ```plaintext
   cnh-ocr/
   |-- main.py
   |-- cnh_exemplo.jpg
   ```

2. **Script Principal (`main.py`)**
   ```python
   import boto3

   def extract_cnh_data(image_path):
       # Inicializar cliente Textract
       textract = boto3.client('textract')

       # Ler imagem
       with open(image_path, 'rb') as image_file:
           image_bytes = image_file.read()

       # Chamar Textract para análise
       response = textract.detect_document_text(Document={'Bytes': image_bytes})

       extracted_text = []
       for item in response['Blocks']:
           if item['BlockType'] == 'LINE':
               extracted_text.append(item['Text'])

       return extracted_text

   def validate_cnh_data(extracted_text):
       # Campos importantes para validar
       campos_obrigatorios = ["NOME", "DATA DE NASCIMENTO", "REGISTRO"]

       for campo in campos_obrigatorios:
           if not any(campo in linha.upper() for linha in extracted_text):
               print(f"Campo obrigatório não encontrado: {campo}")
               return False
       print("CNH válida!")
       return True

   if __name__ == "__main__":
       caminho_imagem = "cnh_exemplo.jpg"  # Substitua pelo caminho da imagem
       dados_extraidos = extract_cnh_data(caminho_imagem)

       if dados_extraidos:
           validate_cnh_data(dados_extraidos)
       else:
           print("Nenhum dado foi extraído.")
   ```

3. **Executar o script:**
   ```bash
   python main.py
   ```

---


