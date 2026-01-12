# Arquitetura

O **Probato** foi projetado com uma arquitetura modular e altamente extensível para suportar a automação de testes em nível funcional de forma eficiente e escalável. A arquitetura adota conceitos modernos de design de software, como o **Page Object Model (POM)** e a **injeção de dependências via anotações**, permitindo a criação de scripts reutilizáveis, fáceis de manter e evoluir.

Essa abordagem garante separação clara de responsabilidades, previsibilidade de execução e flexibilidade para adaptação a diferentes cenários de automação.

## Princípios Arquiteturais

A arquitetura do **Probato** é baseada em:

- modularidade
- isolamento de responsabilidades
- reutilização de componentes
- extensibilidade sem impacto no núcleo
- integração transparente com ferramentas externas

Esses princípios orientam todas as camadas do framework.

## Camadas Arquiteturais e Isolamento de Responsabilidades

A arquitetura do **Probato** é composta por múltiplas camadas, cada uma com responsabilidades bem definidas, facilitando a manutenção, evolução e diagnóstico de falhas.

### Camada de Interação (Page Object Model)

- Implementa o padrão **Page Object Model (POM)**, encapsulando a lógica de interação com a interface do usuário.
- Cada página, tela ou componente é representado como um objeto contendo métodos para interações possíveis (cliques, inserção de dados, validações etc.).
- Promove reutilização de código e facilita a manutenção quando a interface da aplicação é alterada.

### Camada de Testes (Scripts e Procedimentos)

- Os testes são organizados em **scripts**, compostos por ações subdivididas em:
  - **Pré-condições**
  - **Procedimentos**
  - **Pós-condições**
- Essa separação permite isolar falhas e identificar com precisão em qual etapa ocorreu o erro.

### Camada de Injeção de Massa de Dados

- Permite o uso flexível e dinâmico de dados de entrada.
- Suporta injeção de dados via arquivos CSV.
- Possui previsão de suporte futuro para JSON, YAML e bancos de dados por meio de plugins personalizados.

### Camada de Persistência e Conectores SQL

- Disponibiliza um executor SQL integrado capaz de conectar-se a múltiplas bases de dados.
- Permite definir pré-condições de banco, alterar estados dinamicamente antes dos testes e restaurar estados após a execução.

## Injeção de Dependências com Anotações

- Adota um modelo de **injeção de dependências via anotações Java**, promovendo **Inversão de Controle (IoC)**.
- Simplifica configurações manuais, permitindo que objetos necessários sejam injetados automaticamente.
- Promove modularidade, desacoplamento e reutilização de componentes.

## Modelo de Execução Baseado no JUnit 5

O **Probato** integra-se ao ciclo de vida do **JUnit 5**, utilizando testes dinâmicos e a anotação `@TestFactory` para geração de casos de teste em tempo de execução.

### Ciclo de Vida de Execução

![Probato Life Cycle](/assets/images/introduction/probato-life-cycle.png)

- **BeforeAll**  
  Carrega pontos de extensão, configurações e executa validações de código e ambiente. Também cria testes dinâmicos do JUnit 5.

- **BeforeEach**  
  Carrega conjuntos de dados e scripts necessários e inicia a execução dos cenários de teste.

- **TestFactory**  
  Gera testes dinamicamente com base em scripts, procedimentos e Page Objects. Suporta **data-driven testing**, permitindo múltiplas execuções com diferentes conjuntos de dados.

- **AfterEach**  
  Submete os dados coletados ao **Probato Manager** e armazena imagens e vídeos no armazenamento configurado.

- **AfterAll**  
  Calcula métricas de qualidade do software e notifica os colaboradores sobre a conclusão da execução.

## Suporte à Execução Multibrowser

- Construído sobre APIs do **Selenium** e **Playwright**, permitindo automação em múltiplos navegadores.
- Suporte extensível para novos browsers, sistemas operacionais e contextos de execução.

## Extensibilidade e Plugins

- O framework foi projetado para ser **altamente extensível**, permitindo a adição de funcionalidades sem alterações no núcleo.
- Suporte a plugins para:
  - novos drivers de browser
  - formatos adicionais de dados de entrada
  - novos tipos de validação
  - executores SQL ou NoSQL personalizados

## Gerenciamento de Execuções e Coleta de Dados

Durante a execução dos testes, o **Probato** captura e processa dados como:

- logs de execução
- capturas de tela
- vídeos
- passos executados

Esses dados são enviados para uma aplicação web integrada, que oferece:

- monitoramento centralizado das execuções
- geração de relatórios detalhados
- rastreamento de bugs
- análise por versionamento

A arquitetura do Probato permite a integração com ferramentas externas de gestão de testes e defeitos, como **TestLink** e **Mantis Bug Tracker**, por meio de seus pontos de extensibilidade. Essas integrações podem ser implementadas como plugins, sem necessidade de alterações no núcleo do framework.

## Configurações e Personalizações Avançadas

O **Probato** oferece opções avançadas de configuração para:

- definição de **timeouts** e intervalos entre ações
- ajuste de qualidade de imagens e vídeos
- controle de execução em múltiplos monitores

## Notificações e Integração Contínua

- Envio automático de notificações aos colaboradores após cada execução.
- Integração com ferramentas de **CI/CD**, como **Jenkins**, permitindo automação completa do processo de testes no ciclo de desenvolvimento.
