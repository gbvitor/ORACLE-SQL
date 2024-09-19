### Sobre as condições SQL.

O Oracle Database não aceita todas as condições em todas as partes de todas as instruções SQL. Consulte a seção dedicada a uma instrução SQL específica neste livro para obter informações sobre restrições nas condições dessa instrução.

#### Precedência de condição

Precedência é a ordem na qual o Oracle Database avalia diferentes condições na mesma expressão. Ao avaliar uma expressão que contém várias condições, a Oracle avalia as condições com precedência mais alta antes de avaliar aquelas com precedência mais baixa. O Oracle avalia condições com precedência igual da esquerda para a direita em uma expressão, com as seguintes exceções:

-  A avaliação da esquerda para a direita não é garantida para várias condições conectadas usando AND

-  A avaliação da esquerda para a direita não é garantida para várias condições conectadas usando OR

A Tabela lista os níveis de precedência entre a condição SQL de alto a baixo. As condições listadas na mesma linha têm a mesma precedência. Como a tabela indica, a Oracle avalia os operadores antes das condições.

|                       **Tipo de condição**                       |                                                                               **Propósito**                                                                                |
| :--------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|   Os operadores SQL são avaliados antes das<br> condições SQL    | Consulte [Precedência do Operador](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/About-SQL-Operators.html#GUID-FEF44762-F45C-41D9-B380-F6A61AD25338) |
|                       =, !=, <, >, <=, >=,                       |                                                                                 comparação                                                                                 |
| IS [NOT] NULL, LIKE, [NOT] BETWEEN, [NOT] IN, EXISTS, IS OF type |                                                                                 comparação                                                                                 |
|                               NOT                                |                                                                       exponenciação, negação lógica                                                                        |
|                               AND                                |                                                                                 conjunção                                                                                  |
|                                OR                                |                                                                                 disjunção                                                                                  |
