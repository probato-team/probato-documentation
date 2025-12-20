# Visão geral

**Uma proposta Open Source para automação de testes funcionais end-to-end (E2E).**

O Probato é uma iniciativa que busca tornar o processo de automação **mais viável, sustentável e acessível** para equipes e empresas de qualquer porte.

Ele não se propõe a ser uma solução definitiva ou completa, mas sim uma **base inicial**, construída a partir de necessidades reais, que evolui de forma colaborativa com a participação da comunidade.

O Probato nasce como um **ponto de partida estruturado** para discutir, experimentar e evoluir a automação de testes funcionais de forma coletiva.

---

## O problema que o Probato resolve

Na prática, a automação de testes funcionais costuma enfrentar desafios recorrentes:

- Uso disperso de múltiplas bibliotecas e utilitários
- Falta de padronização e reutilização de código
- Alto custo de manutenção dos testes ao longo do tempo
- Resultados e evidências espalhados em relatórios, logs e pipelines
- Pouca visibilidade do valor da automação para além do time técnico

Esses fatores tornam a automação frágil, difícil de escalar e, muitas vezes, inviável para a maioria dos projetos.

O **Probato** foi criado para atacar esses problemas de forma direta, oferecendo uma abordagem estruturada e integrada para automação de testes E2E.

---

## O que é o Probato

O **Probato** é uma proposta composta por dois grandes componentes que trabalham de forma complementar.

Juntos, eles permitem separar claramente **a execução dos testes** da **análise da qualidade**, mantendo organização, rastreabilidade e visibilidade ao longo do tempo.

### Biblioteca Java

A biblioteca Java é o núcleo da automação. Ela centraliza e organiza o uso de soluções amplamente consolidadas no mercado, como Selenium, adicionando:

- Padrões de projeto e boas práticas
- Reutilização de código
- API simples, orientada a anotações
- Estrutura baseada em Page Objects
- Configuração mínima para execução em múltiplos navegadores

A proposta não é reinventar ferramentas existentes, mas **organizar, padronizar e simplificar** seu uso em projetos reais.

### Aplicação Web

A aplicação Web tem como objetivo centralizar e dar visibilidade às informações coletadas durante as execuções dos testes.

Ela permite:

- Armazenar resultados e evidências de forma estruturada
- Manter histórico de execuções ao longo do tempo
- Visualizar dados técnicos e funcionais em um único local
- Acompanhar métricas e indicadores de qualidade

A forma como esses dados são coletados, armazenados e analisados **não é definitiva** e está aberta à evolução conforme novas necessidades, contextos e aprendizados surgirem.

---

## Proposta do Probato

A proposta central do **Probato** é funcionar como uma abordagem “receita de bolo” para automação de testes funcionais:

- Simples de adotar em novos projetos
- Fácil de desenvolver e evoluir
- Sustentável de manter ao longo do tempo
- Baseada em boas práticas consolidadas

O objetivo é reduzir a complexidade técnica e o esforço operacional, permitindo que equipes foquem na qualidade do software, e não na manutenção da automação.

---

## Métricas e visibilidade

Durante a execução dos testes, a biblioteca coleta uma ampla gama de informações técnicas e funcionais, que são enviadas automaticamente para a aplicação Web.

Essas informações permitem:

- Analisar a estabilidade das funcionalidades
- Identificar falhas recorrentes e pontos críticos
- Avaliar a evolução da qualidade ao longo do tempo
- Apoiar decisões técnicas e estratégicas com base em dados

A automação deixa de ser apenas um mecanismo de validação pontual e passa a ser uma fonte contínua de informação sobre a qualidade do produto.

---

## Para quem é

O **Probato** foi projetado para atender diferentes contextos e níveis de maturidade:

- Equipes pequenas que desejam iniciar a automação de forma organizada
- Times maduros que buscam padronização e visibilidade
- Empresas de médio e grande porte com múltiplos projetos
- Ambientes corporativos com pipelines de CI/CD

Sua arquitetura flexível permite adoção gradual, sem impor mudanças bruscas no ecossistema existente.

---

## Open Source e colaboração

O **Probato** é um projeto **Open Source** que se assume como uma proposta em evolução.

O projeto parte de uma visão inicial e de decisões técnicas que **não são finais**. A expectativa é que a comunidade participe ativamente com opiniões, sugestões e contribuições para complementar, ajustar e amadurecer a ferramenta ao longo do tempo.

A colaboração da comunidade é considerada um fator **essencial e fundamental** para que o Probato se adapte a diferentes contextos, realidades e necessidades.

---

## O que o Probato não se propõe a ser

Para alinhar expectativas, é importante deixar claro que o Probato:

- Não se propõe a ser um framework definitivo ou completo
- Não substitui todo o ecossistema existente de automação de testes
- Não cobre todos os cenários, contextos e necessidades possíveis

Trata-se de uma proposta inicial, aberta à evolução e adaptação conforme o uso prático e as contribuições da comunidade.

---

## Comece a usar

- [Começando](getting-started.md)
- [Biblioteca Java](library.md)
- [Aplicação Web](web-app.md)
- [Projeto de exemplo](examples.md)
- [Sobre o projeto](about.md)
