* Atualização de estoque

** Parâmetros
- Endereço: http://api.easyfarma.me/api/v1/stocks.json
- Verbo HTTP: POST
- Tipo de dado: application/json

Nesta API, os parâmetros obrigatórios são:
- api_token: O token configurado pela drogaria, disponível na área administrativa do EasyFarma
- medicines: Um vetor (array) com a lista de produtos com o estoque atualizado.

Por sua vez, o parâmetro _medicines_ possui a estrutura:
    [
      // Primeiro produto
      { "**código de barras**":
        { "quantity": **quantidade**,
          "price": **preço**
        }
      },
      // Segundo produto
      { "**código de barras**":
        { "quantity": **quantidade**,
          "price": **preço**
        }
      }
    ]

Não existe nenhum limite no número de produtos, mas é recomendável que qualquer atualização grande de estoque seja feita em blocos de no máximo 1000 produtos.


** Exemplo
Uma farmácia está cadastrada no EasyFarma e possui o api_token a1b2c3d4e5f6g7h8.

Digamos que o atendente da farmácia vendeu duas unidades do medicamento _Exemplex_, que possui o código de barras _12341234_. O estoque desse medicamento, que era de 100 unidades, passou a ser de 98. No caso do medicamento ter o preço de R$ 12,94, o aplicativo mandaria a seguinte requisição ao EasyFarma:

    POST http://api.easyfarma.me/api/v1/stocks.json
    Content-Type: application/json
    { "api_token": "a1b2c3d4e5f6g7h8", "medicines": [{ "12341234": { "quantity": 98, "price": 12.94 }}] }



