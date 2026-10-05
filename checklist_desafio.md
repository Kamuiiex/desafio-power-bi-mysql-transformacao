# Checklist das transformações do desafio

Este arquivo mapeia cada item solicitado no material da DIO para a evidência preparada neste repositório.

| # | Requisito | Evidência / decisão |
|---|---|---|
| 1 | Verificar cabeçalhos e tipos | Tipos definidos em `powerquery/consultas_power_query.m` e abas do Excel. |
| 2 | Valores monetários em double/decimal | `Salary` tratado como número decimal. |
| 3 | Verificar nulos | `Super_ssn` e `Hours` analisados; resultados documentados em `docs/validacoes.md`. |
| 4 | `Super_ssn` nulo pode indicar gerente | James E Borg é o gerente de Headquarters e não possui gerente direto. |
| 5 | Departamento sem gerente | Nenhum departamento sem gerente. |
| 6 | Preencher lacunas de gerente se necessário | Não necessário nesta base. |
| 7 | Verificar horas dos projetos | `dados/hours_by_project.csv` e consulta SQL de validação. |
| 8 | Separar colunas complexas | `Address` separado em número, logradouro, cidade e estado. |
| 9 | Mesclar employee + department | LEFT OUTER com employee como base. |
| 10 | Eliminar colunas desnecessárias | Consultas transformadas deixam apenas campos úteis. |
| 11 | Colaborador + gerente | Self join por `Super_ssn = Ssn`. |
| 12 | Mesclar nome e sobrenome | Campo `EmployeeName`. |
| 13 | Departamento + localização | Campo `Store = Department - Location`. |
| 14 | Explicar mesclar x acrescentar | Explicação no README e em `docs/validacoes.md`. |
| 15 | Agrupar colaboradores por gerente | `dados/employees_by_manager.csv`. |
| 16 | Remover colunas sem uso | Aplicado nas saídas transformadas. |
