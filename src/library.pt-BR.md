# Biblioteca Java

A biblioteca Java do **Probato** é o núcleo da proposta de automação de testes funcionais end-to-end (E2E).

Ela foi concebida para **centralizar e organizar boas práticas**, padrões e utilitários amplamente utilizados na automação, reduzindo decisões repetitivas e o custo de manutenção dos testes ao longo do tempo.

A biblioteca não se propõe a ser um framework definitivo ou fechado, mas sim uma **base estruturada**, aberta a adaptações conforme o contexto de cada projeto.

---

## Objetivo da biblioteca

O principal objetivo da biblioteca do Probato é tornar a automação de testes funcionais:

- Mais simples de iniciar
- Mais consistente ao longo do tempo
- Mais fácil de manter e evoluir
- Menos dependente de soluções improvisadas

Ela busca reduzir a complexidade inicial sem impedir customizações avançadas quando necessárias.

---

## Abordagem adotada

A biblioteca não reinventa ferramentas consolidadas. Pelo contrário, ela **centraliza e organiza** o uso de soluções já amplamente adotadas no mercado, como Selenium, adicionando:

- Padrões de projeto bem definidos
- Estrutura baseada em Page Objects
- API simples, orientada a anotações
- Reutilização de código
- Configuração mínima para execução

A proposta é padronizar o essencial, mantendo flexibilidade onde o contexto exigir.

---

## Funcionalidades principais

Entre os recursos oferecidos pela biblioteca, destacam-se:

- Execução de testes funcionais em múltiplos navegadores
- Configuração simplificada de ambientes de execução
- Gerenciamento de massa de dados
- Execução de scripts SQL
- Suporte a múltiplos bancos de dados
- Coleta automática de informações de contexto da execução
- Geração de evidências, como screenshots e vídeos

Esses recursos refletem necessidades comuns encontradas em projetos reais de automação.

---

## API e padrão de uso

A API da biblioteca foi projetada para ser:

- Simples
- Declarativa
- Focada em legibilidade

A implementação dos testes é baseada principalmente em:

- Anotações
- Classes Page Object
- Configurações externas

Essa abordagem reduz código repetitivo e facilita a compreensão dos testes, especialmente em equipes com diferentes níveis de maturidade.

---

## Escopo da biblioteca

É importante alinhar expectativas quanto ao escopo da biblioteca:

- Ela **não cobre todos os cenários possíveis** de automação
- Não elimina a necessidade de decisões arquiteturais locais
- Não substitui completamente outras bibliotecas ou soluções específicas

A biblioteca oferece uma base inicial sólida, que pode ser estendida ou adaptada conforme a necessidade.

---

## Uso independente e integração

A biblioteca do Probato pode ser utilizada de forma **independente**, sem a necessidade da aplicação Web.

Quando integrada à aplicação Web, ela passa a enviar automaticamente dados de execução, evidências e informações de contexto, potencializando análises e métricas de qualidade.

Essa integração é **opcional**, permitindo adoção gradual.

---

## Público-alvo

A biblioteca foi pensada para atender:

- Equipes iniciantes em automação, que buscam padronização
- Times maduros que desejam reduzir esforço operacional
- Projetos que precisam de consistência entre diferentes suítes de teste

Ela busca apoiar diferentes níveis de maturidade sem impor rigidez excessiva.

---

## Evolução da biblioteca

As decisões técnicas e os padrões adotados **não são definitivos**.

A evolução da biblioteca depende diretamente de:

- Uso prático
- Feedback da comunidade
- Discussões técnicas
- Sugestões de melhoria

A proposta é evoluir de forma incremental e colaborativa.

➡ Próxima seção: **[Aplicação Web](web-app.md)**
