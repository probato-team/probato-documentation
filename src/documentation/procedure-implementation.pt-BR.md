# Implementação de Procedure

Nesta seção será implementada uma **Procedure de teste básica**, responsável pela **execução da lógica do cenário** definido anteriormente no Script de login com sucesso. A Procedure é o ponto onde o comportamento do sistema é efetivamente exercitado. Ela executa ações, interage com a aplicação e realiza validações, sempre no contexto de um Script.

No Probato, uma Procedure pode ser implementada de **duas formas**:

- Como método dentro do Script
- Como classe dedicada reutilizável

## Implementando Procedure como método no Script

Essa abordagem é indicada para cenários simples, com lógica curta e sem necessidade de reutilização.

1. Abra a classe `UC01TC01_EfetuarLoginComSucesso.java`.
2. Adicione um método anotado com `@Procedure`.

```java title="UC01TC01_EfetuarLoginComSucesso.java" linenums="1" hl_lines="13-16"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Script;
import org.probato.api.Procedure;

@Script(
    code = "UC01TC01",
    name = "Efetuar login com sucesso",
    description = "Valida o cenário de autenticação do usuário com credenciais válidas"
)
public class UC01TC01_EfetuarLoginComSucesso {

    @Procedure
    private void procedure() {
        System.out.println("Executando procedure principal");
    }

}
```

Nesse modelo, o método anotado com `@Procedure` representa a **execução principal do cenário**.

### Separando pré-condição e pós-condição

Caso seja necessário diferenciar etapas do cenário, podem ser definidos métodos específicos.

```java title="UC01TC01_EfetuarLoginComSucesso.java" linenums="1" hl_lines="15-28 20-23 25-28"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Script;
import org.probato.api.Procedure;
import org.probato.api.Precondition;
import org.probato.api.Postcondition;

@Script(
    code = "UC01TC01",
    name = "Efetuar login com sucesso",
    description = "Valida o cenário de autenticação do usuário com credenciais válidas"
)
public class UC01TC01_EfetuarLoginComSucesso {

    @Precondition
    private void precondition() {
        System.out.println("Executando pré-condição");
    }

    @Procedure
    private void procedure() {
        System.out.println("Executando procedure principal");
    }

    @Postcondition
    private void postcondition() {
        System.out.println("Executando pós-condição");
    }

}
```

Essa separação melhora a legibilidade, rastreabilidade e diagnóstico de falhas.

## Implementando Procedure como classe dedicada

Essa abordagem é recomendada quando a lógica:

- É mais complexa
- recisa ser reutilizada
- Deve ser isolada do Script

1. Crie a classe `EfetuarLoginComSucessoProcedure.java`.

```java title="DoLoginSuccessfullyProcedure.java" linenums="1" hl_lines="7-10"
package org.probato.manager.usecase.UC01.procedure;

import org.probato.api.Run;

public class EfetuarLoginComSucessoProcedure {

    @Run
    private void procedure() {
        System.out.println("Executando procedure principal");
    }

}
```

A anotação `@Run` indica o ponto de entrada da execução da Procedure.

## Associando a Procedure ao Script

Após criar a classe de Procedure, ela deve ser associada ao Script.

```java title="UC01TC01_EfetuarLoginComSucesso.java" linenums="1" hl_lines="14-15"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Script;
import org.probato.api.Procedure;
import org.probato.manager.usecase.UC01.procedure.EfetuarLoginComSucessoProcedure;

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

Nesse modelo, o Script continua declarativo, enquanto a lógica fica encapsulada na Procedure.

## Executando neste estágio

Ao executar o projeto neste ponto:

- O Probato localizará a Procedure associada
- Executará os métodos anotados corretamente
- Exibirá as saídas no console

Isso confirma que o fluxo Script → Procedure está funcionando.

## Checklist Final

Antes de prosseguir, verifique se:

- ✅ A Procedure foi implementada corretamente.
- ✅ O Script referencia a Procedure.
- ✅ O projeto compila sem erros.
- ✅ Os métodos de pré-condição, execução e pós-condição são executados.

Com a Procedure implementada, o próximo passo será criar os **Page Objects**, responsáveis por encapsular as interações com a interface.

➡️ Continue em **Implementação de Page Object**.
