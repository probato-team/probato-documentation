# Implementação de Database

Nesta seção será implementado o conceito de **Database**, responsável por preparar o **estado persistente da aplicação** como pré-condição necessária para a execução do cenário de **login com sucesso** no **Probato**. No Probato, Database é utilizado para **definir estado**, não para executar lógica de teste. Scripts SQL ou NoSQL são declarados de forma explícita e executados automaticamente antes dos cenários.

## Configuração de datasource

A configuração de conexão com o banco de dados deve ser definida no arquivo `configuration.yml`

```yaml title="configuration.yml"

datasources:

   probato:
      url: jdbc:h2:mem:testdb
      driver: org.h2.Driver
      username: sa
      password: password

```

## Criando os arquivos SQL

1. No diretório `src/test/resources/sql`, crie a pasta `init`.
2. No diretório `src/test/resources/sql`, crie a pasta `user`.
3. Dentro de `src/test/resources/sql/init`, crie o arquivo `init.sql`.
4. Dentro de `src/test/resources/sql/user`, crie o arquivo `insert-user.sql`.

### Script de inicialização global

O script `init.sql` será utilizado para preparar o **estado global** da funcionalidade, sendo executado antes de todos os Scripts da Suite.

```sql title="init.sql" linenums="1"
DELETE FROM testano_app.users;
```

### Script de dados do cenário

O script `insert-user.sql` será utilizado para preparar o **estado específico do cenário**, inserindo os usuários necessários para o teste de login.

```sql title="insert-user.sql" linenums="1"
INSERT INTO testano_app.users
(id, "name", email, "password", gender, active)
VALUES
('a02b03e6-c462-4980-9997-c1203a094c9d'::uuid, 'User 01', 'user01@probato.org', '$2a$10$Kml4nk3ADhnWrJg0GkStVeTJoslDBir/Fgyw2gkLR0FukujfIxZQ2', 'MALE', true);

INSERT INTO testano_app.users
(id, "name", email, "password", gender, active)
VALUES
('bd84a2c8-d315-40ea-80aa-1841254b20c9'::uuid, 'User 02', 'user02@probato.org', '$2a$10$oHZ7er1/2/xKjgOq0znXnOPcvoOXpX.in6XO/4mf2xf5ZV7OMyvq6', 'MALE', true);

INSERT INTO testano_app.users
(id, "name", email, "password", gender, active)
VALUES
('b86a08ac-2ee8-42c7-a46f-c589b1d26503'::uuid, 'User 03', 'user03@probato.org', '$2a$10$81pSkjzZTqgn3/nU5DzxVemmr0rjJ7NHtK/UiGhzomEwTyHZgFliC', 'MALE', true);
```

## Atualizando a classe Script

O Script pode declarar **estado específico do cenário** por meio da anotação `@SQL`.

```java title="UC01TC01_EfetuarLoginComSucesso.java" linenums="1" hl_lines="9-11"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Dataset;
import org.probato.api.Procedure;
import org.probato.api.Script;
import org.probato.api.SQL;

@Dataset("dataset/UC01/UC01TC01.csv")
@SQL(
    datasource = "probato",
    scriptPath = { "sql/user/insert-user.sql" }
)
@Script(
    code = "UC01TC01",
    name = "Efetuar login com sucesso",
    description = "Valida o cenário de autenticação do usuário com credenciais válidas"
)
public class UC01TC01_EfetuarLoginComSucesso {

    @Procedure
    private EfetuarLoginComSucessoProcedure procedure;

}
```

Nesse ponto:

- O Script declara qual estado específico necessita
- O Database é preparado automaticamente antes da execução
- A Procedure permanece focada apenas na lógica

## Atualizando a classe Suite

A Suite pode declarar **estado global da funcionalidade**, aplicado antes de todos os Scripts.

```java title="UC01_EfetuarLogin.java" linenums="1" hl_lines="5-8"
import org.probato.api.SQL;
import org.probato.api.Suite;
import org.probato.api.TestCase;

@SQL(
    datasource = "probato",
    scriptPath = { "sql/init/init.sql" }
)
@Suite(
    code = "UC01",
    name = "Efetuar Login",
    description = "Valida a funcionalidade de autenticação de usuários no sistema"
)
class UC01_EfetuarLogin {

    @TestCase
    private UC01TC01_EfetuarLoginComSucesso uc01tc01;

}
```

Dessa forma:

- O estado global é preparado uma única vez
- Cada Script aplica apenas seu estado específico
- Não há acoplamento entre estado e lógica de teste

## Checklist final

Antes de prosseguir, verifique se:

- ✅ Os arquivos SQL foram criados corretamente.
- ✅ O datasource `probato` está configurado no `configuration.yml`.
- ✅ Os scripts SQL são executados antes dos testes.
- ✅ O cenário é executado com estado previsível e controlado.

Com a implementação de Database concluída, a automação passa a ser **reprodutível, previsível e confiável**.
