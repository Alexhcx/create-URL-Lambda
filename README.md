# Create URL Lambda - Projeto Rocketseat

## Descrição

Este projeto Lambda gera URLs curtas e as armazena no S3, juntamente com a URL original e a data de expiração. Faz parte do curso gratuito de Java da Rocketseat, que aborda o desenvolvimento de uma aplicação serverless de encurtamento de URLs usando AWS. [1]

## Funcionalidade

O Lambda recebe a URL original e a data de expiração como entrada. [4] Ele gera um código de URL curta aleatório, cria um objeto JSON com os dados da URL e armazena esse objeto em um bucket S3. [4]

## Detalhes Técnicos

* Utiliza AWS Lambda e S3. [4]
* O código-fonte está disponível no GitHub. [5]

## Instruções de Uso

**Pré-requisitos:** Uma conta AWS, Java JDK instalado.

**Deploy:**

1.  Faça o download do código-fonte do projeto no GitHub. [5]
2.  Utilize o Serverless Framework para fazer o deploy do Lambda na AWS.

**Testes:**

1.  **Localmente:** Utilize um ambiente de desenvolvimento Java para executar o código e simular requisições.
2.  **Na AWS:** Utilize o console da AWS Lambda para invocar o Lambda com diferentes URLs e datas de expiração.

## Informações Adicionais

Este projeto faz parte de um sistema de encurtamento de URLs que também inclui um Lambda para redirecionar URLs curtas. [1]

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests.

## Licença

Este projeto é licenciado sob a licença MIT.
