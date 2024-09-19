### Sobre operadores SQL.

Os operadores manipulam itens de dados individuais chamados operandos ou argumentos. Os operadores são representados por<br>
caracteres especiais ou por palavras-chave. Por exemplo, o operador de multiplicação é representado por um asterisco (\*).

#### Precedência dos operadores.

Precedência é a ordem na qual o Oracle Database avalia diferentes operadores na mesma expressão. Ao avaliar uma expressão que<br>
contém vários operadores, a Oracle avalia os operadores com maior precedência antes de avaliar aqueles com menor precedência.<br>
A Oracle avalia operadores com precedência igual da esquerda para a direita em uma expressão.

|                      **Operador**                       |                                                                                **Operação**                                                                                 |
| :-----------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|         +, -, prior,<br>connect_by_rootcollate          |                                                             Identidade, negação, localização na <br>hierarquia                                                              |
|                          \*, /                          |                                                                           Multiplicação, divisão                                                                            |
|            +, - (como operadores binários),             |                                                                       Adição, subtração, concatenação                                                                       |
| As condições SQL são avaliadas após os <br>operadoreSQL | Consulte [Precedência do Operador](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/About-SQL-Conditions.html#GUID-65B103FE-C00C-46A3-8173-A731DBF62C80) |
