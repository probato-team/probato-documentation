# Criação do Projeto

Esta seção descreve como criar a **estrutura base de um projeto de automação utilizando o Probato**. O objetivo não é apenas gerar um projeto Maven, mas estabelecer uma organização consistente que facilite a aplicação dos conceitos do framework.

Ao final desta etapa, o projeto estará pronto para receber configurações, Suites, Scripts e demais componentes do Probato.

## Visão geral da estrutura do projeto

O Probato é utilizado **exclusivamente no contexto de testes automatizados**. Por esse motivo, toda a implementação do framework reside sob o diretório `src/test`.

A criação do projeto segue três etapas principais:

1. Criação do projeto Maven  
2. Ajuste da estrutura de pacotes e diretórios  
3. Preparação dos recursos necessários à execução  

## Criação do projeto Maven

### Utilizando terminal ou prompt de comando

1. Abra o terminal ou prompt de comando.
2. Navegue até o diretório onde o projeto será criado.
3. Execute o comando abaixo:

```bash
mvn archetype:generate   -DgroupId=com.example.automation   -DartifactId=my-project-automation   -DarchetypeArtifactId=maven-archetype-quickstart   -DinteractiveMode=false
```

### Parâmetros utilizados

- **groupId**  
  Identificador do grupo da organização, normalmente relacionado ao domínio.  
  Exemplo: `com.example.automation`

- **artifactId**  
  Nome do projeto de automação.  
  Exemplo: `my-project-automation`

!!! note
    A criação do projeto também pode ser realizada diretamente pela IDE, utilizando os assistentes de criação de projetos Maven.

### Estrutura inicial gerada

Após a execução do comando, o Maven cria a seguinte estrutura padrão:

```plaintext title="Estrutura padrão Maven"
my-project-automation/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/example/automation/App.java
│   └── test/
│       └── java/
│           └── com/example/automation/AppTest.java
└── pom.xml
```

Essa estrutura é genérica e precisa ser ajustada para o uso com o Probato.

## Ajuste da estrutura de pacotes e pastas

O Probato não utiliza código de produção (`src/main`). Todo o código relevante fica em `src/test`.

### Limpeza inicial

1. Remova o diretório `src/main/java`.
2. Em `src/test/java`, remova a classe gerada automaticamente (`AppTest.java`).

### Criação da estrutura do Probato

Crie os seguintes diretórios:

- `src/test/java/com/example/automation/`
- `src/test/resources/`

Organize a estrutura conforme o modelo abaixo:

```plaintext title="Estrutura do projeto com Probato"
my-project-automation/
├── src/
│   └── test/
│       ├── java/
│       │   └── com/example/automation/
│       │       ├── model/
│       │       ├── page/
│       │       └── usecase/
│       └── resources/
│           ├── dataset/
│           ├── sql/
│           └── configuration.yml
└── pom.xml
```

### Descrição dos diretórios

- **src/test/java**  
  Contém toda a implementação de testes automatizados:

  - Suites
  - Scripts
  - Procedures
  - Page Objects
  - Modelos auxiliares

- **src/test/resources**  
  Armazena os recursos externos utilizados durante a execução:

  - Arquivos de Dataset
  - Scripts SQL ou NoSQL
  - Arquivo de configuração do Probato

O arquivo `configuration.yml` é o ponto central de configuração do framework.

!!! note
    O conteúdo e a estrutura do `configuration.yml` serão detalhados na próxima seção.

## Checklist final

Antes de avançar, confirme que:

- ✅ O projeto Maven foi criado corretamente
- ✅ A estrutura de diretórios foi ajustada
- ✅ O diretório `src/main` foi removido
- ✅ O arquivo `configuration.yml` existe em `src/test/resources`

Com o projeto criado, o próximo passo é configurar o comportamento do framework.

➡️ Próximo passo: **Configuração do Projeto**
