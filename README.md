<h2> API RESTful para Gestão de Produtos </h2> 
Este projeto consolida o desenvolvimento de uma API robusta utilizando o ecossistema Spring Boot 3 e Java 22, projetada para gerenciar catálogos de produtos com foco em eficiência e organização arquitetural. A aplicação não apenas cumpre o ciclo CRUD padrão, mas introduz funcionalidades avançadas de persistência em massa, permitindo que o sistema processe listas de produtos em uma única transação. 

<h3> Estrutura Técnica e Persistência com SQLite </h3> 
A arquitetura foi fundamentada no padrão de camadas, onde o Spring Data JPA desempenha o papel crucial de abstrair a complexidade das consultas SQL, gerenciando as entidades diretamente no banco de dados SQLite. A escolha pelo SQLite ocorre na escolha de uma solução leve e autossuficiente para o armazenamento de dados, enquanto o JPA assegura que a aplicação permaneça escalável e fácil de manter. No arquivo de modelo, anotações de validação como @NotEmpty garantem que nenhum produto seja registrado sem informações essenciais, mantendo a integridade do banco desde o primeiro contato com a API.

 ![Estrutura Package Explorer](Assets/organizacaoPackageExplorer.png)

<h3> Cadastro em massa </h3>
Um dos pontos interessantes desta API é a capacidade de realizar adições em massa através do endpoint /salvarLista. Diferente de implementações convencionais que processam um item por vez, esta funcionalidade utiliza o método saveAll para otimizar o fluxo de escrita no banco de dados. Abordagem fundamental para cenários de alta demanda. Ao enviar um array de objetos JSON via Postman, o backend processa a coleção completa atribuindo IDs.

![Adicionando lista de produtos](Assets/POST.png)
![Mostrando lista de produtos](Assets/GET.png)


<h3> Integração Frontend e CORS </h3>
Foi desenvolvida uma interface utilizando HTML e JavaScript para mostrar a tabela final dos produtos na web. A comunicação ocorre por meio da Fetch API, que consome os endpoints da API para renderizar dinamicamente uma tabela de produtos. Para haver essa troca de informações entre backend e frontend, foi implementada a configuração de CORS (Cross-Origin Resource Sharing) no controlador principal, para não haver bloqueio do navegador.

![Tabela WEB](Assets/tabelaWebEPostman.png)
