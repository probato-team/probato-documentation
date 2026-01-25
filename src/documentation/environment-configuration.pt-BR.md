# Configuração de Ambiente

A configuração correta do ambiente é o primeiro passo para utilizar o **Probato** de forma eficiente. Esta etapa garante que todas as ferramentas necessárias estejam disponíveis para criar, executar e evoluir projetos de automação de testes baseados no framework.

Esta seção foca **exclusivamente na preparação do ambiente**. Nenhum conceito do Probato é apresentado aqui — eles já foram tratados na seção *Conceitos*.

## Visão geral do ambiente necessário

Para trabalhar com o Probato, é necessário:

- Java Development Kit (JDK) 11 ou superior
- Apache Maven
- Uma IDE com suporte a Java

Esses componentes formam a base de execução do framework.

## Java Development Kit (JDK)

O **Java Development Kit (JDK)** é necessário para compilar e executar o código Java utilizado pelo Probato.

A versão mínima recomendada é **Java 11**.

### Opções de distribuição

Você pode utilizar qualquer distribuição compatível com Java 11 ou superior, como:

- [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html)
- [OpenJDK](https://jdk.java.net/)
- [Temurin](https://adoptium.net/)
- [Corretto](https://aws.amazon.com/pt/corretto/)

A escolha da distribuição não impacta o funcionamento do Probato.

### Configuração de variáveis de ambiente

#### Windows

1. Acesse **Editar variáveis de ambiente do sistema**
2. Em **Variáveis de Sistema**, clique em **Novo**:
   - Nome: `JAVA_HOME`
   - Valor: `C:\dev\java\jdk-11`
3. Edite a variável `Path` e adicione:
   ```
   %JAVA_HOME%\bin
   ```

#### Mac / Linux

Adicione as seguintes linhas ao arquivo `~/.bash_profile` ou `~/.zshrc`:

```bash
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
```

### Validação da instalação

Execute o comando:

```bash
java --version
```

Saída esperada:

```plaintext
java version "11.0.X"
Java(TM) SE Runtime Environment (build 11.0.X)
Java HotSpot(TM) 64-Bit Server VM (build 11.0.X)
```

Se a versão for exibida corretamente, o JDK está configurado.

## Apache Maven

O **Apache Maven** é utilizado pelo Probato para:

- Gerenciamento de dependências
- Execução de testes
- Automação de build

### Instalação

Faça o download no site oficial:

- https://maven.apache.org/download.cgi

Extraia o conteúdo para um diretório de sua preferência, por exemplo:

- Windows: `C:\dev\maven`
- Mac/Linux: `/usr/local/maven`

### Configuração de variáveis de ambiente

#### Windows

- Crie a variável:
  - Nome: `MAVEN_HOME`
  - Valor: `C:\dev\maven`
- Adicione ao `Path`:
  ```
  %MAVEN_HOME%\bin
  ```

#### Mac / Linux

Adicione ao `~/.bash_profile` ou `~/.zshrc`:

```bash
export MAVEN_HOME=/usr/local/maven
export PATH=$MAVEN_HOME/bin:$PATH
```

### Validação da instalação

Execute:

```bash
mvn -version
```

Saída esperada:

```plaintext
Apache Maven 3.X.X
Maven home: /usr/local/maven
Java version: 11.0.X
```

Se o Maven responder corretamente, a instalação está concluída.

## IDE (Ambiente de Desenvolvimento)

Uma IDE facilita a escrita, execução e depuração dos testes automatizados.

As opções mais utilizadas com o Probato são:

| IDE | Vantagem principal | Uso recomendado |
|-----|--------------------|----------------|
| :simple-eclipseide:{ .eclipseide } [Eclipse](https://www.eclipse.org/downloads/) | Leve e gratuito | Iniciantes |
| :simple-intellijidea:{ .intellijidea } [IntelliJ IDEA](https://www.jetbrains.com/idea/download/) | Recursos avançados | Projetos maiores |
| :material-microsoft-visual-studio-code:{ .visual-studio-code } [Visual Studio Code](https://code.visualstudio.com/download) | Leve e extensível | Projetos simples |

!!! note
    Independentemente da IDE escolhida, certifique-se de instalar os plugins necessários para suporte a Java e Maven.

## Checklist final

Antes de avançar para a criação do projeto, confirme:

- ✅ Java instalado e acessível (`java --version`)
- ✅ Maven instalado e acessível (`mvn -version`)
- ✅ IDE instalada e configurada

Com o ambiente configurado, você está pronto para criar seu primeiro projeto com o Probato.

➡️ Próximo passo: **Criação de Projeto**
