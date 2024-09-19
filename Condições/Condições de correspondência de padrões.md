### Condições de correspondência de padrões.

As condições de correspondência de padrões comparam dados de caracteres.

#### Condição LIKE

As condições especificam um teste envolvendo correspondência de padrões. Enquanto o operador de igualdade (=) corresponde exatamente a um valor de caractere a outro, as condições like correspondem a uma parte de um valor de caractere a outro pesquisando o primeiro valor para o padrão especificado pelo segundo. Calcula cadeias de caracteres usando caracteres conforme definido pelo conjunto de caracteres de entrada. usa caracteres completos Unicode. usa pontos de código UCS2. usa pontos de código UCS4.

Para processar as condições, o Oracle divide o padrão em subpadrões que consistem em um ou dois caracteres cada. Os subpadrões de dois caracteres começam com o caractere de escape e o outro caractere é %, ou \_, ou o caractere de escape. LIKE

Seja P1, P2, ..., Pn esses subpadrões. A condição semelhante é verdadeira se houver uma maneira de particionar o valor de pesquisa em substrings S1, S2, ..., Sn de modo que para todos i entre 1 e n:

-  Se Pi é \_, então Si é um único caractere.

-  Se Pi é %, então Si é qualquer string.

-  Se Pi são dois caracteres começando com um caractere de escape, então Si é o segundo caractere de Pi.

-  Caso contrário, Pi = Si.

Com as condições LIKE, você pode comparar um valor com um padrão em vez de uma constante. O padrão deve aparecer após a palavra-chave. Por exemplo, você pode emitir a seguinte consulta para localizar os salários de todos os funcionários com nomes que começam com :

```sql
SELECT salário
FROM Funcionários
WHERE last_name LIKE 'R%'
ORDER BY salário;
```

A consulta a seguir usa o operador =, em vez da condição LIKE, para localizar os salários de todos os funcionários com o nome 'R%':

```sql
SELECT salário
FROM Funcionários
WHERE last_name = 'R%'
ORDER BY salário;
```

#### Ordenação e diferenciação de maiúsculas e minúsculas.

A condição LIKE é sensível à ordenação. O Oracle Database compara o subpadrão Pi com a substring Si no algoritmo de processamento acima usando a ordenação determinada a partir das ordenações derivadas de char1 e char2. Se essa ordenação não diferenciar maiúsculas de minúsculas, a correspondência de padrões também não diferenciará maiúsculas de minúsculas.

#### Correspondência de padrões em colunas indexadas.

Quando você usa LIKE para pesquisar uma coluna indexada para um padrão, a Oracle pode usar o índice para melhorar o desempenho de uma consulta se o caractere principal no padrão não for % ou _. Nesse caso, o Oracle pode verificar o índice por esse caractere principal. Se o primeiro caractere no padrão for % ou _, o índice não poderá melhorar o desempenho porque o Oracle não pode verificar o índice.

#### Condição LIKE: Exemplos Gerais.

Essa condição é verdadeira para todos os valores que começam com last_name Ma:

```sql
last_name LIKE 'Ma%'

---------------------------------------------------->

-- Todos esses valores tornam a condição verdadeira:
-- Mallin, Markle, Marlow, Marvins, Mavris, Matos
```

Case é significativo, portanto, os valores que começam com last_name MA, ma, mA, e tornam a condição falsa.

Considere esta condição:

```sql
last_name LIKE 'SMITH_'

------------------------------------------------->

-- Essa condição é verdadeira para estes valores:
--SMITHE, SMITHY, SMITHS
```

Essa condição é falsa porque o caractere de sublinhado especial (SMITH\_) deve corresponder exatamente a um caractere do valor.

#### Exemplo de cláusula ESCAPE

O exemplo a seguir pesquisa funcionários com o padrão em seu nome: A_B

```sql
SELECT last_name
FROM employees
WHERE last_name LIKE '%A\_B%' ESCAPE '\'
ORDER BY last_name;
```

A cláusula identifica a barra invertida (\) como o caractere de escape. No padrão, o caractere de escape precede o sublinhado (\_). Isso faz com que o Oracle interprete o sublinhado literalmente, em vez de como um caractere especial de correspondência de padrões.
