### Condição EXISTS.

Uma condição EXISTS testa a existência de linhas em uma subconsulta.

| **Tipo de condição** |                     **Operação**                      | **Exemplo**                                                                                                                                                   |
| :------------------: | :---------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|        EXISTS        | TRUE se uma subconsulta retornar pelo menos uma linha | SELECT department_id FROM departments d <br>WHERE EXISTS (SELECT \* FROM employees e <br>WHERE d.department_id = e.department_id) <br>ORDER BY department_id; |
