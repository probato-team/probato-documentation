# Configuração do Projeto

Esta seção descreve como configurar um projeto Maven para utilizar o **Probato**. Aqui são definidos tanto os **artefatos necessários para o build** quanto o **comportamento de execução do framework**.

O objetivo desta etapa é preparar o projeto para executar testes automatizados de forma previsível, declarativa e extensível.

## Papel da configuração no Probato

No Probato, a configuração é explicitamente separada do código de teste.

Enquanto o código descreve **o que será testado**, a configuração define:

- Como os testes serão executados
- Quais browsers serão utilizados
- Como evidências serão capturadas
- Quais integrações estarão ativas

Essa separação evita lógica condicional no código e permite alterar o comportamento do projeto sem recompilação.

## Configuração do Build (Maven)

O Probato é distribuído de forma **modular**. Cada funcionalidade do framework é habilitada por meio de dependências Maven.

### Dependências principais do Probato

Abra o arquivo `pom.xml`, localizado no diretório raiz do projeto, e adicione as dependências necessárias.

```xml title="pom.xml"
<project 
    xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example.automation</groupId>
    <artifactId>my-project-automation</artifactId>
    <version>1.0.0</version>

    <properties>
        <probato.version>0.1.0</probato.version>
        <selenium.version>4.33.0</selenium.version>
        <playwright.version>1.57.0</playwright.version>
        <postgresql.version>42.7.3</postgresql.version>
    </properties>

    <dependencies>

        <!-- Probato Core -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-core</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- Browsers -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-browser-chrome</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-browser-firefox</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-browser-edge</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- Datasets -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-datasets-csv</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- Database -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-database-sql</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- Record -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-record</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- UI executors -->
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>${selenium.version}</version>
        </dependency>

        <dependency>
            <groupId>com.microsoft.playwright</groupId>
            <artifactId>playwright</artifactId>
            <version>${playwright.version}</version>
        </dependency>

        <!-- Database driver -->
        <dependency>
            <groupId>org.postgresql</groupId>
            <artifactId>postgresql</artifactId>
            <version>${postgresql.version}</version>
            <scope>test</scope>
        </dependency>

    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.0.0-M7</version>
                <configuration>
                    <includes>
                        <include>**/*.java</include>
                    </includes>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>
```

## Arquivo de Configuração do Probato

O comportamento de execução do framework é definido no arquivo:

```
src/test/resources/configuration.yml
```

Esse arquivo concentra todas as definições relacionadas à execução dos testes.

### Exemplo de configuração

```yaml title="configuration.yml"
execution:
  engine: SELENIUM

  target:
    url: http://localhost:8099
    version: 0.0.0

  delay:
    waitingTimeout: 5000
    actionInterval: 500

  video:
    enabled: true
    frameRate: 1000
    quality: MEDIUM

  manager:
    submit: true
    url: http://localhost:8080
    token: [TOKEN]

browsers:
- type: CHROME
  headless: false
  dimension:
    mode: FULLSCREEN

datasources:
  probato:
    url: jdbc:postgresql://localhost:5444/probato
    driver: org.postgresql.Driver
    username: root
    password: root
```

## Propriedades disponíveis no configuration.yml

### Execution

| Propriedade | Descrição |
|-----------|----------|
| execution.engine | Engine de execução (SELENIUM ou PLAYWRIGHT) |
| execution.target.url | URL da aplicação alvo |
| execution.target.version | Versão da aplicação |
| execution.delay.waitingTimeout | Tempo máximo de espera |
| execution.delay.actionInterval | Intervalo entre ações |
| execution.video.enabled | Habilita gravação de vídeo |
| execution.video.frameRate | Taxa de quadros |
| execution.video.quality | Qualidade do vídeo |
| execution.manager.submit | Envia dados ao Probato Manager |
| execution.manager.url | URL do Manager |
| execution.manager.token | Token de autenticação |

### Browsers

| Propriedade | Descrição |
|------------|----------|
| browsers[].type | Tipo do browser |
| browsers[].headless | Executa em modo headless |
| browsers[].dimension.mode | FULLSCREEN, MAXIMIZED ou CUSTOM |
| browsers[].dimension.width | Largura (CUSTOM) |
| browsers[].dimension.height | Altura (CUSTOM) |

### Datasources

| Propriedade | Descrição |
|------------|----------|
| datasources.*.url | URL de conexão |
| datasources.*.driver | Driver JDBC |
| datasources.*.username | Usuário |
| datasources.*.password | Senha |

## Checklist final

- ✅ Dependências configuradas no `pom.xml`
- ✅ Arquivo `configuration.yml` criado
- ✅ Propriedades ajustadas conforme o ambiente

➡️ Próximo passo: **Configuração de Browser**
