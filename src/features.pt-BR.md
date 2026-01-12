# Recursos

O **Probato** oferece um conjunto abrangente de recursos para estruturar, executar, observar e evoluir projetos de automação de testes de forma consistente e escalável.

Os recursos abaixo estão organizados de acordo com seu papel no ciclo de automação.

## Estrutura e Organização de Testes

### Estrutura Simples e Intuitiva

O **Probato** oferece uma estrutura organizada e modular para implementação de testes, facilitando a reutilização de componentes e a manutenção de scripts. Isso permite que equipes se concentrem mais na lógica de testes do que na estrutura de implementação.

### Injeção de Objetos com Anotações

A utilização de anotações simplifica a configuração de testes, permitindo uma injeção de objetos clara e concisa, sem necessidade de implementações adicionais.

### Padrão Page Object Model (POM)

O **Probato** segue o padrão **Page Object Model**, ajudando na separação de camadas e organização do código. Essa abordagem facilita a manutenção e leitura dos scripts, especialmente em frameworks como Selenium.

### Organização de Procedimentos de Teste

Os testes são organizados em três etapas:

1. **Pré-condições**
2. **Procedimentos**
3. **Pós-condições**

Essa estrutura permite identificar rapidamente a origem de falhas e entender se os erros estão nas funcionalidades alvo, nas etapas preparatórias ou nos objetivos de pós-condição.

### Criação de Roteiros de Teste Intuitivos

Os roteiros podem ser criados com código, descrição e pesos baseados na relevância e complexidade da funcionalidade. Isso auxilia na priorização e na análise de métricas para inferir a qualidade do software testado.

## Dados e Estado da Aplicação

### Carregamento e Injeção Implícita de Massa de Dados

Os scripts podem ser executados com diferentes conjuntos de dados, permitindo testes abrangentes sem duplicação de código. Essa funcionalidade melhora a eficiência e amplia a cobertura dos testes.

### Executores SQL e NoSQL

Os executores permitem conectar-se a múltiplas bases de dados para alterar o estado da aplicação conforme as pré-condições dos testes. Isso oferece flexibilidade na preparação de cenários de teste.

## Execução e Controle

### Configurações de Timeout e Intervalos

O **Probato** permite:

- configurar _timeouts_ para o tempo de espera durante a execução dos testes;
- ajustar intervalos entre ações, otimizando o desempenho das execuções.

### Execução em Diversos Browsers

Suporte para execução de testes em múltiplos navegadores, com opções como:

- modo maximizado, normal ou customizado (dimensões específicas);
- escolha do monitor para execução (primário ou secundário).

## Observabilidade e Análise de Resultados

### Gerenciamento de Dados Coletados

O **Probato** inclui uma aplicação web dedicada para:

- gerenciamento de dados de execução;
- análise da qualidade do software;
- criação de bugs a partir dos resultados;
- visualização de históricos por versionamento;
- geração de relatórios detalhados com logs e gráficos de cobertura.

### Captura de Dados Durante a Execução

Durante a execução dos testes, o Probato coleta e armazena informações como:

- suítes e roteiros de testes;
- passos executados;
- dados aplicados;
- scripts SQL;
- vídeos e capturas de tela.

A qualidade dos vídeos pode ser configurada para permitir análises detalhadas.

### Notificações de Execução

O framework permite o envio de notificações para os colaboradores sempre que novas execuções ocorrem, mantendo todos atualizados sobre o status dos testes.

## Extensibilidade e Integração

### Extensibilidade

O **Probato** permite personalizações por meio de plugins, incluindo:

- suporte a novos browsers;
- validações adicionais;
- entrada de massa de dados em novos formatos;
- executores SQL ou NoSQL personalizados;
- abertura para criação de novos recursos.

### Integração com Ferramentas de CI/CD

O framework integra-se facilmente com sistemas de integração contínua, como:

- **Jenkins**
- **Travis CI**
- **GitLab CI**

Essa integração permite a execução automática de testes a cada commit ou em etapas estratégicas do desenvolvimento, garantindo validações contínuas e ágeis.
