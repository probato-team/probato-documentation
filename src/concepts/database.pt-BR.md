# Database

O conceito de **Database** no Probato representa o **estado da aplicação** necessário para a execução de um cenário de teste. Ele permite preparar, validar ou limpar dados de forma declarativa, sem misturar estado com lógica de execução. No modelo mental do Probato, Database trata **estado**, não comportamento.

O Probato oferece suporte a **scripts SQL e NoSQL**, permitindo preparar estados tanto em bancos relacionais quanto não relacionais.

## Papel do Database no Probato

O Database é responsável por:

- Preparar o estado da aplicação antes da execução
- Garantir previsibilidade e reprodutibilidade dos testes
- Isolar dependências externas da lógica de teste
- Manter o código de execução limpo e focado

> O Database responde à pergunta: *Em qual estado o sistema deve estar antes da execução?*

## Onde o Database se encaixa no modelo mental

``` title="Modelo conceitual" hl_lines="2-3 6-7"
Suite
 ├── SQL (estado global / pré-condições da funcionalidade)
 ├── NoSQL (estado global / pré-condições da funcionalidade)
 └── Script
      ├── Dataset (dados de execução)
      ├── SQL (estado específico do cenário)
      ├── NoSQL (estado específico do cenário)
      ├── Precondition
      │     └── Page Object
      │           ├── Action
      │           └── Param
      ├── Procedure
      │     └── Page Object
      │           ├── Action
      │           └── Param
      └── Postcondition
            └── Page Object
                  ├── Action
                  └── Param
```

Scripts SQL e NoSQL podem ser aplicados tanto no nível da Suite quanto no nível do Script.

## Database no nível da Suite

Quando definido na **Suite**, o Database representa um **estado global** da funcionalidade.

Características:

- Aplicado antes da execução dos Scripts
- Compartilhado por todos os cenários da Suite
- Ideal para dados comuns e pré-requisitos gerais

Exemplos de uso:

- Carga inicial de dados
- Configuração de usuários padrão
- Preparação de ambiente funcional

## Database no nível do Script

Quando definido no **Script**, o Database representa um **estado específico do cenário**.

Características:

- Aplicado apenas para aquele Script
- Não afeta outros cenários
- Ideal para dados específicos ou variações de estado

Exemplos de uso:

- Usuário bloqueado
- Dados inválidos
- Estados transitórios

## Separação entre estado e lógica

No Probato:

- Database **não executa lógica de teste**
- Procedures **não manipulam estado diretamente**
- Scripts apenas declaram qual estado é necessário

Essa separação garante:

- Testes mais previsíveis
- Menor acoplamento
- Facilidade de manutenção

## Boas práticas

- Utilize Database apenas quando necessário
- Prefira estado mínimo para cada cenário
- Evite dependência entre execuções
- Mantenha scripts SQL e NoSQL simples e claros

## Considerações finais

O uso correto do Database é fundamental para garantir testes confiáveis e reprodutíveis.  
Ele deve ser tratado como **infraestrutura de suporte**, nunca como parte da lógica de validação.

## Próximo passo

Com todos os conceitos compreendidos, o próximo passo é avançar para os **Guias** ou **Configurações**, onde o uso prático do framework é detalhado.
