# **Exemplo**

Esta seção apresenta projetos oficiais que demonstram a utilização do
**Probato** em cenários reais de automação. Os exemplos foram estruturados para servir como referência prática de arquitetura, organização e boas práticas recomendadas.

------------------------------------------------------------------------

# **Probato Manager Automation**

O projeto **Probato Manager Automation** é um exemplo completo de
automação da aplicação **Probato Manager**, demonstrando a estrutura
modular proposta pelo framework.

🔗 [**Repositório oficial**](https://github.com/probato-team/probato-manager-automation)

------------------------------------------------------------------------

## **Objetivo do Projeto**

Este projeto demonstra:

-   Implementação de **Suite**
-   Organização de **Scripts**
-   Separação de responsabilidades com **Procedures**
-   Aplicação do padrão **Page Object**
-   Utilização de **Dataset (CSV)**
-   Execução de **Scripts SQL** como pré-condição
-   Execução em múltiplos navegadores
-   Configuração via `configuration.yml`

Ele serve como modelo de referência para equipes que desejam estruturar
seus projetos de automação com o Probato.

------------------------------------------------------------------------

## **Estrutura do Projeto**

A estrutura adotada no exemplo segue o padrão recomendado:

``` plaintext
probato-manager-automation/
├── src/
│   └── test/
│       ├── java/
│       │   └── org.probato.manager.automation/
│       │       ├── model/
│       │       ├── page/
│       │       └── usecase/
│       └── resources/
│           ├── dataset/
│           ├── sql/
│           └── configuration.yml
└── pom.xml
```

### **Descrição das Pastas**

-   `model/` → Classes de mapeamento de dados (Datamodel)
-   `page/` → Implementação dos Page Objects
-   `usecase/` → Suites, Scripts e Procedures organizados por
    funcionalidade
-   `dataset/` → Arquivos CSV com dados de teste
-   `sql/` → Scripts de preparação de base de dados
-   `configuration.yml` → Configuração central da execução

------------------------------------------------------------------------

## **Exemplo Simplificado**

### Suite

``` java
@Suite(
  code = "UC01",
  name = "Perform login",
  description = "Allow user to login")
class UC01_PerformLogin implements TestSuite {

  @TestCase
  private UC01TC01_PerformLoginSuccessfully uc01tc01;
}
```

------------------------------------------------------------------------

### Script

``` java
@Script(
  code = "UC01TC01",
  name = "Perform login successfully",
  description = "Validate successful login")
public class UC01TC01_PerformLoginSuccessfully {

  @Page
  private LoginPage loginPage;

  @Procedure
  private void procedure(LoginModel model) {
    loginPage.checkPage();
    loginPage.fillEmail(model.getEmail());
    loginPage.fillPassword(model.getPassword());
    loginPage.pressAccessButton();
  }
}
```

------------------------------------------------------------------------

## **Boas Práticas Demonstradas**

Este projeto evidencia princípios fundamentais do Probato:

-   Separação clara entre estrutura e lógica de execução
-   Organização orientada a negócio (Use Case → Script → Procedure)
-   Reutilização por meio de Page Objects
-   Isolamento e repetibilidade com SQL e Dataset
-   Configuração centralizada

------------------------------------------------------------------------

## **Quando Utilizar Este Exemplo**

Recomendado para:

-   Equipes iniciando com Probato
-   Projetos que exigem organização modular
-   Automação com integração de banco de dados
-   Implementação multi-browser
-   Referência arquitetural para novos projetos

------------------------------------------------------------------------

## **Como Executar**

1.  Clonar o repositório:

``` bash
git clone https://github.com/probato-team/probato-manager-automation
```

2.  Ajustar o `configuration.yml` conforme seu ambiente.

3.  Executar via Maven:

``` bash
mvn test
```

------------------------------------------------------------------------

# **Contribuições**

Caso deseje contribuir com exemplos adicionais:

-   Fork do repositório
-   Submissão de Pull Request
-   Proposta de novos cenários de referência
-   Integrações com CI/CD

A evolução dos exemplos faz parte do crescimento do ecossistema Probato.
