# **Criação do Projeto**

Nesta seção, é apresentado o processo de criação de um projeto para utilização do **Probato**, garantindo uma estrutura base adequada para a automação de testes. O objetivo é organizar o projeto de forma consistente, preparando-o para receber as configurações e implementações necessárias à automação dos cenários de teste.

## **Criar um Projeto Maven**

### Usando o terminal ou prompt de comando

1. Abra o terminal ou prompt de comando.
2. Navegue até o diretório onde deseja criar o projeto.
3. Execute o comando abaixo:

```bash
mvn archetype:generate -DgroupId=com.example.automation -DartifactId=my-project-automation -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

**Parâmetros:**

* **groupId:** Identificador do grupo da sua organização, geralmente relacionado ao domínio (ex.: `com.example.automation`).
* **artifactId:** Nome do projeto de automação de testes (ex.: `my-project-automation`).

!!! note
    Caso prefira, a criação do projeto também pode ser realizada diretamente por meio da sua IDE.

4. Após a execução do comando, a seguinte estrutura será criada:

```plaintext title="Estrutura Padrão Maven"
my-project-automation/
├── src/
│   ├── main/
│   │   └── java/
│   │   │   └── com/example/automation/App.java
│   └── test/
│       └── java/
│           └── com/example/automation/AppTest.java
└── pom.xml
```

### Sobre o Maven Archetype

O comando `mvn archetype:generate` utiliza o **Maven Archetype** para gerar um projeto com uma estrutura inicial padrão. Esse recurso facilita a criação rápida de projetos, incluindo diretórios e arquivos básicos.

## **Configurar a Estrutura de Pacotes e Pastas**

1. Acesse o diretório `src/main/java/`.
2. Remova o pacote gerado automaticamente nesse diretório.
3. No diretório `src/test/java/`, remova a classe gerada automaticamente.
4. Crie o diretório `src/test/resources/` e adicione um arquivo chamado `configuration.yml`.

Após esses ajustes, a estrutura do projeto ficará da seguinte forma:

```plaintext title="Estrutura do projeto"
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

**Descrição das pastas:**

* `src/test/java/`: Local onde será implementada a automação de testes.
* `src/test/resources/`: Diretório destinado ao armazenamento de configurações, massas de dados, scripts SQL e outros arquivos necessários para a execução dos testes.

!!! note
    O arquivo `configuration.yml` será configurado em detalhes em seções posteriores.

## **Checklist Final**

Antes de prosseguir para a próxima seção, verifique se:

- ✅ O projeto Maven foi criado (`my-project-automation`).
- ✅ A estrutura de pastas foi ajustada conforme o exemplo apresentado.
- ✅ O arquivo `configuration.yml` foi criado em `src/test/resources/`.

Seu projeto está pronto para avançar para as próximas etapas da automação de testes com o Probato.
