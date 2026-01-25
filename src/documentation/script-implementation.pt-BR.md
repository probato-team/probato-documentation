# Implementação de Script

Nesta seção será implementado um **Script de teste básico**, responsável por representar um **cenário de teste** no Probato. O cenário implementado será o de **login realizado com sucesso** na aplicação **Probato Manager**.

O Script descreve **qual cenário será executado**, mas não contém lógica de execução — essa responsabilidade pertence às Procedures.

## Criando a classe Script

O Script pertence ao mesmo contexto da Suite e representa um cenário específico dentro da funcionalidade.

### Passo a passo

1. No pacote `org.probato.manager.usecase.UC01`, crie um novo pacote chamado `script`.
2. No pacote `org.probato.manager.usecase.UC01.script`, crie a classe `UC01TC01_EfetuarLoginComSucesso.java`.
3. Implemente o código abaixo:

```java title="UC01TC01_EfetuarLoginComSucesso.java" linenums="1"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Script;

@Script(
    code = "UC01TC01",
    name = "Efetuar login com sucesso",
    description = "Valida o cenário de autenticação do usuário com credenciais válidas"
)
public class UC01TC01_EfetuarLoginComSucesso {

}
```

O Script acima descreve apenas **a intenção do cenário**. Nenhuma ação é executada neste nível.

## Associando o Script à Suite

Após criar o Script, ele deve ser associado à Suite correspondente.

1. Abra a classe da Suite `UC01_EfetuarLogin`.
2. Adicione o Script como um campo anotado.

```java title="UC01_EfetuarLogin.java" linenums="1" hl_lines="14-15"
package org.probato.manager.usecase.UC01;

import org.probato.api.Suite;
import org.probato.api.TestCase;
import org.probato.manager.usecase.UC01.script.UC01TC01_EfetuarLoginComSucesso;

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

A anotação `@TestCase` indica ao Probato que este Script faz parte da execução da Suite.

## Executando neste estágio

Se o projeto for executado neste ponto, o Probato informará que:

> O Script deve possuir pelo menos uma Procedure.

Esse comportamento é esperado, pois o Script apenas descreve o cenário — a lógica será implementada no próximo passo.

## Checklist final

Antes de prosseguir, verifique se:

- ✅ A classe `UC01TC01_EfetuarLoginComSucesso` foi criada corretamente.
- ✅ O Script foi associado à Suite.
- ✅ O projeto compila sem erros.
- ✅ O cenário é reconhecido pelo JUnit 5.

Com o Script definido, o próximo passo é implementar a **Procedure**, responsável pela execução da lógica do cenário.

➡️ Continue em **Implementação de Procedure**.
