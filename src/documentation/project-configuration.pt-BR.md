# **Configuração do Projeto**

Nesta seção, será detalhado como configurar o projeto Maven para utilizar o **Probato**, garantindo as devidas configurações estejam de acordo com necessário para automação de testes. O objetivo é preparar o projeto com as devidas com dependências e configurações essenciais para rodar testes automatizados de forma eficaz.

## **Adicionar Dependências ao Maven**

1. Abra o arquivo `pom.xml` localizado no diretório raiz do projeto.
2. Adicione as seguintes dependências:
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
        </properties>

        <dependencies>

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

            <!-- Dependência(s) do bando(s) de dados da aplicação alvo dos testes -->
            <dependency>
                <groupId>org.postgresql</groupId>
                <artifactId>postgresql</artifactId>
                <version>42.7.3</version>
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

### Descrição das Dependências
- **`probato-api`**, **`probato-browser`**, **`probato-dataset-csv`**, **`probato-database-sql`**, **`probato-record`**, **`probato-manager`**  : Oferece acesso às funcionalidades do **Probato**.
- **`postgresql`**: Necessário para conexão com banco de dados, então deve ser adicionada a dependência relativa ao banco de dados da aplicação alvo dos testes.
- **`junit-jupiter`**: Necessário para executar os testes com o JUnit 5.

    !!! note
         Outras dependências serão adicionadas conforme avançamos no tutorial.

---

## Adicionando e configurando o Probato 

1. No arquivo `configuration.yml` adicionar as configurações abaixo
```yaml title="configuration.yml"


execution:

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
      token: [TOKEN] # Token de integração que pode ser obtido no Probato Manager na página do projeto 

browsers:

-  type: CHROME
   headless: false
   dimension:
      mode: FULLSCREEN

-  type: FIREFOX
   headless: false
   dimension:
      mode: MAXIMIZED

-  type: EDGE
   headless: false
   dimension:
      mode: CUSTOM
      width: 800
      height: 600

datasources:

   probato:
      url: jdbc:postgresql://localhost:5444/probato
      driver: org.postgresql.Driver
      username: root
      password: root

```
  **Propriedades:**
    * **execution.delay.waitingTimeout:**   
    Tempo de espera máximo para execução de ação.
    * **execution.delay.actionInterval:**   
    Intervalo de tempo entre ações a serem executadas.
    * **browsers.[*].type:**   
    Informa qual o navegador será executado.
    * **browsers.[*].headless:**   
    Por padrão é `false`. Se `true` a janela do browser ficará invisível durante a execução.
    * **browsers.[*].dimension.mode:**   
    Por padrão é definido como `MAXIMIZED`, tem valores possíveis `FULLSCREEN`, `MAXIMIZED` e `CUSTOM`. Se informado `CUSTOM`, as propriedades `width` e `height` serão obrigatórias.
    * **browsers.[*].dimension.width:**  
    Informa qual a dimensão de largura o navegador será executado.
    * **browsers.[*].dimension.height:**   
    Informa qual a dimensão de altura o navegador será executado.
    * **datasources.[nome]:**   
    Informa o nome do recurso que será acessado.
    * **datasources.[nome].url:**   
    Informa a URL do recurso que será acessado.
    * **datasources.[nome].driver:**   
    Informa o driver de conexão para o recurso que será acessado.
    * **datasources.[nome].schema:**   
    Informa o schema para o recurso que será acessado.
    * **datasources.[*].dimension.width:**  
    Informa o usuário para o recurso que será acessado.
    * **datasources.[*].dimension.height:**   
    Informa a senha para o recurso que será acessado.

---

## **Checklist Final**

Antes de seguir para a próxima seção, confirme se tudo foi configurado:

- ✅ Dependências adicionadas ao arquivo `pom.xml`.
- ✅ Configurações adicionadas ao arquivo `configuration.yml`.

Seu projeto agora está pronto para começar a automação de testes com o Probato!
