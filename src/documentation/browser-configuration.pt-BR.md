# Configuração de Browser

Esta seção descreve como configurar a execução de testes automatizados em diferentes navegadores no **Probato**. A execução multi-browser é um recurso fundamental para validar a compatibilidade da aplicação em ambientes reais, garantindo que os cenários sejam executados de forma consistente nos principais navegadores do mercado.

## Papel da configuração de browser no Probato

No Probato, browsers não são definidos no código de teste. Eles são configurados exclusivamente via arquivo de configuração, permitindo que o mesmo conjunto de testes seja executado em diferentes navegadores sem alterações no código.

Cada browser configurado gera uma execução independente de todos os cenários.

## Dependências necessárias

O suporte a browsers é habilitado por meio de módulos específicos do Probato.

No arquivo `pom.xml`, devem ser adicionadas as dependências correspondentes aos navegadores desejados.

```xml title="pom.xml"
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
```

!!! note
    Apenas os navegadores com dependência adicionada poderão ser utilizados na execução.

## Configuração mínima de browser

A configuração mínima exige ao menos um browser definido no arquivo `configuration.yml`.

```yaml title="configuration.yml"
execution:
  target:
    url: http://localhost:8099
    version: 0.0.0

browsers:
- type: CHROME
```

Com essa configuração, os testes já podem ser executados com sucesso.

## Execução multi-browser

É possível definir múltiplos navegadores simultaneamente. Para cada browser configurado, o Probato executará todo o conjunto de testes novamente.

```yaml title="configuration.yml"
browsers:
- type: CHROME
- type: FIREFOX
- type: EDGE
```

!!! note
    Os navegadores configurados devem estar instalados na máquina de execução.

## Dimensionamento e modo de execução

Por padrão, os browsers são executados com janela maximizada. Entretanto, é possível controlar completamente o dimensionamento e o modo de execução.

```yaml title="configuration.yml"
browsers:
- type: CHROME
  headless: false
  dimension:
    mode: FULLSCREEN

- type: FIREFOX
  headless: true
  dimension:
    mode: MAXIMIZED

- type: EDGE
  dimension:
    mode: CUSTOM
    width: 1256
    height: 1018
```

## Propriedades de browser

| Propriedade | Descrição |
|------------|----------|
| browsers[].type | Tipo do navegador (CHROME, FIREFOX, EDGE) |
| browsers[].headless | Executa em modo headless |
| browsers[].dimension.mode | FULLSCREEN, MAXIMIZED ou CUSTOM |
| browsers[].dimension.width | Largura da janela (CUSTOM) |
| browsers[].dimension.height | Altura da janela (CUSTOM) |

## Timeouts e intervalos de execução

Os tempos de espera e intervalos entre ações são configurados globalmente no bloco `execution.delay`.

```yaml title="configuration.yml"
execution:
  delay:
    waitingTimeout: 5000
    actionInterval: 300
```

## Propriedades de delay

| Propriedade | Descrição |
|------------|----------|
| execution.delay.waitingTimeout | Tempo máximo de espera por ação |
| execution.delay.actionInterval | Intervalo entre ações |

## Considerações finais

A configuração de browser no Probato é declarativa, extensível e desacoplada do código.

Isso permite:

- reutilizar os mesmos testes em diferentes ambientes
- executar validações paralelas por navegador
- alterar comportamento sem recompilar o projeto

➡️ Próximo passo: **Implementação de Suite**
