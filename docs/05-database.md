# Database

## Overview

O sistema utilizará PostgreSQL como banco de dados relacional e Django ORM como camada de acesso aos dados.

A modelagem foi projetada para priorizar consistência, integridade referencial e facilidade de evolução, acompanhando o crescimento do produto sem comprometer a organização dos dados.

---

## Objetivos da Modelagem

A modelagem do banco de dados busca atender aos seguintes objetivos:

- Representar corretamente o domínio do processo seletivo;
- Garantir integridade entre os dados;
- Evitar duplicação de informações;
- Facilitar consultas e relatórios;
- Permitir futuras evoluções do sistema.

---

## Entidades do Domínio

O MVP será composto pelas seguintes entidades principais:

### Usuário

Representa qualquer usuário autenticado na plataforma.

Possíveis perfis:

- Candidato
- Organizador

Responsabilidades:

- autenticação;
- informações pessoais;
- permissões.

---

### Processo Seletivo

Representa um processo seletivo criado por uma organização.

Exemplos:

- Processo Seletivo 2026.2
- Processo Seletivo 2027.1

Responsabilidades:

- período de inscrições;
- status;
- configuração geral;
- etapas.

---

### Etapa

Representa uma fase do processo seletivo.

Exemplos:

- Inscrição
- Dinâmica
- Entrevista
- Resultado Final

Responsabilidades:

- ordem;
- critérios;
- datas;
- status.

---

### Candidatura

Representa a participação de um candidato em um processo seletivo.

Responsabilidades:

- status atual;
- etapa atual;
- data de inscrição;
- histórico.

---

### Avaliação

Representa a avaliação realizada por um organizador.

Responsabilidades:

- nota;
- comentários;
- parecer;
- data.

---

### Notificação

Representa comunicações enviadas ao candidato.

Exemplos:

- confirmação de inscrição;
- convocação;
- aprovação;
- reprovação.

---

## Relacionamentos

Relacionamentos previstos:

```text
Usuário
      │
      ├────────────┐
      │            │
      ▼            ▼
Candidatura    Avaliação
      │            ▲
      ▼            │
Processo Seletivo──┘
      │
      ▼
Etapa

Notificação
      │
      ▼
Usuário
```

---

## Modelo Conceitual

O modelo conceitual será elaborado após a validação dos requisitos funcionais do sistema.

---

## Modelo Lógico

O modelo lógico será desenvolvido utilizando PostgreSQL e documentado conforme a evolução do projeto.

---

## Modelo Físico

As tabelas, índices, constraints e relacionamentos serão definidos durante a implementação.

---

## Índices

Os índices serão adicionados conforme necessidade.

Inicialmente, espera-se indexar campos como:

- e-mail;
- status da candidatura;
- processo seletivo;
- etapa atual;
- usuário.

---

## Auditoria

Sempre que possível serão armazenadas informações de auditoria para facilitar rastreabilidade.

Exemplos:

- data de criação;
- data de atualização;
- usuário responsável por alterações relevantes.

---

## Próximos Passos

Após a conclusão do levantamento de requisitos e definição do MVP, serão adicionados:

- Diagrama Entidade-Relacionamento (ER);
- Modelo lógico completo;
- Modelo físico do banco;
- Dicionário de dados;
- Regras de integridade.