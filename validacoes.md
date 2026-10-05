# Validações e anomalias encontradas

## 1. Valores nulos

- `employee.Super_ssn`: 1 nulo, pertencente a **James E Borg**. O registro é coerente: ele é o gerente de Headquarters e ocupa o topo da hierarquia.
- `works_on.Hours`: 1 nulo no projeto **Reorganization** para James E Borg. O valor foi mantido como nulo na base bruta e destacado na validação.

## 2. Departamentos sem gerente

Nenhum. Os três departamentos possuem `Mgr_ssn` preenchido e correspondente a um colaborador válido.

## 3. Colaboradores por gerente

| Gerente | Colaboradores |
|---|---:|
| Franklin T Wong | 3 |
| James E Borg | 2 |
| Jennifer S Wallace | 2 |

## 4. Colaboradores por departamento

| Departamento | Colaboradores |
|---|---:|
| Research | 4 |
| Administration | 3 |
| Headquarters | 1 |

## 5. Por que usar Mesclar e não Acrescentar?

**Mesclar (Merge)** combina tabelas horizontalmente usando uma chave em comum, equivalente a um `JOIN` relacional. É o comportamento necessário para enriquecer `employee` com o nome do departamento, associar colaboradores aos gerentes e relacionar departamentos às localizações.

**Acrescentar (Append)** concatena linhas de tabelas. Como as tabelas deste desafio representam entidades diferentes e têm colunas diferentes, acrescentá-las geraria uma estrutura esparsa, com muitos valores nulos, e não preservaria os relacionamentos entre as entidades.
