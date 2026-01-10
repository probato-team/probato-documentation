# **Implementação de Database**

Nessa seção será implementado Database. Neste Database irá contemplar o estado persistente necessário como pré condição necessária para execução do cenário de teste de login com sucesso no **Probato**

## **Criando arquivos SQL**

1. Na pasta `src/test/resources/sql` vamos criar a nova pasta `init`.
2. Na pasta `src/test/resources/sql` vamos criar a nova pasta `user`.
3. Na pasta `src/test/resources/sql/init` vamos criar o arquivo chamado `init.sql`.
4. Na pasta `src/test/resources/sql/user` vamos criar o arquivo chamado `insert-user.sql`.
5. No arquivo `init.sql` vamos adicionar o conteúdo abaixo.
```sql title="init.sql" linenums="1"

DELETE FROM testano_app.users;

```
6. No arquivo `insert-user.sql` vamos adicionar o conteúdo abaixo.
```sql title="insert-user.sql" linenums="1"

INSERT INTO testano_app.users
(id, "name", email, "password", gender, active)
VALUES('a02b03e6-c462-4980-9997-c1203a094c9d'::uuid, 'User 01', 'user01@probato.org', '$2a$10$Kml4nk3ADhnWrJg0GkStVeTJoslDBir/Fgyw2gkLR0FukujfIxZQ2', 'MALE',  true);

INSERT INTO testano_app.users
(id, "name", email, "password", gender, active)
VALUES('bd84a2c8-d315-40ea-80aa-1841254b20c9'::uuid, 'User 02', 'user02@probato.org', '$2a$10$oHZ7er1/2/xKjgOq0znXnOPcvoOXpX.in6XO/4mf2xf5ZV7OMyvq6', 'MALE',  true);

INSERT INTO testano_app.users
(id, "name", email, "password", gender, active)
VALUES('b86a08ac-2ee8-42c7-a46f-c589b1d26503'::uuid, 'User 03', 'user03@probato.org', '$2a$10$81pSkjzZTqgn3/nU5DzxVemmr0rjJ7NHtK/UiGhzomEwTyHZgFliC', 'MALE',  true);

```

## **Atualizando classe Script**

1. Na classe `UC01TC01_PerformLoginSuccessfully.java` vamos adicionar a implementação abaixo.
```java title="UC01TC01_PerformLoginSuccessfully.java" linenums="1" hl_lines="8-10"

package org.probato.manager.automation.usecase.UC01.script;

import org.probato.api.Dataset;
import org.probato.api.Procedure;
import org.probato.api.Script;

@Dataset("dataset/UC01/UC01TC01.csv")
@SQL(
	datasource = "probato", 
	scriptPath = { "sql/user/insert-user.sql" })
@Script(
  code = "UC01TC01", 
  name = "Perform login successfully", 
  description = "This script aims to validate the user's login in the application successfully")
public class UC01TC01_PerformLoginSuccessfully {

  @Procedure
  private PerformLoginSuccessfullyProcedure procedure;
  
}
```

## **Atualizando classe Suite**

1. Na classe `UC01_PerformLogin.java` vamos adicionar a implementação abaixo.
```java title="UC01_PerformLogin.java" linenums="1" hl_lines="1-3"
@SQL(
	datasource = "probato", 
	scriptPath = { "sql/init/init.sql" })
@Suite(
	code = "UC01", 
	name = "Perform login", 
	description = "This feature aims to allow the user to login to this application")
class UC01_PerformLogin implements TestSuite {
	
	@TestCase
	private UC01TC01_PerformLoginSuccessfully uc01tc01;

}
```

## **Checklist Final**

Antes de prosseguir para a próxima seção, verifique se:

- ✅ O código criado compila com sucesso.
- ✅ Os scripts SQL devem ser executados na base de dados informada no datasource.

Seu projeto está pronto para avançar para as próximas etapas da automação de testes com o **Probato**.
