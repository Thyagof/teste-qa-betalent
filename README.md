# Bem-vindo(a) ao Teste Prático QA Testing BeTalent! 

Você terá de executar e documentar dois tipos de testes:

1. [**UI Testing**](/ui-testing)
2. [**API Testing**](/api-testing)

Os requisitos a serem atendidos estão detalhados abaixo.

---

## 1. [UI Testing](/ui-testing)

### Descrição
A tarefa consiste em testar a plataforma de e-commerce **[Sauce Demo](https://www.saucedemo.com)**. O objetivo é realizar uma validação completa da aplicação antes de sua liberação em produção.

### Instruções
1. Crie um plano de testes documentado que cubra os principais fluxos da aplicação.
2. Execute os testes manualmente e documente os resultados.
3. Identifique potenciais problemas de UX/UI que poderiam impactar negativamente a experiência do usuário.

### Cenários Mínimos a Serem Testados
1. Login com diferentes tipos de usuários disponíveis.
2. Ordenação e filtragem de produtos.
3. Fluxo completo de compra (do carrinho até a finalização).
4. Remoção de itens do carrinho.
5. Navegação entre páginas.
6. Logout.

### Entregáveis
1. **Documento em Markdown (.md)** contendo:
   - Plano de testes estruturado com casos de teste.
   - Resultados dos testes executados.
   - Sugestões de melhorias de UX/UI.
   - Lista de bugs encontrados (se houver).
   - Análise de riscos da aplicação.
2. **Extras (diferenciais)**:
   - Testes de responsividade.
   - Testes de acessibilidade.
   - Sugestões de automação.

### Critérios de Avaliação
1. Organização e clareza da documentação.
2. Cobertura dos cenários críticos.
3. Capacidade de identificar eventuais bugs/problemas.
4. Qualidade das sugestões de melhoria.
5. Pensamento crítico sobre eventuais riscos e impactos no negócio.

### Observações
- A documentação deve ser entregue obrigatoriamente em Markdown (.md).
- Quando necessário, explique/justifique suas decisões.
- Inclua prints de tela quando relevante.

---

## 2. [API Testing](/api-testing)

### Descrição
A tarefa consiste em testar a API do **[Restful-Booker](https://restful-booker.herokuapp.com)**, um sistema de reservas de hotel. O objetivo é validar a API antes de sua integração com o front-end.

### Instruções
1. Analise a documentação da API fornecida.
2. Crie e execute testes para os endpoints principais.
3. Documente os resultados e comportamentos encontrados.

### Cenários
1. **Autenticação**:
   - Gerar token de autenticação.
   - Tentar gerar token com credenciais inválidas.
2. **Gestão de Reservas**:
   - Criar uma nova reserva.
   - Buscar uma reserva específica.
   - Listar todas as reservas.
   - Atualizar uma reserva existente.
   - Deletar uma reserva.
3. **Filtros e Buscas**:
   - Buscar reservas por nome.
   - Buscar reservas por data de check-in.
   - Buscar reservas por data de check-out.

### Entregáveis
1. **Collection contendo**:
   - Todos os requests organizados.
   - Pelo menos um teste para cada request.
   - Variáveis de ambiente configuradas.
2. **Documento em Markdown (.md)** contendo:
   - Lista de cenários testados.
   - Resultados obtidos.
   - Bugs encontrados (se houver).

### Pontos de Atenção
1. Tratamento de erros.
2. Validação de campos obrigatórios.
3. Formato das datas.
4. Códigos de resposta HTTP.

### Observações
- Utilize o Postman ou qualquer outra ferramenta de sua preferência.
- Documente quaisquer premissas assumidas, se possível.

---

## 3. Considerações Finais

Caso não consiga completar os testes até o prazo definido:
1. Garanta que tudo que foi construído esteja em funcionamento.
2. Relate na documentação quais foram as dificuldades encontradas.
3. Documente o que foi implementado e o que ficou pendente.

---

## 4. Envio dos Entregáveis

Os entregáveis de ambos os testes deverão ser hospedados em um repositório no seu GitHub. O link do repositório deverá ser fornecido por meio deste formulário. **Não serão aceitos links de entregáveis enviados por outros meios.**

---

**Boa sorte! 🍀**
