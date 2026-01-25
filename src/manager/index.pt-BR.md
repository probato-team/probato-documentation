# Probato Manager

O **Probato Manager** é o componente responsável por **coletar, organizar e visualizar os resultados de execução** gerados pelo framework Probato. Enquanto o Probato é responsável pela **execução e orquestração dos testes**, o Manager foca em **observabilidade, métricas e geração de insights**.

## Objetivo do Probato Manager

O Probato Manager foi projetado para:

- Centralizar os resultados de execução
- Fornecer métricas e tendências de execução
- Oferecer visibilidade para stakeholders técnicos e não técnicos
- Apoiar a análise de qualidade ao longo do tempo

Ele **não executa testes** e **não interfere na lógica de execução**.

## Papel no ecossistema Probato

O Probato é composto por duas partes complementares:

- **Probato Framework** — executa e orquestra os testes
- **Probato Manager** — observa e analisa as execuções

```
Probato Framework ──▶ Dados de Execução ──▶ Probato Manager
```

O Manager consome os dados produzidos durante a execução e os transforma em informações relevantes.

## Quais dados são coletados

Durante a execução dos testes, o Probato pode enviar os seguintes dados para o Manager:

- Metadados de execução (projeto, suite, script, page object)
- Duração e status da execução
- Descrições de passos e parâmetros utilizados
- Evidências (capturas de tela, vídeos, logs)
- Histórico de execuções

Esses dados permitem análises detalhadas e geração de relatórios.

## Quem se beneficia do Probato Manager

O Probato Manager é útil para diferentes perfis:

### Engenheiros de QA

- Análise de falhas
- Identificação de testes instáveis (flaky tests)
- Acompanhamento do histórico de execuções

### Desenvolvedores

- Diagnóstico de problemas
- Entendimento do comportamento das execuções
- Validação de correções aplicadas

### Gestores e Stakeholders

- Acompanhamento de tendências de qualidade
- Monitoramento da estabilidade das execuções
- Avaliação da prontidão para releases

## Integração com o framework

A integração com o Probato Manager é controlada por **configuração**, e não por código.

Os passos típicos de integração incluem:

- Habilitar o envio de resultados
- Configurar endpoint e credenciais
- Definir quais dados serão coletados

Isso garante observabilidade sem poluir a lógica dos testes.

## Métricas e observabilidade

O Probato Manager possibilita:

- Dashboards de execução
- Análise de tendências históricas
- Categorização de falhas
- Inspeção de evidências

A observabilidade é tratada como um **conceito de primeira classe**, e não como algo secundário.

## Princípios arquiteturais

O Probato Manager segue os seguintes princípios:

- Observador passivo — não controla a execução
- Dados de execução imutáveis
- Visualização independente de ambiente
- Armazenamento e consulta escaláveis

Esses princípios garantem confiabilidade, rastreabilidade e evolução sustentável.

## Distribuição e execução via Docker

O **Probato Manager** é disponibilizado como uma imagem Docker oficial, facilitando sua instalação e execução em diferentes ambientes.

A imagem está disponível no **Docker Hub**, no repositório oficial do projeto:

- **Repositório:** `probato`
- **Imagem:** [`probato/probato-manager:latest`](https://hub.docker.com/r/probato/probato-manager)

A execução do Manager via Docker permite:

- Rápida inicialização do ambiente
- Padronização de execução entre equipes
- Fácil integração com pipelines e ambientes CI/CD

Detalhes sobre configuração, portas, volumes e variáveis de ambiente podem ser encontrados na documentação específica de deployment.

## Próximos passos

Para integrar o Probato Manager:

- Configure o envio de dados de execução
- Execute os testes normalmente
- Explore os resultados na interface do Manager

O Probato Manager completa o ecossistema Probato ao transformar dados de execução em **insights acionáveis**.
