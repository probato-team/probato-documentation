# Primeiros passos

Esta seção apresenta um ponto de partida para utilização do **Probato**.

O objetivo não é cobrir todos os cenários possíveis, mas oferecer um **caminho inicial simples**, permitindo que equipes com diferentes níveis de maturidade consigam experimentar a proposta, validar conceitos e evoluir gradualmente.

---

## Antes de começar

O Probato é composto por dois componentes independentes:

* **Biblioteca Java**: responsável pela execução dos testes automatizados
* **Aplicação Web**: responsável pela centralização de resultados, evidências e métricas

É possível utilizar apenas a biblioteca Java de forma isolada ou integrá-la à aplicação Web para obter maior visibilidade e histórico de qualidade.

---

## Pré-requisitos

Para utilizar a biblioteca Java do Probato, recomenda-se:

* Java 11 ou superior
* Maven ou Gradle
* Conhecimento básico em testes automatizados
* Familiaridade com Page Objects e testes funcionais

Para utilização da aplicação Web:

* Docker
* Navegador Web moderno

---

## Primeiros passos com a biblioteca

A adoção da biblioteca do Probato foi pensada para ser incremental.

De forma geral, o fluxo inicial envolve:

1. Adicionar a dependência da biblioteca ao projeto
2. Definir configurações básicas de execução
3. Criar Page Objects
4. Implementar cenários de teste utilizando anotações
5. Executar os testes

A biblioteca busca reduzir a quantidade de código necessário para estruturar testes funcionais, sem esconder conceitos importantes do processo de automação.

---

## Configuração inicial

As configurações iniciais da biblioteca envolvem, entre outros pontos:

* Navegadores de execução
* Ambiente alvo
* Diretórios de evidências
* Configurações de banco de dados

Essas configurações são mantidas internas ao código, onde podem ser criadas configurações distintas para anbientes diferentes, facilitando alternância das execuções entre ambientes e pipelines.

---

## Execução dos testes

Após a configuração básica, os testes podem ser executados localmente ou por meio de pipelines de integração contínua.

Durante a execução, a biblioteca coleta automaticamente informações como:

* Resultado dos testes
* Evidências
* Dados de ambiente
* Informações de contexto

Esses dados podem ser utilizados localmente ou enviados para a aplicação Web.

---

## Integração com a aplicação Web

A integração com a aplicação Web é **opcional**, mas recomendada para equipes que desejam:

* Centralizar resultados
* Manter histórico de execuções
* Visualizar métricas de qualidade

Quando configurada, a biblioteca envia automaticamente os dados das execuções para a aplicação Web.

---

## Uso progressivo

O Probato foi pensado para permitir uso progressivo:

* Projetos pequenos podem iniciar com poucos testes e configurações mínimas
* Times mais maduros podem explorar integrações, métricas e histórico

Não é necessário adotar todas as funcionalidades desde o início.

## Projeto exemplo

Além da documentação, o Probato conta com um projeto de automação de exemplo que demonstra, na prática, o uso da biblioteca automatizando a própria aplicação Probato Web. A aplicação Probato Web é utilizada como alvo no projeto de automação de exemplo

[Exemplo](https://github.com/probato-team/probato-sample-e2e)

---

## Próximos passos

Após os primeiros testes, recomenda-se:

* Explorar a documentação da [Biblioteca Java](library.md)
* Conhecer a [Aplicação Web](web-app.md)
* Veja o [Projeto de exemplo](examples.md)

O Probato é uma proposta em evolução, e o uso prático é parte fundamental desse processo.
