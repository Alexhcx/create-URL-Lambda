# Create URL

## Visão Geral

Este projeto consiste em uma função Lambda escrita em Java que cria URLs curtas. Ele utiliza os seguintes serviços da AWS:

* **AWS S3:** Armazena os dados das URLs, incluindo a URL original e a data de expiração, em arquivos JSON.
* **API Gateway:** Expõe um endpoint para a função Lambda, permitindo que ela seja acessada publicamente para criar novas URLs curtas.

## Descrição

A função Lambda recebe a URL original e a data de expiração como entrada no corpo da requisição. O código gera um código aleatório de 8 caracteres para a URL curta usando a classe `UUID`, cria um objeto `UrlData` contendo a URL original, o código da URL curta e a data de expiração, e armazena esses dados em um arquivo JSON no bucket do S3 `projeto-lambda-shortener-url-ale`. O nome do arquivo JSON é o código da URL curta seguido da extensão ".json".

## Explicação do Código

* **Classe App:** Implementa a interface `RequestHandler` do AWS Lambda.
    * **Método handleRequest:** Processa as requisições recebidas pela função Lambda.
        * Obtém a URL original e a data de expiração a partir do corpo da requisição.
        * Gera um código aleatório de 8 caracteres para a URL curta.
        * Cria um objeto `UrlData` com a URL original, a data de expiração e o código da URL curta.
        * Serializa o objeto `UrlData` em um JSON usando a biblioteca Jackson.
        * Constrói um objeto `PutObjectRequest` para enviar o arquivo JSON para o S3.
        * Utiliza o cliente S3 (`s3Client`) para enviar o arquivo JSON para o bucket.
        * Retorna uma resposta HTTP com o código da URL curta gerada.

* **Classe UrlData:** Representa os dados de uma URL, incluindo a URL original, a data de expiração e o código da URL curta.


## Dependências

* **AWS SDK para Java:** Permite a interação com os serviços da AWS, como S3 e Lambda.
* **Jackson:** Biblioteca para serialização e desserialização de objetos JSON.
* **Maven:** Ferramenta de gerenciamento de dependências e build do projeto.

## Exemplo de Uso

```json
{
  "originalUrl": "[https://www.exemplo.com](https://www.exemplo.com)",
  "expirationTime": 1670976000
}
```
## Observações

* A data de expiração deve ser informada em segundos (timestamp Unix).
* Este projeto foi desenvolvido como parte do Curso Gratuito de Java da Rocketseat. O certificado de participação está disponível [aqui](source 1).
* O curso abrangeu tópicos como desenvolvimento de aplicações serverless com Java e Maven, integração com AWS S3, API Gateway e Lambda, e manipulação de dados em JSON.
* O código fonte do projeto está disponível no GitHub:
    * **Redirect URL:** [https://github.com/Alexhcx/Redirect-URL-Lambda](https://github.com/Alexhcx/Redirect-URL-Lambda)
    * **Create URL:** [https://github.com/Alexhcx/create-URL-Lambda](https://github.com/Alexhcx/create-URL-Lambda)


## Informações Adicionais

As URLs curtas criadas por esse projeto serão no formato `https://{seu_endpoint_api_gateway}/{código_url_curta}`, onde `{seu_endpoint_api_gateway}` é o endpoint do API Gateway configurado para a função Lambda e `{código_url_curta}` é o código aleatório de 8 caracteres gerado pela função Lambda.
