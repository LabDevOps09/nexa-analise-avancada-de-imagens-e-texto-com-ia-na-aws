# Detector de Celebridades com AWS Rekognition

Este projeto utiliza o **AWS Rekognition** para identificar celebridades em imagens enviadas ao Amazon S3. O objetivo deste projeto é aplicar os conhecimentos adquiridos sobre serviços da AWS, especificamente o Rekognition, para realizar a detecção de celebridades com alta precisão.

## Visão Geral do Projeto

Neste repositório, você encontrará o código desenvolvido para detectar celebridades em imagens. O projeto envolve:

1. Subir imagens para o **Amazon S3**.
2. Utilizar o serviço **AWS Rekognition** para identificar as celebridades nas imagens.
3. Exibir os resultados, incluindo o nome da celebridade e a confiança da detecção.

## Processo de Desenvolvimento

### 1. **Subida da Imagem para o S3**

A primeira etapa consiste em carregar a imagem para o S3, onde ela ficará disponível para a análise pelo **Rekognition**.

### 2. **Uso do AWS Rekognition**

Utilizamos o **Rekognition** para detectar celebridades nas imagens. O serviço fornece uma lista de celebridades reconhecidas, com o percentual de confiança para cada identificação.

### 3. **Exibição de Resultados**

Após a análise, o sistema exibe o nome das celebridades detectadas e a confiança associada à detecção. Em caso de falha, uma mensagem informando que nenhuma celebridade foi encontrada é exibida.

## Como Usar

1. **Configuração da AWS**: Antes de começar, é necessário configurar as credenciais da AWS utilizando o comando `aws configure` ou configurando diretamente no código.
   
2. **Instalação de Dependências**: O projeto utiliza a biblioteca `boto3` para interagir com a AWS. Instale as dependências com o comando:

    ```bash
    pip install boto3
    ```

3. **Execução**: Para rodar o projeto, basta chamar a função principal que realiza o upload da imagem para o S3 e executa a detecção de celebridades:

    ```bash
    python detect_celebrities.py
    ```

4. **Resultados**: O sistema imprimirá as celebridades detectadas ou informará se nenhuma celebridade foi encontrada na imagem.

## Prints do Projeto

Aqui estão alguns prints do processo de execução e dos resultados da detecção:

1. **Subida da Imagem para o S3**:


![bbc](https://github.com/user-attachments/assets/dbdf29c6-24bd-4795-98a6-cbd60ddfbade)


2. **Resultado da Detecção de Celebridades**:

![bbc-resultado](https://github.com/user-attachments/assets/d8d4dae9-51ba-409f-b465-c5440f22ad8f)


## Insights Aprendidos

- **AWS Rekognition** é uma ferramenta poderosa para análise de imagens, com detecção rápida e eficiente de celebridades.
- A precisão da detecção é alta, mas depende da qualidade da imagem e da visibilidade das celebridades.
- A integração com o **Amazon S3** permite um fluxo de trabalho escalável e eficiente para armazenar e processar imagens.

## Possíveis Melhorias

- **Adicionar detecção de emoções**: Além das celebridades, seria interessante expandir o projeto para detectar emoções nas faces das pessoas nas imagens.
- **Detecção em tempo real**: A detecção pode ser otimizada para analisar vídeos em tempo real.
- **Outras categorias de objetos**: O Rekognition também pode ser usado para detectar outros objetos e atividades nas imagens, o que pode ser integrado a este projeto.

## Conclusão

Este projeto demonstrou como utilizar o **AWS Rekognition** para detectar celebridades em imagens. Ele mostra a versatilidade da AWS em processar imagens de forma eficiente e com alta precisão. O projeto é facilmente escalável para outros tipos de análise de imagem.

