# API Testing - [Restful-Booker](https://restful-booker.herokuapp.com/)

## Lista de Cenários Testados

### Autenticação
CT1: Gerar token de autenticação
CT2: Tentar gerar token de autenticação sem body
CT3: Tentar gerar token de autenticação sem username
CT4: Tentar gerar token de autenticação sem password
CT5: Tentar gerar token com credenciais inválidas

### Criar Reservas
CT6: Criar uma nova reserva
CT7: Criar reserva com firstname de tipo errado
CT8: Criar reserva com lastname de tipo errado
CT9: Criar reserva com totalprice de tipo errado
CT10: Criar reserva com depositpaid de tipo errado
CT11: Criar reserva com additionalneeds de tipo errado
CT12: Criar reserva com checkin de tipo errado
CT13: Criar reserva com checkout de tipo errado
CT14: Criar reserva com checkout com formato de data diferente
CT15: Criar reserva com checkin com formato de data diferente
CT16: Criar reserva com checkin maior que o checkout
CT17: Criar reserva sem totalprice
CT18: Criar reserva sem additionalneeds
CT19: Criar reserva sem checkin
CT20: Criar reserva sem depositpaid
CT21: Criar reserva sem checkout
CT22: Criar reserva sem lastname
CT23: Criar reserva sem firstname

### Filtros e Buscas
CT24: Listar todas as reservas
CT25: Buscar reservas por first e last name
CT26: Buscar reservas com names de valores inválidos
CT27: Buscar reservas com parâmetro inválido
CT28: Buscar reservas por last name
CT29: Buscar reservas por first name
CT30: Buscar reservas por data de check-in/check-out
CT31: Buscar reservas por datas inválidas
CT32: Buscar reservas por data de check-out
CT33: Buscar reservas por data de check-in
CT34: Buscar uma reserva específica
CT35: Buscar uma reserva com id inexistente
CT36: Buscar uma reserva com id inválido

### Atualizar Reservas
CT37: Atualizar reserva existente
CT38: Atualizar reserva sem firstname
CT39: Atualizar reserva sem lastname
CT40: Atualizar reserva com depositpaid de tipo errado
CT41: Atualizar reserva com additionalneeds tipo errado
CT42: Atualizar reserva com checkin depois do checkout

### Deletar Reservas
CT43: Deletar uma reserva
CT44: Deletar uma reserva com valor inválido
CT45: Deletar uma reserva com valor inexistente

## Resultados Obtidos

### Autenticação
**CT1: Gerar token de autenticação**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Token é gerado`: <font color="green">Passou</font>
  - `Token não é vazio`: <font color="green">Passou</font>

**CT2: Tentar gerar token de autenticação sem body**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Bad credentials'`: <font color="green">Passou</font>

**CT3: Tentar gerar token de autenticação sem username**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Bad credentials'`: <font color="green">Passou</font>

**CT4: Tentar gerar token de autenticação sem password**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Bad credentials'`: <font color="green">Passou</font>

**CT5: Tentar gerar token com credenciais inválidas**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Bad credentials'`: <font color="green">Passou</font>
### Gestão de Reservas
**CT6: Criar uma nova reserva**
- Status: 200 OK
- Testes:
  - `Status code é 201`: <font color="red">Falhou</font>
  - `Response tem id da reserva`: <font color="green">Passou</font>
  - `Response contém os detalhes da reserva`: <font color="green">Passou</font>

**CT7: Criar reserva com firstname de tipo errado**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Firstname expected string, got number'`: <font color="red">Falhou</font>

**CT8: Criar reserva com lastname de tipo errado**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Lastname expected string, got number'`: <font color="red">Falhou</font>

**CT9: Criar reserva com totalprice de tipo errado**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Totalprice expected number, got string'`: <font color="red">Falhou</font>

**CT10: Criar reserva com depositpaid de tipo errado**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Depositpaid expected boolean, got string'`: <font color="red">Falhou</font>

**CT11: Criar reserva com additionalneeds de tipo errado**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Additionalneeds expected string, got number'`: <font color="red">Falhou</font>

**CT12: Criar reserva com checkin de tipo errado**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Checkin expected date, got number'`: <font color="red">Falhou</font>

**CT13: Criar reserva com checkout de tipo errado**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'Checkout expected date, got string'`: <font color="red">Falhou</font>

**CT14: Criar reserva com checkout com formato de data diferente**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response contém data convertida`: <font color="green">Passou</font>

**CT15: Criar reserva com checkin com formato de data diferente**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Invalid checkin date format`: <font color="red">Falhou</font>

**CT16: Criar reserva com checkin maior que o checkout**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `O checkout acontece antes do checkin`: <font color="red">Falhou</font>

**CT17: Criar reserva sem totalprice**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'totalprice is required'`: <font color="red">Falhou</font>

**CT18: Criar reserva sem additionalneeds**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'additionalneeds is required'`: <font color="red">Falhou</font>

**CT19: Criar reserva sem checkin**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'checkin is required'`: <font color="red">Falhou</font>

**CT20: Criar reserva sem depositpaid**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'depositpaid is required'`: <font color="red">Falhou</font>

**CT21: Criar reserva sem checkout**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'checkout is required'`: <font color="red">Falhou</font>

**CT22: Criar reserva sem lastname**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'lastname is required'`: <font color="red">Falhou</font>

**CT23: Criar reserva sem firstname**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém 'firstname is required'`: <font color="red">Falhou</font>

### Filtros e Buscas
**CT24: Listar todas as reservas**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response é um array`: <font color="green">Passou</font>
  - `Todos os registros da response contêm bookingid`: <font color="green">Passou</font>

**CT25: Buscar reservas por first e last name**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response é um array`: <font color="green">Passou</font>
  - `Todos os registros da response contêm bookingid`: <font color="green">Passou</font>

**CT26: Buscar reservas com names de valores inválidos**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém as mensagens de erro para os dois parâmetros`: <font color="red">Falhou</font>

**CT27: Buscar reservas com parâmetro inválido**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>

**CT28: Buscar reservas por last name**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response é um array`: <font color="green">Passou</font>
  - `Todos os registros da response contêm bookingid`: <font color="green">Passou</font>

**CT29: Buscar reservas por first name**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response é um array`: <font color="green">Passou</font>
  - `Todos os registros da response contêm bookingid`: <font color="green">Passou</font>

**CT30: Buscar reservas por data de check-in/check-out**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response é um array`: <font color="green">Passou</font>
  - `Todos os registros da response contêm bookingid`: <font color="green">Passou</font>

**CT31: Buscar reservas por datas inválidas**
- Status: 500 Internal Server Error
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém mensagens de erro para os dois parâmetros`: <font color="red">Falhou</font>

**CT32: Buscar reservas por data de check-out**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response é um array`: <font color="green">Passou</font>
  - `Todos os registros da response contêm bookingid`: <font color="green">Passou</font>

**CT33: Buscar reservas por data de check-in**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response é um array`: <font color="green">Passou</font>
  - `Todos os registros da response contêm bookingid`: <font color="green">Passou</font>

**CT34: Buscar uma reserva específica**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response contém todos os campos esperados`: <font color="green">Passou</font>

**CT35: Buscar uma reserva com id inexistente**
- Status: 404 Not Found
- Testes:
  - `Status code é 404`: <font color="green">Passou</font>
  - `Response contém uma mensagem apropriada de erro`: <font color="green">Passou</font>

**CT36: Buscar uma reserva com id inválido**
- Status: 404 Not Found
- Testes:
  - `Status code é 404`: <font color="green">Passou</font>
  - `Response contém uma mensagem apropriada de erro`: <font color="green">Passou</font>

### Atualizar Reservas
**CT37: Atualizar reserva existente**
- Status: 200 OK
- Testes:
  - `Status code é 200`: <font color="green">Passou</font>
  - `Response contém os dados atualizados`: <font color="green">Passou</font>

**CT38: Atualizar reserva sem firstname**
- Status: 400 Bad Request
- Testes:
  - `Status code é 400`: <font color="green">Passou</font>
  - `Response contém mensagem de erro adequada`: <font color="red">Falhou</font>

**CT39: Atualizar reserva sem lastname**
- Status: 400 Bad Request
- Testes:
  - `Status code é 400`: <font color="green">Passou</font>
  - `Response contém mensagem de erro adequada`: <font color="red">Falhou</font>

**CT40: Atualizar reserva com depositpaid de tipo errado**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém mensagem de erro adequada`: <font color="red">Falhou</font>

**CT41: Atualizar reserva com additionalneeds tipo errado**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém mensagem de erro adequada`: <font color="red">Falhou</font>

**CT42: Atualizar reserva com checkin depois do checkout**
- Status: 200 OK
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém mensagem de erro adequada`: <font color="red">Falhou</font>

### Deletar Reservas
**CT43: Deletar uma reserva**
- Status: 201 Created
- Testes:
  - `Status code é 200`: <font color="red">Falhou</font>
  - `Response contém mensagem de sucesso`: <font color="red">Falhou</font>

**CT44: Deletar uma reserva com valor inválido**
- Status: 405 Method Not Allowed
- Testes:
  - `Status code é 400`: <font color="red">Falhou</font>
  - `Response contém mensagem de erro para ID Inválido`: <font color="red">Falhou</font>

**CT45: Deletar uma reserva com valor inexistente**
- Status: 405 Method Not Allowed
- Testes:
  - `Status code é 404`: <font color="red">Falhou</font>
  - `Response contém mensagem de erro para ID não encontrado`: <font color="red">Falhou</font>

## Bugs Encontrados

1. **CT2: Tentar gerar token de autenticação sem body**
   - **URL**: `https://restful-booker.herokuapp.com/auth`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
   - **Retornado**: 
     - **Status Code**: 200 OK
     - **Corpo da Resposta**: { "reason": "Bad credentials" }

2. **CT3: Tentar gerar token de autenticação sem username**
   - **URL**: `https://restful-booker.herokuapp.com/auth`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Corpo da Requisição**: { "password": "password123" }
   - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
   - **Retornado**: 
     - **Status Code**: 200 OK
     - **Corpo da Resposta**: { "reason": "Bad credentials" }

3. **CT4: Tentar gerar token de autenticação sem password**
   - **URL**: `https://restful-booker.herokuapp.com/auth`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Corpo da Requisição**: { "username": "admin" }
   - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
   - **Retornado**: 
     - **Status Code**: 200 OK
     - **Corpo da Resposta**: { "reason": "Bad credentials" }

4. **CT5: Tentar gerar token com credenciais inválidas**
   - **URL**: `https://restful-booker.herokuapp.com/auth`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Corpo da Requisição**: { "username": "invalid", "password": "invalid" }
   - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
   - **Retornado**: 
     - **Status Code**: 200 OK
     - **Corpo da Resposta**: { "reason": "Bad credentials" }

5. **CT6: Criar uma nova reserva**
   - **URL**: `https://restful-booker.herokuapp.com/booking`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Corpo da Requisição**: 
     ```json
     {
       "firstname": "Jotaro",
       "lastname": "Kujo",
       "totalprice": 123,
       "depositpaid": true,
       "bookingdates": {
         "checkin": "2023-01-01",
         "checkout": "2023-01-02"
       },
       "additionalneeds": "Breakfast"
     }
     ```
   - **Esperado**: Retornar `201 Created` com os detalhes da reserva.
   - **Retornado**: 
     - **Status Code**: 200 OK
     - **Corpo da Resposta**: 
       ```json
       {
         "bookingid": 1,
         "booking": {
           "firstname": "Jotaro",
           "lastname": "Kujo",
           "totalprice": 123,
           "depositpaid": true,
           "bookingdates": {
             "checkin": "2023-01-01",
             "checkout": "2023-01-02"
           },
           "additionalneeds": "Breakfast"
         }
       }
       ```

6. **CT7: Criar reserva com firstname de tipo errado**
   - **URL**: `https://restful-booker.herokuapp.com/booking`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Corpo da Requisição**: 
     ```json
     {
       "firstname": 123,
       "lastname": "Kujo",
       "totalprice": 123,
       "depositpaid": true,
       "bookingdates": {
         "checkin": "2023-01-01",
         "checkout": "2023-01-02"
       },
       "additionalneeds": "Breakfast"
     }
     ```
   - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
   - **Retornado**: 
     - **Status Code**: 500 Internal Server Error
     - **Corpo da Resposta**: { "message": "Internal Server Error" }

7. **CT8: Criar reserva com lastname de tipo errado**
   - **URL**: `https://restful-booker.herokuapp.com/booking`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Corpo da Requisição**: 
     ```json
     {
       "firstname": "Jotaro",
       "lastname": 123,
       "totalprice": 123,
       "depositpaid": true,
       "bookingdates": {
         "checkin": "2023-01-01",
         "checkout": "2023-01-02"
       },
       "additionalneeds": "Breakfast"
     }
     ```
   - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
   - **Retornado**: 
     - **Status Code**: 500 Internal Server Error
     - **Corpo da Resposta**: { "message": "Internal Server Error" }

8. **CT9: Criar reserva com totalprice de tipo errado**
   - **URL**: `https://restful-booker.herokuapp.com/booking`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Corpo da Requisição**: 
     ```json
     {
       "firstname": "Jotaro",
       "lastname": "Kujo",
       "totalprice": "123",
       "depositpaid": true,
       "bookingdates": {
         "checkin": "2023-01-01",
         "checkout": "2023-01-02"
       },
       "additionalneeds": "Breakfast"
     }
     ```
   - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
   - **Retornado**: 
     - **Status Code**: 200 OK
     - **Corpo da Resposta**: 
       ```json
       {
         "bookingid": 1,
         "booking": {
           "firstname": "Jotaro",
           "lastname": "Kujo",
           "totalprice": "123",
           "depositpaid": true,
           "bookingdates": {
             "checkin": "2023-01-01",
             "checkout": "2023-01-02"
           },
           "additionalneeds": "Breakfast"
         }
       }
       ```

9. **CT10: Criar reserva com depositpaid de tipo errado**
   - **URL**: `https://restful-booker.herokuapp.com/booking`
   - **Método HTTP**: POST
   - **Cabeçalhos de Requisição**: `Content-Type: application/json`
   - **Corpo da Requisição**: 
     ```json
     {
       "firstname": "Jotaro",
       "lastname": "Kujo",
       "totalprice": 123,
       "depositpaid": "true",
       "bookingdates": {
         "checkin": "2023-01-01",
         "checkout": "2023-01-02"
       },
       "additionalneeds": "Breakfast"
     }
     ```
   - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
   - **Retornado**: 
     - **Status Code**: 200 OK
     - **Corpo da Resposta**: 
       ```json
       {
         "bookingid": 1,
         "booking": {
           "firstname": "Jotaro",
           "lastname": "Kujo",
           "totalprice": 123,
           "depositpaid": "true",
           "bookingdates": {
             "checkin": "2023-01-01",
             "checkout": "2023-01-02"
           },
           "additionalneeds": "Breakfast"
         }
       }
       ```
## Bugs Encontrados

10. **CT11: Criar reserva com additionalneeds de tipo errado**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": 123
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "bookingid": 1,
          "booking": {
            "firstname": "Jotaro",
            "lastname": "Kujo",
            "totalprice": 123,
            "depositpaid": true,
            "bookingdates": {
              "checkin": "2023-01-01",
              "checkout": "2023-01-02"
            },
            "additionalneeds": 123
          }
        }
        ```

11. **CT12: Criar reserva com checkin de tipo errado**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": 123,
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "bookingid": 1,
          "booking": {
            "firstname": "Jotaro",
            "lastname": "Kujo",
            "totalprice": 123,
            "depositpaid": true,
            "bookingdates": {
              "checkin": 123,
              "checkout": "2023-01-02"
            },
            "additionalneeds": "Breakfast"
          }
        }
        ```

12. **CT13: Criar reserva com checkout de tipo errado**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": 123
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "bookingid": 1,
          "booking": {
            "firstname": "Jotaro",
            "lastname": "Kujo",
            "totalprice": 123,
            "depositpaid": true,
            "bookingdates": {
              "checkin": "2023-01-01",
              "checkout": 123
            },
            "additionalneeds": "Breakfast"
          }
        }
        ```

13. **CT15: Criar reserva com checkin com formato de data diferente**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023/01/01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "bookingid": 1,
          "booking": {
            "firstname": "Jotaro",
            "lastname": "Kujo",
            "totalprice": 123,
            "depositpaid": true,
            "bookingdates": {
              "checkin": "2023/01/01",
              "checkout": "2023-01-02"
            },
            "additionalneeds": "Breakfast"
          }
        }
        ```

14. **CT16: Criar reserva com checkin maior que o checkout**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-02",
          "checkout": "2023-01-01"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "bookingid": 1,
          "booking": {
            "firstname": "Jotaro",
            "lastname": "Kujo",
            "totalprice": 123,
            "depositpaid": true,
            "bookingdates": {
              "checkin": "2023-01-02",
              "checkout": "2023-01-01"
            },
            "additionalneeds": "Breakfast"
          }
        }
        ```

15. **CT17: Criar reserva sem totalprice**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 500 Internal Server Error
      - **Corpo da Resposta**: { "message": "Internal Server Error" }

16. **CT18: Criar reserva sem additionalneeds**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        }
      }
      ```
    - **Esperado**: Retornar `201 Created` com os detalhes da reserva.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "bookingid": 1,
          "booking": {
            "firstname": "Jotaro",
            "lastname": "Kujo",
            "totalprice": 123,
            "depositpaid": true,
            "bookingdates": {
              "checkin": "2023-01-01",
              "checkout": "2023-01-02"
            }
          }
        }
        ```
## Bugs Encontrados

17. **CT19: Criar reserva sem checkin**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 500 Internal Server Error
      - **Corpo da Resposta**: { "message": "Internal Server Error" }

18. **CT20: Criar reserva sem depositpaid**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 500 Internal Server Error
      - **Corpo da Resposta**: { "message": "Internal Server Error" }

19. **CT21: Criar reserva sem checkout**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 500 Internal Server Error
      - **Corpo da Resposta**: { "message": "Internal Server Error" }

20. **CT22: Criar reserva sem lastname**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 500 Internal Server Error
      - **Corpo da Resposta**: { "message": "Internal Server Error" }

21. **CT23: Criar reserva sem firstname**
    - **URL**: `https://restful-booker.herokuapp.com/booking`
    - **Método HTTP**: POST
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 500 Internal Server Error
      - **Corpo da Resposta**: { "message": "Internal Server Error" }

22. **CT26: Buscar reservas com names de valores inválidos**
    - **URL**: `https://restful-booker.herokuapp.com/booking?firstname=123&lastname=456`
    - **Método HTTP**: GET
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: []

23. **CT31: Buscar reservas por datas inválidas**
    - **URL**: `https://restful-booker.herokuapp.com/booking?checkin=123&checkout=456`
    - **Método HTTP**: GET
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 500 Internal Server Error
      - **Corpo da Resposta**: { "message": "Internal Server Error" }

24. **CT38: Atualizar reserva sem firstname**
    - **URL**: `https://restful-booker.herokuapp.com/booking/1`
    - **Método HTTP**: PUT
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 400 Bad Request
      - **Corpo da Resposta**: { "message": "Bad Request" }

25. **CT39: Atualizar reserva sem lastname**
    - **URL**: `https://restful-booker.herokuapp.com/booking/1`
    - **Método HTTP**: PUT
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 400 Bad Request
      - **Corpo da Resposta**: { "message": "Bad Request" }

## Bugs Encontrados

26. **CT40: Atualizar reserva com depositpaid de tipo errado**
    - **URL**: `https://restful-booker.herokuapp.com/booking/1`
    - **Método HTTP**: PUT
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": "true",
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "firstname": "Jotaro",
          "lastname": "Kujo",
          "totalprice": 123,
          "depositpaid": "true",
          "bookingdates": {
            "checkin": "2023-01-01",
            "checkout": "2023-01-02"
          },
          "additionalneeds": "Breakfast"
        }
        ```

27. **CT41: Atualizar reserva com additionalneeds de tipo errado**
    - **URL**: `https://restful-booker.herokuapp.com/booking/1`
    - **Método HTTP**: PUT
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-01",
          "checkout": "2023-01-02"
        },
        "additionalneeds": 123
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "firstname": "Jotaro",
          "lastname": "Kujo",
          "totalprice": 123,
          "depositpaid": true,
          "bookingdates": {
            "checkin": "2023-01-01",
            "checkout": "2023-01-02"
          },
          "additionalneeds": 123
        }
        ```

28. **CT42: Atualizar reserva com checkin depois do checkout**
    - **URL**: `https://restful-booker.herokuapp.com/booking/1`
    - **Método HTTP**: PUT
    - **Cabeçalhos de Requisição**: `Content-Type: application/json`
    - **Corpo da Requisição**: 
      ```json
      {
        "firstname": "Jotaro",
        "lastname": "Kujo",
        "totalprice": 123,
        "depositpaid": true,
        "bookingdates": {
          "checkin": "2023-01-02",
          "checkout": "2023-01-01"
        },
        "additionalneeds": "Breakfast"
      }
      ```
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 200 OK
      - **Corpo da Resposta**: 
        ```json
        {
          "firstname": "Jotaro",
          "lastname": "Kujo",
          "totalprice": 123,
          "depositpaid": true,
          "bookingdates": {
            "checkin": "2023-01-02",
            "checkout": "2023-01-01"
          },
          "additionalneeds": "Breakfast"
        }
        ```

29. **CT43: Deletar uma reserva**
    - **URL**: `https://restful-booker.herokuapp.com/booking/1`
    - **Método HTTP**: DELETE
    - **Esperado**: Retornar `200 OK` com uma mensagem de sucesso.
    - **Retornado**: 
      - **Status Code**: 201 Created

30. **CT44: Deletar uma reserva com valor inválido**
    - **URL**: `https://restful-booker.herokuapp.com/booking/abc`
    - **Método HTTP**: DELETE
    - **Esperado**: Retornar `400 Bad Request` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 405 Method Not Allowed

31. **CT45: Deletar uma reserva com valor inexistente**
    - **URL**: `https://restful-booker.herokuapp.com/booking/9999`
    - **Método HTTP**: DELETE
    - **Esperado**: Retornar `404 Not Found` com uma mensagem de erro adequada.
    - **Retornado**: 
      - **Status Code**: 405 Method Not Allowed
