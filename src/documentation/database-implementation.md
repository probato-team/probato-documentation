# Database Implementation

In this section, the **Database** concept will be implemented. It is responsible for preparing the **persistent state of the application** as a prerequisite for executing the **successful login** test scenario in **Probato**. In Probato, Database is used to **define state**, not to execute test logic. SQL or NoSQL scripts are declared explicitly and executed automatically before scenarios run.

## Creating the SQL files

1. In the `src/test/resources/sql` directory, create a folder named `init`.
2. In the `src/test/resources/sql` directory, create another folder named `user`.
3. Inside `src/test/resources/sql/init`, create the file `init.sql`.
4. Inside `src/test/resources/sql/user`, create the file `insert-user.sql`.

### Global initialization script

The `init.sql` script is used to prepare the **global state** of the feature and is executed before all Scripts in the Suite.

```sql
DELETE FROM testano_app.users;
```

### Scenario data script

The `insert-user.sql` script is used to prepare the **scenario-specific state**, inserting the users required for the login test.

```sql
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

## Updating the Script class

The Script can declare **scenario-specific state** through the `@SQL` annotation.

```java title="UC01TC01_DoLoginSuccessfully.java" linenums="1" hl_lines="9-11"
@Dataset("dataset/UC01/UC01TC01.csv")
@SQL(
    datasource = "probato",
    scriptPath = { "sql/user/insert-user.sql" }
)
@Script(
    code = "UC01TC01",
    name = "Do login successfully",
    description = "Validates the user authentication scenario with valid credentials"
)
public class UC01TC01_DoLoginSuccessfully {

    @Procedure
    private DoLoginSuccessfullyProcedure procedure;

}
```

At this point:

- The Script declares which specific state it requires
- The Database is prepared automatically before execution
- The Procedure remains focused only on business logic

## Updating the Suite class

The Suite can declare **global feature state**, applied before all Scripts.

```java title="UC01_Login.java" linenums="1" hl_lines="5-8"
@SQL(
    datasource = "probato",
    scriptPath = { "sql/init/init.sql" }
)
@Suite(
    code = "UC01",
    name = "Do Login",
    description = "Validates the user authentication functionality in the system"
)
class UC01_Login {

    @TestCase
    private UC01TC01_DoLoginSuccessfully uc01tc01;

}
```

This ensures that:

- The global state is prepared only once
- Each Script applies only its specific state
- There is no coupling between state and test logic

## Final Checklist

Before proceeding, make sure that:

- ✅ The SQL files were created correctly.
- ✅ The `probato` datasource is configured in `configuration.yml`.
- ✅ The SQL scripts are executed before test execution.
- ✅ The scenario runs with a predictable and controlled state.

With the Database implementation completed, automation becomes **reproducible, predictable, and reliable**.
