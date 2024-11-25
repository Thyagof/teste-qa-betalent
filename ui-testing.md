# Plano de Testes - UI Testing ([Sauce Demo](https://www.saucedemo.com/))

## 1. Objetivo
Realizar a validação completa da plataforma Sauce Demo, cobrindo os principais fluxos da aplicação antes do lançamento em produção.

---

## 2. Plano de Testes

### 2.1 Estratégia de teste
O objetivo desta estratégia de testes é garantir que todas as funcionalidades do site Sauce Demo sejam testadas de forma abrangente. Serão aplicados testes funcionais e testes de usabilidade.

Os casos de teste deste projeto serão escritos utilizando a linguagem Gherkin, seguindo a abordagem Behavior-Driven Development (BDD). Essa escolha visa garantir a padronização e a facilidade de entendimento para todos os envolvidos no processo de desenvolvimento e teste.

### 2.2 Cenários de Teste
    Feature: Login

    CT01: Acesso a página de Login
        Given que o usuário esteja no navegador
        When o usuário preencher a barra de navegação com o "https://www.saucedemo.com/"
        And o usuário pressionar a tecla "Enter"
        Then o sistema exibe a página de login do site

    CT02: Login com credenciais válidas "standard_user"
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário preencher o campo username com "standard_user"
        And o usuário preencher o campo password com "secret_sauce"
        And o usuário clicar no botão "Login"
        Then o sistema redireciona para a página de principal "https://www.saucedemo.com/inventory.html"

    CT03: Tentativa de login com credenciais de um usuário bloqueado "locked_out_user"
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário preencher o campo username com "locked_out_user"
        And o usuário preencher o campo password com "secret_sauce"
        And o usuário clicar no botão "Login"
        Then o sistema exibe a mensagem de erro "Epic sadface: Sorry, this user has been locked out" entre os campos do formulário e o botão

    CT04: Login com credenciais com outro tipo de usuário
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário preencher o campo username com "performance_glitch_user"
        And o usuário preencher o campo password com "secret_sauce"
        And o usuário clicar no botão "Login"
        Then o sistema redireciona para a página de principal "https://www.saucedemo.com/inventory.html"

    CT05: Tentativa de login com username válido e password inválida
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário preencher o campo username com "error_user"
        And o usuário preencher o campo password com "invalid_password"
        And o usuário clicar no botão "Login"
        Then o sistema exibe a mensagem de erro "Epic sadface: Username and password do not match any user in this service" entre os campos do formulário e o botão

    CT06: Tentativa de login com username inválido e password válida
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário preencher o campo username com "test_user"
        And o usuário preencher o campo password com "secret_sauce"
        And o usuário clicar no botão "Login"
        Then o sistema exibe a mensagem de erro "Epic sadface: Username and password do not match any user in this service" entre os campos do formulário e o botão

    CT07: Tentativa de login com username e password inválida
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário preencher o campo username com "invalid_user"
        And o usuário preencher o campo password com "invalid_sauce"
        And o usuário clicar no botão "Login"
        Then o sistema exibe a mensagem de erro "Epic sadface: Username and password do not match any user in this service" entre os campos do formulário e o botão

    CT08: Tentativa de login com campos vazios
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário clicar no botão "Login"
        Then o sistema exibe a mensagem de erro "Epic sadface: Username is required" entre os campos do formulário e o botão

    CT09: Tentativa de login com campos Username vazio e campo Password preenchido
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário preencher o campo Password com "secret_sauce"
        And o usuário clicar no botão "Login"
        Then o sistema exibe a mensagem de erro "Epic sadface: Username is required" entre os campos do formulário e o botão

    CT10: Tentativa de login com campos Password vazio e campo Username preenchido
        Given que o usuário esteja na página "https://www.saucedemo.com/"
        When o usuário preencher o campo Username com "problem_user"
        And o usuário clicar no botão "Login"
        Then o sistema exibe a mensagem de erro "Epic sadface: Username is required" entre os campos do formulário e o botão
    
---
    Feature: Produtos
    
    CT11: Validação da exibição dos produtos
        Given que o usuário tenha feito login com sucesso
        When o usuário estiver na página principal "https://www.saucedemo.com/inventory.html"
        Then a lista de produtos deve ser exibida respeitando a ordem alfabética por nome
        And cada produto deve mostrar nome, texto, preço, imagem e ter um botão com texto "Add to cart"

    CT12: Validação do filtro "Name (A to Z)"
        Given que o usuário esteja na página principal "https://www.saucedemo.com/inventory.html"
        When o usuário selecionar no filtro "Name (Z to A)"
        And o usuário selecionar no filtro "Name (A to Z)"
        Then a lista de produtos deve ser exibida respeitando a ordem alfabética por nome

    CT13: Validação do filtro "Name (Z to A)"
        Given que o usuário esteja na página "https://www.saucedemo.com/inventory.html"
        When o usuário selecionar no filtro "Name (Z to A)"
        Then a lista de produtos deve ser exibida respeitando a ordem alfabética inversa por nome

    CT14: Validação do filtro "Price (low to high)"
        Given que o usuário esteja na página "https://www.saucedemo.com/inventory.html"
        When o usuário selecionar no filtro "Price (low to high)"
        Then a lista de produtos deve ser exibida respeitando a ordem crescente de preço

    CT15: Validação do filtro "Price (high to low)"
        Given que o usuário esteja na página "https://www.saucedemo.com/inventory.html"
        When o usuário selecionar no filtro "Price (high to low)"
        Then a lista de produtos deve ser exibida respeitando a ordem decrescente de preço

    CT16: Validação do redirecionamento da página pelo Botão "Products" no menu hambúrguer
        Given que o usuário esteja na página "https://www.saucedemo.com/cart.html"
        When o usuário clicar no menu hamburguer
        And o usuário clicar no botão Products
        Then o usuário deve ser redirecionado para a página "https://www.saucedemo.com/inventory.html"

    CT17: Validação da página de item
        Given que o usuário esteja na página "https://www.saucedemo.com/inventory.html"
        When o usuário clicar no nome do primeiro item da página
        Then o usuário deve ser redirecionado para a página
        And o sistema deve mostrar nome do item, texto do item, preço do item, imagem do item e ter um botão com texto "Add to cart"

---
    Feature: Carrinho

    CT18: Redirecionamento da página pelo botão do carrinho
        Given que o usuário esteja na página "https://www.saucedemo.com/inventory.html"
        When o usuário clicar no botão com ícone do carrinho
        Then o usuário deve ser redirecionado para a página "https://www.saucedemo.com/cart.html"

    CT19: Atualização do ícone do carrinho ao adicionar item ao carrinho
        Given que o usuário esteja na página "https://www.saucedemo.com/inventory.html"
        When o usuário clicar no botão "Add to cart" do primeiro item da lista
        Then o ícone do carrinho deve mudar passando a exibir uma bolinha vermelha com o número 1

    CT20: Atualização do ícone do carrinho ao remover item ao carrinho
        Given que o usuário esteja com um produto no carrinho 
        When o usuário clicar no botão "Remove" do item da lista que ele adicionou ao carrinho
        Then o ícone do carrinho deve mudar, passando a exibir apenas o carrinho

    CT21: Atualização do ícone do carrinho ao adicionar múltiplos itens ao carrinho
        Given que o usuário esteja na página "https://www.saucedemo.com/inventory.html"
        When o usuário clicar no botão "Add to cart" do primeiro item da lista
        And o usuário clicar no botão "Add to cart" do último item da lista
        Then o ícone do carrinho deve mudar passando a exibir uma bolinha vermelha com o número 2

    CT22: Exibição de item no carrinho
        Given que o usuário esteja na página "https://www.saucedemo.com/inventory.html"
        When o usuário clicar no botão "Add to cart" do primeiro item da lista
        And o usuário clicar no ícone do carrinho
        Then o sistema deve redirecionar para a página "https://www.saucedemo.com/cart.html"
        And o sistema deve exibir o item que foi adicionado ao carrinho, com nome, texto, preço e quantidade e imagem

    CT23: Remoção de item do carrinho
        Given que o usuário tenha adicionado um item ao carrinho
        When o usuário acessar o carrinho
        And o usuário clicar no botão "Remove" do item adicionado
        Then o item deve ser devidamente removido do carrinho
    
    CT24: Remoção de multiplos itens do carrinho
        Given que o usuário tenha adicionado três itens ao carrinho
        When o usuário acessar o carrinho
        And o usuário clicar no botão "Remove" dos 3 itens adicionados
        Then os itens devem ser devidamente removidos do carrinho
        
    CT25: Redirecionamento do botão "Continue Shopping"
        Given que o usuário esteja na página "https://www.saucedemo.com/cart.html"
        When o usuário clicar no botão "Continue Shopping"
        Then deve ser redirecionado para a página "https://www.saucedemo.com/inventory.html"

---

    Feature: Checkout

    CT26: Acesso à página de Checkout
        Given que o usuário esteja com um produto no carrinho
        When o usuário clicar no botão "Checkout"
        Then deve ser redirecionado para a página "https://www.saucedemo.com/checkout-step-one.html"

    CT27: Validação do botão de Checkout desabilitado sem produtos no carrinho
        Given que o usuário esteja na página "https://www.saucedemo.com/cart.html"
        When o usuário não tiver produtos no carrinho
        Then o botão de checkout deve estar desabilitado

    CT28: Preenchimento das informações de Checkout
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher os campos com dados válidos 
        And o usuário clicar no botão "Continue"
        Then deve ser redirecionado para a página "https://www.saucedemo.com/checkout-step-two.html"

    CT29: Prosseguimento do Checkout sem preencher os dados
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: First Name is required" logo abaixo dos campos

    CT30: Prosseguimento do Checkout preenchendo somente o campo First Name
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher o campo "First Name" com "Jotaro"
        And o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: Last Name is required" logo abaixo dos campos

    CT31: Prosseguimento do Checkout preenchendo somente o campo Last Name
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher o campo "Last Name" com "Kujo"
        And o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: First Name is required" logo abaixo dos campos
    
    CT32: Prosseguimento do Checkout preenchendo somente o campo Zip/Postal Code
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher o campo "Zip/Postal Code" com "123123123"
        And o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: First Name is required" logo abaixo dos campos
    
    CT33: Prosseguimento do Checkout sem preencher somente o campo Zip/Postal Code
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher o campo "First Name" com "Jotaro"
        And o usuário preencher o campo "Last Name" com "Kujo"
        And o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: Postal Code is required" logo abaixo dos campos
    
    CT34: Preenchimento do campo "First Name" do Checkout com dados inválidos
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher o campo "First Name" com números aleatórios
        And o usuário preencher o campo "Last Name" com "Kujo"
        And o usuário preencher o campo "Zip/Postal Code" com "123123123"
        And o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: Invalid First Name" logo abaixo dos campos

    CT35: Preenchimento do campo "Last Name" do Checkout com dados inválidos
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher o campo "First Name" com "Jotaro"
        And o usuário preencher o campo "Last Name" com números aleatórios
        And o usuário preencher o campo "Zip/Postal Code" com "123123123"
        And o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: Invalid Last Name" logo abaixo dos campos
    
    CT36: Preenchimento do campo "Zip/Postal Code" do Checkout com dados inválidos
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher o campo "First Name" com "Jotaro"
        And o usuário preencher o campo "Last Name" com "Kujo"
        And o usuário preencher o campo "Zip/Postal Code" com letras aleatórias
        And o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: Invalid Last Name" logo abaixo dos campos

    CT37: Preenchimento dos campos do Checkout com dados inválidos
        Given que o usuário acessou o Checkout com um produto no carrinho
        When o usuário preencher todos os campos do Checkout com dados inválidos
        And o usuário clicar no botão "Continue"
        Then o sistema deve exibir o aviso "Error: Invalid First Name" logo abaixo dos campos
    
    CT38: Redirecionamento do botão "Cancel" da primeira página do Checkout para o Carrinho
        Given que o usuário esteja na página de preenchimento de informações do Checkout "https://www.saucedemo.com/checkout-step-one.html"
        When o usuário clicar no botão "Cancel"
        Then deve ser redirecionado para a página do Carrinho "https://www.saucedemo.com/cart.html"
    
    CT39: Exibição dos dados da primeira página do Checkout sendo exibidos na segunda página do Checkout
        Given que o usuário preencheu o formulário do Checkout "https://www.saucedemo.com/checkout-step-one.html" com dados válidos
        When o usuário clicar no botão "Continue"
        Then deve ser redirecionado para a página de continuação do Checkout "https://www.saucedemo.com/checkout-step-two.html"
        And o sistema deve listar os dados do cliente que foram preenchidos no formulário do Checkout
    
    CT40: Finalização da compra
        Given que o usuário esteja na segunda página do Checkout
        When o usuário clicar no botão Finish
        Then deve ser redirecionado para a página final do Checkout "https://www.saucedemo.com/checkout-complete.html"
        And o sistema deve exibir o aviso "Thank you for your order!"

    CT41: Validação dos textos na página de finalização da compra
        Given que o usuário completou a compra
        When o usuário estiver na página de finalização de compra 
        Then o texto "Thank you for your order!" deve ser exibido 
        And o texto "Your order has been dispatched, and will arrive just as fast as the pony can get there!" deve ser exibido 
        And o botão "Back Home" deve estar

    CT42: Redirecionamento do botão "Back Home"
        Given que o usuário esteja na página de finalização de compra "https://www.saucedemo.com/checkout-complete.html"
        When o usuário clicar no botão "Back Home"
        Then deve ser redirecionado para a página principal "https://www.saucedemo.com/inventory.html"
    
    Feature: Logout

    CT43: Logout a partir da página principal
        Given que o usuário esteja na página principal "https://www.saucedemo.com/inventory.html"
        When o usuário clicar no menu hambúrguer
        And o usuário clicar no botão Logout
        Then deve ser redirecionado para a página de login "https://www.saucedemo.com/"

    CT44: Logout a partir da página principal
        Given que o usuário esteja na segunda página de checkout "https://www.saucedemo.com/checkout-step-two.html"
        When o usuário clicar no menu hambúrguer
        And o usuário clicar no botão Logout
        Then deve ser redirecionado para a página de login "https://www.saucedemo.com/"
    
    CT45: Logout a partir do carrinho
        Given que o usuário esteja na carrinho "https://www.saucedemo.com/cart.html"
        When o usuário clicar no menu hambúrguer
        And o usuário clicar no botão Logout
        Then deve ser redirecionado para a página de login "https://www.saucedemo.com/"

    Testes de Responsividade

    CT46: Verificação do layout da página de login em dispositivos móveis 
        Given que o usuário esteja utilizando um smartphone 
        When o usuário acessar a página "https://www.saucedemo.com/" 
        Then o layout deve se ajustar corretamente à tela do dispositivo 
        And todos os elementos devem ser visíveis e funcionais 
    
    CT47: Verificação do layout da página de login em tablets 
        Given que o usuário esteja utilizando um tablet 
        When o usuário acessar a página "https://www.saucedemo.com/" 
        Then o layout deve se ajustar corretamente à tela do dispositivo 
        And todos os elementos devem ser visíveis e funcionais 

    CT48: Verificação do layout da página de login em desktops 
        Given que o usuário esteja utilizando um desktop 
        When o usuário acessar a página "https://www.saucedemo.com/" 
        Then o layout deve se ajustar corretamente à tela do dispositivo 
        And todos os elementos devem ser visíveis e funcionais 

    CT49: Verificação do layout da página de produtos em dispositivos móveis 
        Given que o usuário esteja utilizando um smartphone 
        When o usuário acessar a página "https://www.saucedemo.com/inventory" 
        Then o layout deve se ajustar corretamente à tela do dispositivo 
        And todos os elementos devem ser visíveis e funcionais 
    
    CT50: Verificação do layout da página de produtos em tablets 
        Given que o usuário esteja utilizando um tablet 
        When o usuário acessar a página "https://www.saucedemo.com/inventory" 
        Then o layout deve se ajustar corretamente à tela do dispositivo 
        And todos os elementos devem ser visíveis e funcionais 

    CT51: Verificação do layout da página de produtos em desktops 
        Given que o usuário esteja utilizando um desktop 
        When o usuário acessar a página "https://www.saucedemo.com/inventory" 
        Then o layout deve se ajustar corretamente à tela do dispositivo 
        And todos os elementos devem ser visíveis e funcionais 

---

## 3. Resultados dos Testes
| Cenário de Teste                          | Descrição                                      | Evidência da Execução | Status (Passou/Falhou) | Data de Execução |
|---------------------------------------------------|------------------------------------------------|--------------------|------------------------|------------------|
| **CT01**: Acesso a página de Login                    | Verificar se a página de login é exibida       | [Evidência](images-ui/ct01.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT02**: Login com credenciais válidas "standard_user"| Verificar login com usuário válido             | [Evidência](images-ui/ct02.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT03**: Tentativa de login com credenciais de um usuário bloqueado "locked_out_user" | Verificar login com usuário bloqueado | [Evidência](images-ui/ct03.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT04**: Login com credenciais com outro tipo de usuário | Verificar login com usuário de performance glitch | [Evidência](images-ui/ct04.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT05**: Tentativa de login com username válido e password inválida | Verificar login com username válido e password inválida | [Evidência](images-ui/ct05.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT06**: Tentativa de login com username inválido e password válida | Verificar login com username inválido e password válida | [Evidência](images-ui/ct06.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT07**: Tentativa de login com username e password inválida | Verificar login com username e password inválida | [Evidência](images-ui/ct07.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT08**: Tentativa de login com campos vazios | Verificar login com campos vazios | [Evidência](images-ui/ct08.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT09**: Tentativa de login com campos Username vazio e campo Password preenchido | Verificar login com username vazio e password preenchido | [Evidência](images-ui/ct09.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT10**: Tentativa de login com campos Password vazio e campo Username preenchido | Verificar login com password vazio e username preenchido | [Evidência](images-ui/ct10.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT11**: Validação da exibição dos produtos | Verificar exibição dos produtos na página principal | [Evidência](images-ui/ct11.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT12**: Validação do filtro "Name (A to Z)" | Verificar filtro de ordenação de produtos de A a Z | [Evidência](images-ui/ct12.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT13**: Validação do filtro "Name (Z to A)" | Verificar filtro de ordenação de produtos de Z a A | [Evidência](images-ui/ct13.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT14**: Validação do filtro "Price (low to high)" | Verificar filtro de ordenação de produtos por preço crescente | [Evidência](images-ui/ct14.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT15**: Validação do filtro "Price (high to low)" | Verificar filtro de ordenação de produtos por preço decrescente | [Evidência](images-ui/ct15.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT16**: Validação do redirecionamento da página pelo Botão "Products" no menu hambúrguer | Verificar redirecionamento pelo botão "Products" no menu hambúrguer | [Evidência](images-ui/ct16.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT17**: Validação da página de item | Verificar exibição da página de item ao clicar no nome do produto | [Evidência](images-ui/ct17.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT18**: Redirecionamento da página pelo botão do carrinho | Verificar redirecionamento pelo botão do carrinho | [Evidência](images-ui/ct18.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT19**: Atualização do ícone do carrinho ao adicionar item ao carrinho | Verificar atualização do ícone do carrinho ao adicionar item | [Evidência](images-ui/ct19.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT20**: Atualização do ícone do carrinho ao remover item ao carrinho | Verificar atualização do ícone do carrinho ao remover item | [Evidência](images-ui/ct20.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT21**: Atualização do ícone do carrinho ao adicionar múltiplos itens ao carrinho | Verificar atualização do ícone do carrinho ao adicionar múltiplos itens | [Evidência](images-ui/ct21.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT22**: Exibição de item no carrinho | Verificar exibição de item no carrinho | [Evidência](images-ui/ct22.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT23**: Remoção de item do carrinho | Verificar remoção de item do carrinho | [Evidência](images-ui/ct23.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT24**: Remoção de multiplos itens do carrinho | Verificar remoção de múltiplos itens do carrinho | [Evidência](images-ui/ct24.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT25**: Redirecionamento do botão "Continue Shopping" | Verificar redirecionamento pelo botão "Continue Shopping" | [Evidência](images-ui/ct25.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT26**: Acesso à página de Checkout | Verificar acesso à página de Checkout | [Evidência](images-ui/ct26.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT27**: Validação do botão de Checkout desabilitado sem produtos no carrinho | Verificar botão de Checkout desabilitado sem produtos no carrinho | [Evidência](images-ui/ct27.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT28**: Preenchimento das informações de Checkout | Verificar preenchimento das informações de Checkout | [Evidência](images-ui/ct28.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT29**: Prosseguimento do Checkout sem preencher os dados | Verificar prosseguimento do Checkout sem preencher os dados | [Evidência](images-ui/ct29.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT30**: Prosseguimento do Checkout preenchendo somente o campo First Name | Verificar prosseguimento do Checkout preenchendo somente o campo First Name | [Evidência](images-ui/ct30.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT31**: Prosseguimento do Checkout preenchendo somente o campo Last Name | Verificar prosseguimento do Checkout preenchendo somente o campo Last Name | [Evidência](images-ui/ct31.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT32**: Prosseguimento do Checkout preenchendo somente o campo Zip/Postal Code | Verificar prosseguimento do Checkout preenchendo somente o campo Zip/Postal Code | [Evidência](images-ui/ct32.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT33**: Prosseguimento do Checkout sem preencher somente o campo Zip/Postal Code | Verificar prosseguimento do Checkout sem preencher somente o campo Zip/Postal Code | [Evidência](images-ui/ct33.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT34**: Preenchimento do campo "First Name" do Checkout com dados inválidos | Verificar preenchimento do campo "First Name" do Checkout com dados inválidos | [Evidência](images-ui/ct34.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT35**: Preenchimento do campo "Last Name" do Checkout com dados inválidos | Verificar preenchimento do campo "Last Name" do Checkout com dados inválidos | [Evidência](images-ui/ct35.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT36**: Preenchimento do campo "Zip/Postal Code" do Checkout com dados inválidos | Verificar preenchimento do campo "Zip/Postal Code" do Checkout com dados inválidos | [Evidência](images-ui/ct36.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT37**: Preenchimento dos campos do Checkout com dados inválidos | Verificar preenchimento dos campos do Checkout com dados inválidos | [Evidência](images-ui/ct37.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT38**: Redirecionamento do botão "Cancel" da primeira página do Checkout para o Carrinho | Verificar redirecionamento pelo botão "Cancel" da primeira página do Checkout para o Carrinho | [Evidência](images-ui/ct38.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT39**: Exibição dos dados da primeira página do Checkout sendo exibidos na segunda página do Checkout | Verificar exibição dos dados da primeira página do Checkout na segunda página | [Evidência](images-ui/ct39.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT40**: Finalização da compra | Verificar finalização da compra | [Evidência](images-ui/ct40.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT41**: Validação dos textos na página de finalização da compra | Verificar textos na página de finalização da compra | [Evidência](images-ui/ct41.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT42**: Redirecionamento do botão "Back Home" | Verificar redirecionamento pelo botão "Back Home" | [Evidência](images-ui/ct42.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT43**: Logout a partir da página principal | Verificar logout a partir da página principal | [Evidência](images-ui/ct43.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT44**: Logout a partir da segunda página de checkout | Verificar logout a partir da segunda página de checkout | [Evidência](images-ui/ct44.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT45**: Logout a partir do carrinho | Verificar logout a partir da página do carrinho | [Evidência](images-ui/ct45.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT46**: Verificação do layout da página de login em dispositivos móveis | Verificar layout da página de login em dispositivos móveis | [Evidência](images-ui/ct46.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT47**: Verificação do layout da página de login em tablets | Verificar layout da página de login em tablets | [Evidência](images-ui/ct47.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT48**: Verificação do layout da página de login em desktops | Verificar layout da página de login em desktops | [Evidência](images-ui/ct48.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT49**: Verificação do layout da página de produtos em dispositivos móveis | Verificar layout da página de produtos em dispositivos móveis | [Evidência](images-ui/ct49.png) | <font color="red">Não passou</font> | 22/11/2024 |
| **CT50**: Verificação do layout da página de produtos em tablets | Verificar layout da página de produtos em tablets | [Evidência](images-ui/ct50.png) | <font color="green">Passou</font> | 22/11/2024 |
| **CT51**: Verificação do layout da página de produtos em desktops | Verificar layout da página de produtos em desktops | [Evidência](images-ui/ct51.png) | <font color="green">Passou</font> | 22/11/2024 |


---
## 4. Sugestões de Melhoria UX/UI

- **Criar uma seção de perfil para o usuário:**  
  Permitir que o usuário visualize informações do seu perfil e altere a senha. Essa funcionalidade é essencial, pois, caso o usuário tenha cadastrado uma senha incorreta, ele deve ter a possibilidade de corrigir o erro de forma autônoma.  
  Tomei como base a terceira heurística de Nielsen, *Controle e liberdade do usuário*.  

- **Alterar a cor dos botões ao passar o mouse (hover):**  
  Prover um feedback visual claro ao usuário ao interagir com os botões do sistema.  
  Isso se alinha à quinta heurística de Nielsen, *Feedback visível*.  

- **Adicionar controles de quantidade no carrinho:**  
  Incluir botões para aumentar ou diminuir a quantidade de itens no carrinho. Caso isso seja inviável por se tratar de uma regra de negócio, seria ideal remover a exibição da quantidade dos itens no carrinho, para evitar confusão.  
  Essa sugestão considera a sexta heurística de Nielsen, *Minimizar a carga de memória do usuário*.  

- **Manter consistência nos nomes das páginas:**  
  Por exemplo, a página [*Products*](https://www.saucedemo.com/inventory.html) é chamada de "inventory" na URL e de "All Items" no menu hambúrguer. Padronizar esses nomes melhora a experiência do usuário.  
  Baseado na quarta heurística de Nielsen, *Consistência e padrões*.  

- **Redirecionar o usuário ao clicar no logo:**  
  O logo "Swag Labs" deve redirecionar o usuário para a [página principal](https://www.saucedemo.com/inventory.html).  
  Essa melhoria está alinhada à sétima heurística de Nielsen, *Flexibilidade e eficiência de uso*.  

- **Remover o menu hambúrguer em telas maiores:**  
  Em dispositivos de tela grande, é recomendado substituir o menu hambúrguer por um menu visível, já que há espaço disponível. Isso economiza cliques e facilita a navegação.  
  Baseado na sexta heurística de Nielsen, *Minimizar a carga de memória do usuário*.  

- **Evidenciar o título da página atual:**  
  Tornar mais claro o título da página onde o usuário se encontra, proporcionando um feedback visual imediato.  
  Essa sugestão é fundamentada na quinta heurística de Nielsen, *Feedback visível*.  

- **Permitir fechar o menu hambúrguer ao clicar fora dele:**  
  Essa funcionalidade oferece uma interação mais intuitiva e ágil para o usuário.  
  Baseado na sétima heurística de Nielsen, *Flexibilidade e eficiência de uso*.  

- **Criar breadcrumbs no fluxo de checkout:**  
  Mostrar os passos do processo de checkout por meio de breadcrumbs, para que o usuário tenha visibilidade do status do sistema.  
  Essa recomendação se baseia na primeira heurística de Nielsen, *Visibilidade do status do sistema*.  

- **Rever a posição do botão "Continue" no checkout:**  
  Na primeira página do [Checkout](https://www.saucedemo.com/checkout-step-one.html), em telas maiores, o botão "Continue" está muito distante do formulário. Dependendo do tamanho da tela, o usuário precisa rolar a página para continuar o processo. Ajustar essa distância melhorará a usabilidade.  
  Tomei como base a oitava heurística de Nielsen, *Design estético e minimalista*.  


---

## 5. Lista de Bugs

| **Título** | **Descrição** | **Passos para Reproduzir** | **Resultado Esperado** | **Resultado Atual** | **Ambiente** | **Dispositivo - Sistema Operacional** | **Navegador** | **Evidências** |
|-----------------------------------|-------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------------------|-----------------------|--------------------------------------|-------------------|-------------------------------------|
| Compra com carrinho vazio         | O sistema permite acessar o checkout mesmo com o carrinho vazio.             | 1. Acessar o link "https://www.saucedemo.com/". <br> 2. Logar com um usuário válido. <br> 3. Acessar o carrinho sem adicionar nenhum item a ele. | O botão de checkout deve estar desabilitado.                       | O botão está habilitado mesmo com o carrinho vazio, tornando o checkout acessível.                             | Ambiente de testes    | Desktop - Windows 11                | Microsoft Edge    | [Evidência](images-ui/ct27.png) |
| Redirecionamento inconsistente do botão "Cancel" | Comportamento diferente ao clicar em "Cancel" em diferentes etapas do checkout. | 1. Acessar o link "https://www.saucedemo.com/". <br> 2. Logar com um usuário válido. <br> 3. Adicionar itens ao carrinho. <br> 4. Acessar o carrinho. <br> 5. Clicar no botão "Checkout".<br> 6. Clicar no botão "Cancel". <br> 7. Acessar o carrinho. <br> 8. Clicar no botão "Checkout". <br> 9. Preencher o formulário de Checkout com dados válidos. <br> 10. Clicar no botão "Continue". <br> 11. Clicar no botão "Cancel". | Ambos os botões devem redirecionar para a mesma página (carrinho). | A etapa 1 redireciona para o carrinho; a etapa 2, para a página principal. | Ambiente de testes    | Desktop - Windows 11                | Microsoft Edge    |  [Evidência](gifs-ui/cancel-redirect-bug.gif) |
| Seta do select do filtro de produtos não funciona | O select de filtro de produtos não abre ao clicar na seta para baixo.       | 1. Acessar o link "https://www.saucedemo.com/". <br> 2. Logar com um usuário válido. <br> 3. Clicar no ícone da seta do filtro de produtos. | O menu de filtro deve abrir ao clicar na seta para baixo.           | O menu de filtro não abre.                                               | Ambiente de testes    | Desktop - Windows 11                | Microsoft Edge    |   [Evidência](images-ui/seta-filtro-bug) |
| Avanço no checkout com informações inválidas | O sistema permite continuar no checkout mesmo com informações inválidas.    | 1. Acessar o link "https://www.saucedemo.com/". <br> 2. Logar com um usuário válido. <br> 3. Adicionar itens ao carrinho. <br> 4. Acessar o carrinho. <br> 5. Clicar no botão "Checkout". <br> 6. Inserir informações inválidas.    <br> 7. Clicar em "Continue". | O sistema deve bloquear o avanço com dados.inválidos.              | O sistema permite avançar no checkout.                                   | Ambiente de testes    | Desktop - Windows 11                | Microsoft Edge    | [Evidência](gifs-ui/invalid-info-checkout.gif) |
| Informações do checkout não sendo mostradas na segunda página do checkout | As informações do formulário de checkout não são mostradas na segunda página de checkout.    | 1. Acessar o link "https://www.saucedemo.com/". <br> 2. Logar com um usuário válido. <br> 3. Adicionar itens ao carrinho. <br> 4. Acessar o carrinho. <br> 5. Clicar no botão "Checkout". <br> 6. Inserir informações inválidas.    <br> 7. Clicar em "Continue". | O sistema deve exibir as informações do usuário.  | O sistema não exibe as informações.                                   | Ambiente de testes    | Desktop - Windows 11                | Microsoft Edge    | [Evidência](gifs-ui/checkout-info-bug.gif) |
| Nome inconsistente do botão "Products" | O botão "Products" no menu hambúrguer aparece com o texto "All Items".      | 1. Acessar o link "https://www.saucedemo.com/". <br> 2. Logar com um usuário válido. <br> 3. Clicar no menu hambúrguer.                                                         | O botão deve ter o nome consistente como "Products".               | O botão aparece como "All Items".                                        | Ambiente de testes    | Desktop - Windows 11                | Microsoft Edge    | [Evidência](images-ui/ct16.png)    |
| Imagem dos itens do carrinho não é exibida | As imagens dos itens no carrinho não aparecem.                              | 1. Acessar o link "https://www.saucedemo.com/". <br> 2. Logar com um usuário válido. <br> 3. Adicionar itens ao carrinho. <br> 4. Navegar até o carrinho.                                             | Todas as imagens dos itens devem ser exibidas.                     | As imagens não aparecem.                                                 | Ambiente de testes    | Desktop - Windows 11                | Microsoft Edge    | [Evidência](images-ui/ct22.png)    |
| Espaçamento exagerado na lista de produtos em dispositivos móveis | Espaçamento exagerado entre itens da lista em dispositivos móveis.          | 1. Acessar o link "https://www.saucedemo.com/" em um smartphone. <br> 2. Logar com um usuário válido. <br>                            | O layout deve ser otimizado para dispositivos móveis.               | Espaçamento exagerado entre os itens da lista de produtos.                                    | Ambiente de testes    | Desktop - Windows 11                | Microsoft Edge    | [Evidência](images-ui/ct49.png)    |

---

## **6. Análise de Riscos**

### **6.1 Riscos Identificados**

1. **Inconsistências de Design (UX/UI)**
   - **Descrição**: Problemas na interface do usuário (ex: falta de breadcrumbs, inconsistência de nomenclatura) podem impactar a experiência do usuário.
   - **Nível de Risco**: **Médio**
   - **Mitigação**:
     - Realizar revisões detalhadas de design com as equipes de UX/UI.
     - Implementar testes exploratórios focados em usabilidade.

2. **Falhas em Funcionalidades Críticas**
   - **Descrição**: Bugs identificados em áreas importantes como o login, carrinho e checkout podem bloquear fluxos do usuário.
   - **Nível de Risco**: **Crítico**
   - **Mitigação**:
     - Priorizar a correção de bugs de alta severidade antes da próxima iteração de testes.
     - Acompanhar a resolução dos bugs listados na seção "Lista de Bugs".

3. **Impacto no Responsivo**
   - **Descrição**: O layout não se adapta adequadamente em diferentes dispositivos, prejudicando a experiência do usuário.
   - **Nível de Risco**: **Médio**
   - **Mitigação**:
     - Garantir que testes de responsividade sejam executados em uma ampla variedade de dispositivos e tamanhos de tela.
     - Usar ferramentas como BrowserStack para simular múltiplos ambientes.

4. **Falta de Padronização**
   - **Descrição**: Nomes diferentes para elementos semelhantes (ex: "Products" no menu hambúrguer e "All Items" na URL) podem causar confusão.
   - **Nível de Risco**: **Baixo**
   - **Mitigação**:
     - Estabelecer um guia de estilo e nomenclatura para as equipes de desenvolvimento e design.

5. **Problemas de Navegação**
   - **Descrição**: Redirecionamentos inconsistentes ao clicar em elementos como "Cancel" no checkout.
   - **Nível de Risco**: **Médio**
   - **Mitigação**:
     - Realizar revisões detalhadas dos fluxos de navegação.
     - Adicionar casos de teste específicos para mapear todos os caminhos de navegação.

---

### **6.2 Plano de Ação**
- **Avaliação contínua**: Monitorar os riscos durante todo o ciclo de testes, revisitando as estratégias de mitigação conforme necessário.
- **Automação de testes**: Implementar automação para cobrir regressões frequentes em áreas críticas, garantindo consistência.
- **Comunicação com stakeholders**: Manter todas as partes interessadas informadas sobre os principais riscos e as ações tomadas para mitigá-los.

## 7. Sugestões de Automação

Para melhorar a eficiência do processo de validação e garantir consistência nos testes, as seguintes estratégias de automação são sugeridas:

### 7.1 Ferramentas e Frameworks Recomendados
- **Selenium com Java**: Para automação de fluxos de interface, como login, navegação e checkout.
- **Cucumber**: Para implementar os cenários em Gherkin.
- **JUnit**: Para execução estruturada dos testes automatizados.
- **Allure Report**: Para gerar relatórios detalhados das execuções de teste.

### 7.2 Fluxos Prioritários para Automação
1. **Login**:
   - Cenários de autenticação com credenciais válidas e inválidas.
   - Mensagens de erro exibidas para campos obrigatórios não preenchidos.
   
2. **Carrinho**:
   - Adicionar e remover itens do carrinho.
   - Atualização do ícone do carrinho ao modificar itens.

3. **Checkout**:
   - Validação do fluxo completo de compra, desde o preenchimento dos formulários até a finalização.
   - Mensagens de erro para dados inválidos ou ausentes.

4. **Filtros de Produto**:
   - Validação das opções de ordenação (nome e preço).
   - Comportamento ao aplicar e remover filtros.

5. **Logout**:
   - Testar o logout em diferentes páginas do sistema.

### 7.3 Benefícios da Automação
- **Redução do tempo de execução**: Fluxos críticos podem ser validados rapidamente.
- **Cobertura ampliada**: Possibilidade de rodar os testes em múltiplos navegadores e dispositivos.
- **Previne que o sistema sofra regressões**: Testes automatizados identificam problemas introduzidos por mudanças no código.

### 7.4 Plano de Implementação
1. **Definição do Escopo**:
   - Mapear os casos de teste existentes que podem ser automatizados.
   - Priorizar cenários críticos identificados nas seções anteriores.

2. **Criação de Estrutura de Automação**:
   - Configurar os frameworks e ferramentas.
   - Estabelecer boas práticas de desenvolvimento, como Page Object Model (POM) para organização do código.

3. **Automação Incremental**:
   - Automatizar inicialmente os cenários prioritários (ex.: login, checkout).
   - Gradualmente expandir a automação para os fluxos menos críticos.

4. **Integração Contínua**:
   - Configurar pipelines de CI/CD para execução automática dos testes em cada commit.