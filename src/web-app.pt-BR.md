# Aplicação Web

A aplicação Web do **Probato** é responsável por centralizar, organizar e disponibilizar os dados coletados durante a execução dos testes automatizados.

Ela atua como um ponto de observabilidade do processo de automação, permitindo análise de resultados, acompanhamento histórico e visualização de métricas de qualidade.

Assim como os demais componentes do projeto, a aplicação Web é uma **proposta em evolução**, aberta a ajustes conforme novas necessidades surgirem.

---

## Objetivo da aplicação Web

O principal objetivo da aplicação Web é resolver um problema recorrente na automação de testes:

- Resultados dispersos em logs, relatórios isolados ou pipelines
- Evidências difíceis de localizar
- Pouca visibilidade para além do time técnico

A aplicação centraliza essas informações, tornando-as acessíveis e compreensíveis para diferentes perfis.

---

## Distribuição e execução

A aplicação Web é distribuída como uma imagem Docker, permitindo execução em:

- Ambiente local
- Servidores dedicados
- Ambientes de integração contínua (CI/CD)

Essa abordagem facilita a adoção e a integração com diferentes infraestruturas.

---

## Dados coletados

Durante a execução dos testes, a aplicação Web pode armazenar informações como:

- Identificação do projeto e da suíte de testes
- Cenários, pré-condições e pós-condições
- Passos executados e ações realizadas
- Resultado das execuções
- Evidências (screenshots e vídeos)
- Massa de dados utilizada
- Scripts SQL executados
- Navegadores, sistema operacional e resolução
- Data, hora e duração das execuções

O conjunto de dados armazenados **não é fixo** e pode evoluir conforme novas necessidades surgirem.

---

## Visualização e análise

Por meio da interface Web, é possível:

- Consultar execuções individuais
- Navegar pelo histórico de testes
- Analisar falhas recorrentes
- Acessar evidências associadas às execuções

A proposta é facilitar investigações técnicas e análises de estabilidade ao longo do tempo.

---

## Métricas e indicadores

A aplicação Web permite a visualização de métricas de qualidade, como:

- Taxa de sucesso e falha
- Evolução da estabilidade
- Frequência de falhas por cenário ou funcionalidade
- Impacto de mudanças entre versões

Essas métricas representam um **modelo inicial**, aberto à evolução e à contribuição da comunidade.

---

## Uso progressivo

Embora a aplicação ofereça funcionalidades avançadas, seu uso pode ser **progressivo**:

- Execuções simples podem gerar apenas resultados básicos
- Ambientes mais maduros podem explorar métricas e histórico detalhado

Isso evita complexidade desnecessária em estágios iniciais.

---

## Integração com pipelines

A aplicação Web **não substitui pipelines de CI/CD**.

Ela atua como complemento, consolidando informações geradas por execuções automatizadas realizadas em diferentes ambientes.

Essa integração permite histórico contínuo e comparações entre execuções.

---

## Público-alvo

A aplicação Web atende diferentes perfis:

- Desenvolvedores, para análise técnica
- QA e Engenharia de Qualidade, para acompanhamento de execuções
- Gestores e stakeholders, para visão consolidada da qualidade

Cada perfil acessa o mesmo conjunto de dados, com diferentes níveis de interpretação.

---

## Evolução e colaboração

O modelo de dados, as métricas e as visualizações **não são definitivas**.

A evolução da aplicação Web depende de:

- Feedback da comunidade
- Novos casos de uso
- Discussões sobre métricas e indicadores

A colaboração é fundamental para que a aplicação se mantenha útil em diferentes contextos.

➡ Seção anterior: **[Biblioteca Java](library.md)** <br>
➡ Próxima seção: **[Projeto exemplo](examples.md)**
