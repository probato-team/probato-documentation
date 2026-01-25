# Arquitetura

O **Probato** foi projetado com uma arquitetura modular e altamente extensível para suportar a automação de testes em nível funcional de forma eficiente e escalável. A arquitetura adota conceitos modernos de design de software, como o **Page Object Model (POM)** e a **injeção de dependências via anotações**, permitindo a criação de scripts reutilizáveis, fáceis de manter e evoluir.

Essa abordagem garante separação clara de responsabilidades, previsibilidade de execução e flexibilidade para adaptação a diferentes cenários de automação.

## Princípios arquiteturais

A arquitetura do **Probato** é baseada em:

- Modularidade
- Isolamento de responsabilidades
- Reutilização de componentes
- Extensibilidade sem impacto no núcleo
- Integração transparente com ferramentas externas

Esses princípios orientam todas as camadas do framework.

## Camadas arquiteturais e isolamento de responsabilidades

A arquitetura do **Probato** é composta por múltiplas camadas, cada uma com responsabilidades bem definidas, facilitando a manutenção, evolução e diagnóstico de falhas.

### Camada de interação (Page Object Model)

- Implementa o padrão **Page Object Model (POM)**, encapsulando a lógica de interação com a interface do usuário.
- Cada página, tela ou componente é representado como um objeto contendo métodos para interações possíveis (cliques, inserção de dados, validações etc.).
- Promove reutilização de código e facilita a manutenção quando a interface da aplicação é alterada.

### Camada de testes (Scripts e Procedimentos)

Os testes são organizados em **scripts**, compostos por ações subdivididas em:

- **Pré-condições**
- **Procedimentos**
- **Pós-condições**

Essa separação permite isolar falhas e identificar com precisão em qual etapa ocorreu o erro.

### Camada de injeção de massa de dados

- Permite o uso flexível e dinâmico de dados de entrada.
- Suporta injeção de dados via arquivos CSV.
- Possui previsão de suporte futuro para JSON, YAML e bancos de dados por meio de plugins personalizados.

### Camada de persistência e conectores em bancos de dados

- Disponibiliza um executor SQL e NoSQL integrado capaz de conectar-se a múltiplas bases de dados.
- Permite definir pré-condições de banco, alterar estados dinamicamente antes dos testes e restaurar estados após a execução.

## Injeção de dependências com anotações

- Adota um modelo de **injeção de dependências via anotações Java**, promovendo **Inversão de Controle (IoC)**.
- Simplifica configurações manuais, permitindo que objetos necessários sejam injetados automaticamente.
- Promove modularidade, desacoplamento e reutilização de componentes.

## Modelo de execução baseado no JUnit 5

O **Probato** integra-se ao ciclo de vida do **JUnit 5**, utilizando testes dinâmicos e a anotação `@TestFactory` para geração de casos de teste em tempo de execução.

### Ciclo de vida de execução

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

## Suporte à execução multibrowser

- Construído sobre APIs do **Selenium** e **Playwright**, permitindo automação em múltiplos navegadores.
- Suporte extensível para novos browsers, sistemas operacionais e contextos de execução.

## Extensibilidade e plugins

O framework foi projetado para ser **altamente extensível**, permitindo a adição de funcionalidades sem alterações no núcleo.

Suporte a plugins para:

  - Novos drivers de browser
  - Formatos adicionais de dados de entrada
  - Novos tipos de validação
  - Executores SQL ou NoSQL personalizados

## Gerenciamento de execuções e coleta de dados

Durante a execução dos testes, o **Probato** captura e processa dados como:

- Logs de execução
- Capturas de tela
- Vídeos
- Passos executados

Esses dados são enviados para uma aplicação web integrada, que oferece:

- Monitoramento centralizado das execuções
- Geração de relatórios detalhados
- Rastreamento de bugs
- Análise por versionamento

A arquitetura do Probato permite a integração com ferramentas externas de gestão de testes e defeitos, como **TestLink** e **Mantis Bug Tracker**, por meio de seus pontos de extensibilidade. Essas integrações podem ser implementadas como plugins, sem necessidade de alterações no núcleo do framework.

## Configurações e personalizações avançadas

O **Probato** oferece opções avançadas de configuração para:

- Definição de **timeouts** e intervalos entre ações
- Ajuste de qualidade de imagens e vídeos
- Controle de execução em múltiplos monitores

## Notificações e integração contínua

- Envio automático de notificações aos colaboradores após cada execução.
- Integração com ferramentas de **CI/CD**, como **Jenkins**, permitindo automação completa do processo de testes no ciclo de desenvolvimento.
