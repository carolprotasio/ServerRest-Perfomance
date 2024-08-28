# ServeRest-Performance

## 1. Sobre o Projeto

Este projeto foi desenvolvido como parte dos meus estudos de QA e teste de performance, utilizando o JMeter, Docker, e a biblioteca Faker para geração de dados dinâmicos. O objetivo principal foi realizar testes de performance em diferentes módulos da API ServeRest (https://serverest.dev/), simulando o comportamento de múltiplos usuários acessando e manipulando recursos simultaneamente.

Os testes foram realizados nos endpoints que cobrem as funcionalidades de usuário, produto e carrinho, incluindo operações de CRUD (Criar, Ler, Atualizar, Deletar). Esse projeto permitiu aprofundar meus conhecimentos em automação de testes de performance e integração de ferramentas essenciais para a área de QA.

### 1.1 JMeter

O JMeter é uma ferramenta de código aberto utilizada para testar a performance de aplicações web. No contexto deste projeto, o JMeter foi empregado para simular múltiplos usuários interagindo com a API do ServeRest, permitindo a análise do desempenho da aplicação sob diferentes cargas de trabalho.

### 1.2 Docker

O Docker foi utilizado para configurar e isolar o ambiente de testes, garantindo que o JMeter e todas as dependências necessárias estivessem corretamente configurados e reproduzíveis em qualquer ambiente. Com Docker, foi possível garantir consistência e simplicidade na execução dos testes.
<img src="https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/docker.png" alt="Product Info" width="600"/>

## 2. Tecnologias Utilizadas

- **JMeter**: Ferramenta para testes de carga e performance.
- **Docker**: Plataforma para virtualização e automação de ambientes.
- **Faker**: Biblioteca para geração de dados fictícios, usada na criação de cenários de teste.
- **JSR223 Sampler**: Componente do JMeter usado para scripting avançado, onde foi integrado o Faker.

## 3. Funcionalidades e Módulos Testados

Foram testados os seguintes módulos da API ServeRest:

### 👫 [/usuarios]

- **DoR (Definition of Ready)**
  - Banco de dados e infraestrutura para desenvolvimento disponibilizados.
  - Ambiente de testes configurado.

- **DoD (Definition of Done)**
  - CRUD de usuários implementado (Criar, Atualizar, Listar, Deletar).
  - Testes cobrindo todos os verbos HTTP (GET, POST, PUT, DELETE).
  - Matriz de rastreabilidade atualizada.
  - Automação de testes baseada na análise realizada.

### 📦 [/produtos]

- **DoR**
  - Ambiente de testes e banco de dados configurados.
  - Requisitos funcionais definidos.

- **DoD**
  - CRUD de produtos implementado.
  - Testes de validação de dados, incluindo verificação de campos obrigatórios e formatos válidos.
  - Automação de testes baseada na análise realizada.

### 🛒 [/carrinho]

- **DoR**
  - Banco de dados e API configurados.
  - Escopo de testes definido.

- **DoD**
  - CRUD de carrinhos implementado.
  - Validação de regras de negócio, como quantidade mínima de itens e validação de usuário autenticado.
  - Automação de testes com cobertura total de cenários.

## 4. Critérios de Aceitação dos Módulos

### 👫 Usuários

- Todos os usuários devem possuir cadastro contendo: Nome, Email, Senha, e Administrador.
- Ações não podem ser realizadas com usuários inexistentes.
- Não deve ser possível criar um usuário com email já utilizado.
- Um novo usuário deve ser criado caso o ID informado no PUT não seja encontrado.
- Emails devem seguir um padrão válido.

### 📦 Produtos

- Produtos devem ter os campos: Nome, Preço, Descrição, e Quantidade.
- Não deve ser possível cadastrar produtos com nome duplicado.
- Produtos devem ser acessíveis apenas por usuários autenticados.
- Produtos inativos não devem aparecer na listagem pública.

### 🛒 Carrinho

- Carrinho deve estar associado a um usuário autenticado.
- Não deve ser possível adicionar produtos inexistentes ao carrinho.
- Quantidade de produtos no carrinho deve respeitar os limites estabelecidos (ex: estoque disponível).
- Carrinho deve ser esvaziado após a conclusão da compra.

## 5. Resultado dos Testes

(Inclua aqui as imagens dos resultados dos testes realizados, como gráficos de tempo de resposta, taxa de sucesso, etc.)

## 6. Como Executar o Projeto

### 6.1 Pré-requisitos

- Docker instalado na máquina.
- JMeter configurado (pode ser executado via Docker).

### 6.2 Clonando o Projeto

```bash
git clone https://github.com/carolprotasio/ServerRest-Perfomance.git
```
### 6.3 Executando os Testes
- Navegue até a pasta do projeto.
- Execute o comando Docker para iniciar o ambiente
- Abra o JMeter e carregue o arquivo ServeRest-Performance.jmx.
- Configure o número de usuários virtuais conforme desejado.
- Execute o teste e visualize os resultados.

  ## 7. Conclusão do Projeto
Este projeto proporcionou um aprendizado valioso na aplicação de testes de performance com JMeter e Docker, especialmente ao simular cenários de uso com múltiplos usuários acessando o sistema simultaneamente. A integração da biblioteca Faker no JSR223 Sampler também se mostrou uma solução eficaz para a criação de dados dinâmicos, garantindo testes mais robustos e realistas.

O uso de Docker garantiu um ambiente de testes consistente e facilmente replicável, essencial para manter a integridade dos resultados. Este projeto contribui significativamente para meu paprendizado, demonstrando habilidades avançadas em testes de performance e automação de ambientes de teste.
