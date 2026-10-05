# 📊 Processando e Transformando Dados com Power BI

Projeto desenvolvido para o desafio **Processamento de Dados com Power BI e MySQL** da Formação Power BI Analyst da DIO.

## ⚠️ Adaptação do ambiente

O desafio original propõe o provisionamento de uma instância MySQL na Microsoft Azure. Neste projeto, a etapa de Azure foi **adaptada** porque a conta utilizada é corporativa e não permite criar recursos na Azure. Para manter o objetivo técnico do desafio, o repositório entrega:

- script MySQL completo para criação e carga do banco `company`;
- consultas SQL de validação;
- roteiro de transformações em Power Query (M);
- base final transformada em Excel e CSV;
- documentação das anomalias e decisões de tratamento.

O mesmo script pode ser executado em um MySQL local, Docker, DBeaver/MySQL Workbench ou, caso disponível, em uma instância MySQL na Azure.

## 🎯 Objetivo

Aplicar as etapas de coleta, obtenção e transformação de dados, preparando uma base relacional para análise no Power BI.

## 📂 Estrutura do repositório

```text
.
├── dados/
│   ├── company_transformado.xlsx
│   ├── employee.csv
│   ├── employee_department.csv
│   ├── manager_employee.csv
│   ├── department_location.csv
│   ├── employees_by_manager.csv
│   ├── employees_by_department.csv
│   └── hours_by_project.csv
├── sql/
│   ├── company_database.sql
│   └── consultas_validacao.sql
├── powerquery/
│   └── consultas_power_query.m
├── docs/
│   ├── checklist_desafio.md
│   └── validacoes.md
└── README.md
```

## 🧹 Transformações realizadas

1. Verificação de cabeçalhos e tipos de dados.
2. Conversão de `Salary` para tipo numérico decimal.
3. Análise de valores nulos.
4. Validação de `Super_ssn`: o único nulo é o gerente no topo da hierarquia.
5. Verificação de departamentos sem gerente.
6. Validação das horas registradas nos projetos.
7. Separação de `Address` em número, logradouro, cidade e estado.
8. Mescla de `employee` com `department` usando `employee` como tabela base e junção **Left Outer**.
9. Auto-mescla de `employee` para obter o nome do gerente de cada colaborador.
10. Criação do campo de nome completo `EmployeeName`.
11. Mescla de departamento e localização, criando `Store = Department - Location`.
12. Agrupamento para contabilizar colaboradores por gerente.
13. Remoção de colunas redundantes nas saídas transformadas.

## 🔎 Principais validações

- **8 colaboradores** no total.
- **3 departamentos**, todos com gerente.
- **1 colaborador sem gerente direto**: James E Borg, que representa o topo da hierarquia.
- **1 registro de horas nulo** em `works_on`, mantido e documentado para análise.

### Colaboradores por gerente

| Gerente | Qtd. colaboradores |
|---|---:|
| Franklin T Wong | 3 |
| James E Borg | 2 |
| Jennifer S Wallace | 2 |

### Colaboradores por departamento

| Departamento | Qtd. colaboradores |
|---|---:|
| Research | 4 |
| Administration | 3 |
| Headquarters | 1 |

## 🔀 Mesclar x Acrescentar

Neste desafio, **Mesclar** é a operação correta porque precisamos combinar atributos de entidades diferentes usando chaves (`Dno`, `Dnumber`, `Super_ssn`, `Ssn`). Isso equivale a um `JOIN`.

**Acrescentar** empilharia as linhas das tabelas, o que é adequado quando elas possuem a mesma estrutura. Como `employee`, `department` e `dept_locations` representam entidades diferentes, o append criaria muitas colunas vazias e não resolveria os relacionamentos.

## 🛠️ Como reproduzir

1. Execute `sql/company_database.sql` em um MySQL local ou Azure MySQL.
2. Execute `sql/consultas_validacao.sql` para conferir a consistência da base.
3. No Power BI Desktop, use **Obter Dados → Banco de dados MySQL**.
4. No Power Query, aplique as etapas documentadas em `powerquery/consultas_power_query.m`.
5. Caso não queira instalar MySQL, use diretamente `dados/company_transformado.xlsx` para explorar as tabelas já tratadas.

## 📚 Referências

- Repositório da formação: https://github.com/julianazanelatto/power_bi_analyst
- Documentação do desafio fornecida pela DIO na plataforma do curso.

## 👨‍💻 Autor

Projeto preparado como entrega do desafio da Formação Power BI Analyst da DIO.
