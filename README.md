# BD-Oficina
 Construindo um Esquema Conceitual para Banco De dados de uma Oficina DIO

# 🛠️ Desafio DIO - Esquema Conceitual Oficina Mecânica

## 📘 Descrição do Projeto

Este repositório contém o esquema conceitual criado para o sistema de controle e gerenciamento de ordens de serviço em uma **oficina mecânica**, proposto como desafio pela Digital Innovation One (DIO). O projeto foi desenvolvido com base em uma narrativa fornecida, simulando um cenário real de uma oficina que atende clientes pessoa física (PF) ou jurídica (PJ), realizando consertos e revisões em veículos.

---

## 🎯 Objetivo

Construir o **modelo conceitual** (diagrama EER) que representa as entidades, atributos e relacionamentos envolvidos na gestão de:

- Clientes
- Veículos
- Ordens de Serviço (OS)
- Peças
- Serviços
- Equipes de Mecânicos

---

## 🧱 Entidades Principais

- **Cliente**: identifica os clientes PF ou PJ que levam seus veículos à oficina.
- **Veículo**: cada veículo pertence a um cliente.
- **Equipe**: equipes compostas por mecânicos que executam os serviços.
- **Mecânico**: profissionais com especialidade, atribuídos a equipes.
- **Ordem de Serviço (OS)**: documento que registra os serviços e peças aplicados a um veículo.
- **Serviço**: descrição e preço de mão de obra, conforme tabela de referência.
- **Peça**: peças aplicadas aos veículos durante o serviço.

---

## 🔗 Relacionamentos

- Um **cliente** pode ter vários **veículos** (1:N).
- Um **veículo** pode ter várias **ordens de serviço** (1:N).
- Uma **ordem de serviço** é atribuída a uma **equipe** (1:N).
- Uma **equipe** possui vários **mecânicos** por meio da tabela associativa `Equipe_Mecanico` (N:N).
- Uma **ordem de serviço** pode conter vários **serviços** e **peças** (ambos N:N com tabelas associativas `OS_Servico` e `OS_has_Peca`).
- Cada **serviço** e **peça** contribui para o valor total da OS.

---

## ⚙️ Observações de Modelagem

- Utilizamos **tabelas associativas** para modelar os relacionamentos N:N entre ordens de serviço e serviços/peças.
- O campo `status` da OS foi definido como `VARCHAR`, mas pode futuramente ser alterado para um `ENUM` com status controlados (`Pendente`, `Autorizada`, `Concluída`, etc).
- Todos os campos de valor estão como `VARCHAR(45)` neste estágio inicial, mas idealmente seriam do tipo `DECIMAL` para precisão em dados financeiros.
- O campo `tipo` do cliente pode assumir valores como `'PF'` ou `'PJ'` para distinguir o tipo de pessoa atendida.

---

## 🛠️ Ferramentas Utilizadas

- [MySQL Workbench](https://www.mysql.com/products/workbench/) para modelagem do banco de dados.
