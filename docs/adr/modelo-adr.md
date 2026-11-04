# ADR-001 — Escolha da arquitetura do Connexa

- **Situação:** aceita
- **Data:** 2026-11-04
- **Participantes:** Rafael Inacio, Gabriel Ribeiro, Pedro Miranda, Lucas Loiro

## Contexto

O Connexa é uma plataforma para ajudar estudantes a encontrar grupos de estudo compatíveis com suas disciplinas e horários disponíveis. Além disso, o sistema permitirá organizar encontros e acompanhar a atividade dos grupos, oferecendo informações para monitores e coordenadores.

O projeto será desenvolvido durante o semestre por uma equipe pequena, com prazo limitado. Por isso, precisamos de uma arquitetura que seja simples de desenvolver, fácil de organizar e que permita implementar as funcionalidades gradualmente.

Também precisamos considerar requisitos como autenticação por e-mail institucional, proteção dos dados dos estudantes, acessibilidade e utilização em dispositivos móveis.

## Decisão

Adotaremos uma arquitetura de **monolito modular**, utilizando **C# com ASP.NET Core (.NET 10)** no back-end, **React com TypeScript** no front-end e **PostgreSQL** como banco de dados.

O sistema será organizado em módulos relacionados às funcionalidades do Connexa, permitindo desenvolver e testar cada parte de maneira independente, sem a necessidade de criar vários serviços separados.

## Alternativas consideradas

| Alternativa | Por que não foi escolhida |
|---|---|
| Microsserviços | Exigiriam mais configurações, comunicação entre serviços e manutenção, aumentando a complexidade para o tamanho da equipe e o prazo disponível. |
| Node.js com TypeScript | Seria uma opção válida, mas a equipe escolheu trabalhar com C# e .NET, aproveitando o template fornecido pelo professor. |
| Java com Spring Boot | Também atenderia aos requisitos, mas não foi a tecnologia escolhida pela equipe para este projeto. |

## Consequências

- **Positivas:** facilita a organização do código, permite desenvolver as funcionalidades por etapas e simplifica os testes e a manutenção. Também aproveita a estrutura inicial do template .NET disponibilizado pelo professor.
- **Negativas:** como todos os módulos fazem parte da mesma aplicação, será necessário manter uma boa separação de responsabilidades. Mudanças em uma parte do sistema também poderão exigir novos testes em outras partes.
- **Como verificar:** realizar revisões de código nos Pull Requests, executar testes automatizados no GitHub Actions e conferir se as funcionalidades estão organizadas nos módulos definidos, evitando dependências desnecessárias.
