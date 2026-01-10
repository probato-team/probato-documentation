# **Configuração de Ambiente**

Configurar corretamente o ambiente de desenvolvimento é o primeiro passo para aproveitar todo o potencial do **Probato**, um framework poderoso para automação de testes. Este guia detalha os passos necessários para configurar ferramentas essenciais, como JDK, Maven e uma IDE, garantindo um ambiente pronto para criar e executar testes automatizados.

## **Instalar o JDK**

O **Java Development Kit (JDK)** é necessário para compilar e executar o código Java utilizado pelo **Probato**. Certifique-se de instalar a versão 11 ou superior.

### Baixar o JDK

Acesse um dos links abaixo para fazer o download do JDK:

* [Oracle JDK](https://www.oracle.com/java/technologies/javase-downloads.html)

* [OpenJDK](https://jdk.java.net/)

* [Adoptium](https://adoptium.net/)

* [Amazon Corretto](https://aws.amazon.com/pt/corretto/)

### Configurar Variáveis de Ambiente

**No Windows**:

* Acesse "Editar variáveis de ambiente do sistema".

* Em **Variáveis de Sistema**, clique em **Novo**:
      * Nome: `JAVA_HOME`
      * Valor: `C:\dev\java\jdk-11`

* Edite a variável `Path` e adicione: `%JAVA_HOME%\bin`

**No Mac/Linux**:
      
* Adicione as seguintes linhas ao arquivo `~/.bash_profile` ou `~/.zshrc`:
```bash
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
```

### Validar a instalação
   ```bash
   java --version
   ```
   A saída esperada:
   ```plaintext
   java version "11.0.X"
   Java(TM) SE Runtime Environment (build 11.0.X)
   Java HotSpot(TM) 64-Bit Server VM (build 11.0.X)
   ```
**OBS:** Caso visualize uma saída semelhante à apresentada acima, isso significa que o Java JDK foi instalado com sucesso.

## **Instalar o Maven**

O Maven é usado para gerenciar as dependências do projeto e automatizar processos de build.

### Baixar e Instalar

Acesse o site oficial do [Apache Maven](https://maven.apache.org/download.cgi), baixe o arquivo ZIP e extraia para `C:\dev\maven` (Windows) ou `/usr/local/maven` (Mac/Linux) ou outra de sua preferência.

### Configurar Variáveis de Ambiente

**No Windows**:

* Adicione uma nova variável:
      * Nome: `MAVEN_HOME`
      * Valor: `C:\dev\maven`
* Inclua `%MAVEN_HOME%\bin` no `Path`.

**No Mac/Linux**:

* Adicione ao arquivo `~/.bash_profile` ou `~/.zshrc`:
```bash
export MAVEN_HOME=/usr/local/maven
export PATH=$MAVEN_HOME/bin:$PATH
```

### Valide a instalação
   ```bash
   mvn -version
   ```
   A saída esperada:
   ```plaintext
   Apache Maven 3.X.X
   Maven home: /usr/local/maven
   Java version: 11.0.X, vendor: Oracle Corporation
   OS name: "mac os x", version: "10.15.7", arch: "x86_64"
   ```
**OBS:** Caso visualize uma saída semelhante à apresentada acima, isso significa que o Maven foi instalado com sucesso.

## **Escolher uma IDE**

Uma IDE (Ambiente de Desenvolvimento Integrado) facilita a escrita, execução e depuração de código Java. Aqui estão algumas opções populares:

| **IDE** | **Vantagem Principal** | **Uso Recomendado** |
|-----|--------------------|-----------------|
| :simple-eclipseide:{ .eclipseide } Eclipse | Leve e gratuito | Para iniciantes |
| :simple-intellijidea:{ .intellijidea } IntelliJ | Recursos avançados | Para desenvolvedores avançados |
| :material-microsoft-visual-studio-code:{ .visual-studio-code } VS Code | Moderno e extensível | Para projetos Java simples |

!!! note
    Escolha a IDE que melhor atende às suas necessidades. Certifique-se de instalar os plugins necessários para suporte ao Java.

## **Checklist Final**

Antes de prosseguir para a criação do projeto, verifique se:

- ✅ Java JDK instalado e configurado (`java --version` funcionando).
- ✅ Maven instalado e configurado (`mvn -version` funcionando).
- ✅ IDE instalada e pronta para uso.

Seu ambiente está configurado! Agora você está pronto para criar projetos no Probato.
