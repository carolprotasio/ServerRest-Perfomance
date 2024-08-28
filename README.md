# ServeRest-Performance

## 1. Sobre o Projeto

Este projeto foi desenvolvido como parte dos meus estudos de QA e teste de performance, utilizando o JMeter, Docker, e a biblioteca Faker para geração de dados dinâmicos. O objetivo principal foi realizar testes de performance em diferentes módulos da API ServeRest (https://serverest.dev/), simulando o comportamento de múltiplos usuários acessando e manipulando recursos simultaneamente.

Os testes foram realizados nos endpoints que cobrem as funcionalidades de usuário, produto e carrinho, incluindo operações de CRUD (Criar, Ler, Atualizar, Deletar). Esse projeto permitiu aprofundar meus conhecimentos em automação de testes de performance e integração de ferramentas essenciais para a área de QA.

<img src="https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/swagger.png" alt="Swagger" width="600"/>

### 1.1 JMeter

O JMeter é uma ferramenta de código aberto utilizada para testar a performance de aplicações web. No contexto deste projeto, o JMeter foi empregado para simular múltiplos usuários interagindo com a API do ServeRest, permitindo a análise do desempenho da aplicação sob diferentes cargas de trabalho.

<img src="https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/jmeter.png" alt="jmeter" width="600"/>

### 1.2 Docker

O Docker foi utilizado para configurar e isolar o ambiente de testes, garantindo que o JMeter e todas as dependências necessárias estivessem corretamente configurados e reproduzíveis em qualquer ambiente. Com Docker, foi possível garantir consistência e simplicidade na execução dos testes.

<img src="https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/docker.png" alt="docker" width="600"/>

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

 <img src="https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/grafico-usuario.png"  width="600"/>

### 📦 [/produtos]

- **DoR**
  - Ambiente de testes e banco de dados configurados.
  - Requisitos funcionais definidos.

- **DoD**
  - CRUD de produtos implementado.
  - Testes de validação de dados, incluindo verificação de campos obrigatórios e formatos válidos.
  - Automação de testes baseada na análise realizada.
 
<img src="https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/grafico-produto.png" width="600"/>  

### 🛒 [/carrinho]

- **DoR**
  - Banco de dados e API configurados.
  - Escopo de testes definido.

- **DoD**
  - CRUD de carrinhos implementado.
  - Validação de regras de negócio, como quantidade mínima de itens e validação de usuário autenticado.
  - Automação de testes com cobertura total de cenários.
  - 
 <img src="https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/grafico-carrinho.png" alt="Product Info" width="600"/>
  

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

## 5. 📊 Análise dos Testes

### 5.1. Módulo Usuário

- **Comportamento Geral**: O módulo de usuários apresentou tempos de resposta consistentes. O **GET** teve o melhor desempenho, com um tempo médio de resposta em torno de **300 ms**, enquanto o **POST** foi o mais demorado, com uma média de **500 ms**. A maioria das requisições foi processada de forma eficiente, com o percentil 90 indicando que 90% das requisições foram atendidas dentro de **650 ms**.
- **Erros**: A taxa de erros foi baixa, relacionada principalmente a tentativas de criar usuários com emails duplicados ou inexistentes, o que é esperado e reflete a robustez das validações do sistema.
- **Conclusão**: O módulo de usuários demonstrou bom desempenho e baixa taxa de erros, sendo capaz de lidar com múltiplas requisições simultâneas de maneira eficaz.

![usuario-teste](https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/Crud-usuario-agregado.png)  

### 5.2. Módulo Produto

- **Comportamento Geral**: O módulo de produtos seguiu uma tendência semelhante ao de usuários, com o **GET** novamente sendo o mais rápido, e o **POST** e **PUT** apresentando tempos de resposta mais altos. O tempo médio de resposta do **POST** foi de **520 ms**, enquanto o **GET** ficou em torno de **310 ms**. A maioria das requisições foi atendida dentro de **670 ms** (percentil 90).
- **Erros**: A taxa de erros foi relativamente baixa, com a maioria dos problemas surgindo de tentativas de cadastro de produtos com nomes ou IDs duplicados.
- **Conclusão**: O módulo de produtos demonstrou eficiência, com tempos de resposta adequados e uma baixa incidência de erros, confirmando a capacidade do sistema em gerenciar operações complexas de produtos.


![produto-teste](https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/crud-produto-agregado.png)  

### 5.3. Módulo Carrinho

- **Comportamento Geral**: O módulo de carrinho apresentou um desempenho menos estável em comparação aos outros módulos, com tempos de resposta variando mais amplamente. O **PUT** e o **DELETE** tiveram tempos médios de resposta de **550 ms** e **570 ms**, respectivamente, mas o **POST** apresentou uma média mais alta, em torno de **600 ms**. O percentil 90 mostrou que 90% das requisições foram concluídas em até **710 ms**.
- **Erros**: A taxa de erros foi significativamente mais alta, chegando a quase **10%**, o que indica problemas durante as operações de **POST** e **PUT**. Esses erros estavam relacionados a falhas na criação e atualização de carrinhos, possivelmente devido a problemas na lógica de processamento ou concorrência no acesso aos dados.
- **Conclusão**: O módulo de carrinho demonstrou fragilidades, especialmente na criação e atualização de carrinhos, refletido na alta taxa de erros. Isso sugere que o sistema pode precisar de otimizações para melhorar a confiabilidade e o desempenho nesse módulo específico.

![carrinho-teste](https://github.com/carolprotasio/ServerRest-Perfomance/blob/master/crud-carrinho-agregado.png)
  
## 5.4. Conclusão dos testes de performance

Os testes de performance dos três módulos revelaram que, embora os módulos de usuário e produto tenham mostrado bom desempenho com baixa taxa de erros, o módulo de carrinho apresentou problemas significativos, com uma taxa de erros de quase 10%. O **GET** foi o mais eficiente em todos os módulos, enquanto as operações de **POST** e **PUT** enfrentaram desafios maiores, especialmente no módulo de carrinho. A análise indica que o ServeRest é robusto, mas com áreas que necessitam de melhorias, especialmente na gestão de carrinhos, para garantir uma performance consistente em ambientes de alta carga.

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

## 7. Conclusão do Projeto
Este projeto proporcionou um aprendizado valioso na aplicação de testes de performance com JMeter e Docker, especialmente ao simular cenários de uso com múltiplos usuários acessando o sistema simultaneamente. A integração da biblioteca Faker no JSR223 Sampler também se mostrou uma solução eficaz para a criação de dados dinâmicos, garantindo testes mais robustos e realistas.

O uso de Docker garantiu um ambiente de testes consistente e facilmente replicável, essencial para manter a integridade dos resultados. Este projeto contribui significativamente para meu paprendizado, demonstrando habilidades avançadas em testes de performance e automação de ambientes de teste.
